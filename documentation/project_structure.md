---
layout: page
title: Project Folder Structure
site_nav_entry: false
---

Once you [clone](https://github.com/typelevel/scala/) the compiler project (*hint:* ensure you are in a branch with the compiler code, not a documentation branch) you will see several folders and files. 

## Repository structure

Your starting point should be the `README.md` file at the root, which describes the project a bit more. This file contains a description of the project structure, which we reproduce below:

```
scala/
+--build.sbt                 The main sbt build script
+--build.xml                 The deprecated Ant build script
+--pull-binary-libs.sh       Pulls artifacts from remote repository, used by build
+--lib/                      Pre-compiled libraries for the build
+--src/                      All sources
   +---/compiler             Scala Compiler
   +---/library              Scala Standard Library
   +---/library-aux          Set of files for bootstrapping and documentation
   +---/reflect              Scala Reflection
   +---/repl                 REPL source
   +---/scaladoc             Scaladoc source
   +---/scalap               Scalap source   
   +---/eclipse              Eclipse project files
   +---/ensime               Ensime project templates
   +---/intellij             IntelliJ project templates
   +---...                   other folders like 'manual', etc
+--spec/                     The Scala language specification
+--scripts/                  Scripts for the CI jobs (including building releases)
+--test/                     The Scala test suite
   +---/benchmarks           Benchmark tests using JMH
   +---/files                Partest tests
   +---/junit                JUnit tests
   +---...                   Other folders like 'flaky' for flaky tests, etc
   partest                   Script to launch Partest from command line
+--build/                    [Generated] Build output directory
```


Relevant folders when working with the Scala compiler:

* **src**: source of the compiler. Also contains several IDE specific folders (ensime, eclipse, intellij), as well as the source code for tools like `scaladoc` and `scalap`
* **test**: scala test suite. You may want to focus on the partest side (/files) as well as `junit` and `benchmarks`, for a start

Folders of certain interest:

* **spec**: the Scala specification, as a Jekyll project. You can see it published online at [http://www.scala-lang.org/files/archive/spec/](http://www.scala-lang.org/files/archive/spec/) (select the relevant version to see HTML docs)
* **tools**: set of utility bash scripts, for example `scaladoc-diff` to see changes on Scaladoc

The following folders and files can be ignored when you start working with the Scala compiler as they are not relevant at this stage:

* **doc**: contains licenses for the project
* **docs**: contains some TODO tasks and notes. Not updated for a long while, doubtful to be relevant anymore
* **lib**: contains sha1 signatures for some jar files used in the project, for example the `ant-dotnet` jar to provide Scala support on .Net
* **META-INF**: contains Manifest file for the project
* **project**: contains helpers for the Scala build configuration. The project is using a standard `build.sbt` file, located at the root of the project
* **scripts**: used for CI 
