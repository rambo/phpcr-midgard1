Midgard1 PHP Content Repository provider
========================================

For now efforts are centered in making [Jackalope](http://jackalope.github.com/) transport since that should be less work.

Text copied from https://github.com/bergie/phpcr-midgard2/blob/master/README.md


This project attempts to implement a [Midgard](http://www.midgard-project.org/midgard/8.09/) -backed implementation of the PHP Content Repository (PHPCR) interfaces. First goal is to have read-only support for migrating content to Midgard2

## About PHPCR

The PHP Content Repository API is a PHP version of the Java Content Repository specification. [From Wikipedia](http://en.wikipedia.org/wiki/Content_repository_API_for_Java):

> Content Repository API for Java (JCR) is a specification for a Java platform application programming interface (API) to access content repositories in a uniform manner. The content repositories are used in content management systems to keep the content data and also the metadata used in content management systems (CMS) such as versioning metadata.

This way a content management system, for example, would not be tied to a particular database or other storage scheme. Instead, the content repository providers could be chosen based on deployment requirements.

There is currently [discussion about including](http://java.net/jira/browse/JSR_333-28) PHPCR APIs into the Java Content Repository specification.

## About Midgard

Midgard is an open source content repository library available for multiple programming languages. For PHP it is available as an extension. On many distributions setting this up is as simple as:

    $ sudo apt-get install php5-midgard


### Making the Midgard tree single-rooted

While both Midgard2 and JCR build on the tree concept, the tree in Midgard is multi-rooted. We work around this by making each rootlevel object its own repository.

When user connects to a Midgard2 PHPCR repository, the connection will use configuration to map itself to a particular rootlevel object. A new PHPCR Session will be returned.



---------------
stuff below hasn't even been looked at
---------------


### Namespace mappings

The PHPCR API uses namespaces for node types and property names. The regular [Midgard2 MgdSchema RDF mappings](https://github.com/midgardproject/proposals/blob/master/Semantic%20Data/MgdSchemaRDF.md) should be used for this.

Midgard's MgdSchema types (PHPCR Node types) have a fixed set of properties. To implement the full PHPCR model, additional properties should be implemented using Midgard Parameters.

Basically setting value of Node property `foo:bar`, can mean depending on MgdSchema, either:

    $node->bar = $value;

or:

    $node->set_parameter('foo', 'bar', $value);

## Projects using PHPCR

* [Symfony CMF](http://pooteeweet.org/blog/0/1912#m1912)
* Flow3/TYPO3

## Licensing

Content Repositories are important piece of software infrastructure that must be usable by any projects or companies regardless of their business model. Because of this, the Midgard2 PHPCR implementation will be available under permissive terms of the [GNU Lesser General Public License](http://www.gnu.org/licenses/lgpl-2.1.html).

## Development

The Midgard PHPCR provider is in early stages of development. 

Contributions to the Midgard PHPCR provider are very much appreciated. The development is coordinated on a GitHub repository:

* [github.com/rambo/phpcr-midgard1](https://github.com/rambo/phpcr-midgard1)

Feel free to watch the repository, make a fork and [submit pull requests](http://help.github.com/pull-requests/). Code reviews, testing and [bug reports](https://github.com/rambo/phpcr-midgard1/issues) are also very welcome.
