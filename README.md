# Generating JAXB annotated classes with Maven plugins

Examples of generating JAXB annotated classes with popular Maven plugins:

[cxf](https://cxf.apache.org/cxf-xjc-plugin.html) creates smallest jar and fastest compilation 

[codehouse jaxb2-maven-plugin](http://www.mojohaus.org/jaxb2-maven-plugin/Documentation/v2.2/)

[jvnet jaxb2-maven-plugin](https://github.com/highsource/maven-jaxb2-plugin)


## What is JAXB?
Java docs defines it as 
> The Java Architecture for XML Binding (JAXB) provides an API and tools that automate the mapping between XML documents and Java objects.

> JAXB gives Java developers an efficient and standard way of mapping between XML and Java code.

JAXB provides a convenient and efficient way (with set of annotations) to create XML representations of the class (**marshalling**) or create new class instance from XML document (**unmarshalling**).

It's part of JDK since 1.6 version. [See versions by JDK](https://javaee.github.io/jaxb-v2/doc/user-guide/ch03.html#deployment-which-jaxb-ri-is-included-in-which-jdk) 

## What is XJC?
XJC is JDK-supplied tool for generating annotated Java sources from XML Schema Definition (XSD) file(s)
```
xjc -d src/main/java -b bindings.xjb -p net.ddex.xml ddex382.xsd
```

## JAXB bindings
Enables binding (between Java class and XML element) customizations without changing XSD or XML document 

## How to change JAXB version
Put your jaxb-api-<your-version>.jar inside endorsed directory  ([Java Endorsed Standards Override Mechanism](https://docs.oracle.com/javase/6/docs/technotes/guides/standards))
```
<java-home>\lib\endorsed 
```
or add JVM argument
```
<plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-compiler-plugin</artifactId>
   <version>3.3</version>
   <configuration>
     <compilerArgs>
          <arg>-Djava.endorsed.dirs=/path/to/your/version/jaxb-jar</arg>
     </compilerArgs>
  </configuration>
</plugin>
```

## JAXB alternatives
* [XStream](http://xstream.codehaus.org/)  
* [XMLBeans](https://xmlbeans.apache.org/)
* [Digester](https://commons.apache.org/proper/commons-digester/)
* [JIBX](http://jibx.sourceforge.net/)

## Popular Maven plugins homepages:
* [cxf-xjc-plugin](http://cxf.apache.org/cxf-xjc-plugin.html) personal favorite
* [maven-jaxb2-plugin](https://github.com/highsource/maven-jaxb2-plugin) provides plenty of configuration options
* [jaxb2-maven-plugin](http://www.mojohaus.org/jaxb2-maven-plugin/Documentation/v2.2/index.html)

## References
* [jaxb homepage](https://github.com/javaee/jaxb-v2)
* [jaxb user guide](https://javaee.github.io/jaxb-v2/doc/user-guide)
* [release documentation](https://javaee.github.io/jaxb-v2/doc/user-guide/release-documentation.html)
* [customizing JAXB Bindings](https://docs.oracle.com/cd/E17802_01/webservices/webservices/docs/1.5/tutorial/doc/JAXBUsing4.html)
* [XML bindings@wikipedia](https://en.wikipedia.org/wiki/Java_Architecture_for_XML_Binding)
* http://www.baeldung.com/jaxb