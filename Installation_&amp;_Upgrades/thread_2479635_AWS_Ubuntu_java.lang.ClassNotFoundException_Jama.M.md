---
title: "AWS Ubuntu java.lang.ClassNotFoundException: Jama.Matrix"
date: 2022-10-01
forum: Installation &amp; Upgrades
---

### Post by techveera on 2022-10-01
I am trying to run a mutation clustering algorithm described in


[https://tinyheero.github.io/2015/08/26/TrAp.html](https://tinyheero.github.io/2015/08/26/TrAp.html)


Running ```
java -jar TrApWithDependencies.jar --text figure1.txt 
```works fine on my laptop running windows 10, but not on AWS ubuntu. I would like to run it on my AWS instance because the algorithm is very RAM hungry and will run out of memory for input data with 50 or more rows.


Running it on Ubuntu Server 18.04 LTS gives me the following error. I believe the key issue is with Jama.Matrix


```
Exception in thread "main" java.lang.reflect.InvocationTargetException
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.base/java.lang.reflect.Method.invoke(Method.java:566)
    at org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader.main(JarRsrcLoader.java:58)
Caused by: java.lang.NoClassDefFoundError: Jama/Matrix
    at klugerlab.trap.data.Solution.fitClones(Solution.java:703)
    at klugerlab.trap.algo.MinimalClonesSolver.processTemplate(MinimalClonesSolver.java:168)
    at klugerlab.trap.algo.MinimalClonesSolver.completeSolutions(MinimalClonesSolver.java:204)
    at klugerlab.trap.algo.MinimalClonesSolver.runSolver(MinimalClonesSolver.java:250)
    at klugerlab.trap.algo.Solver.run(Solver.java:229)
    at klugerlab.trap.algo.Job.run(Job.java:97)
    at klugerlab.trap.TrApMain.main(TrApMain.java:120)
    ... 5 more
Caused by: java.lang.ClassNotFoundException: Jama.Matrix
    at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:471)
    at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:588)
    at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:521)
    ... 12 more

```

I do not have access to the source code, only the .jar file.

---

### Post by QIII on 2022-10-01
Please use the default font and colors except when it is important to highlight some detail to make things more understandable.

Also, please enclose all terminal commands and their output in code tags to preserve formatting and make your posts easier to read. 

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.


Do you have Oracle Java installed or OpenJDK?  Was that package written for Oracle Java or OpenJDK.  OpenJDK should, in theory, work for Oracle Java since Oracle states that OpenJDK is the standard open source implementation of Java used as the reference.  But developers don't always know that an their products sometimes become apoplectic if they are unable to locate Oracle Java.

Do you have JAMA installed?  It would appear that the package can be found [here]("https://math.nist.gov/javanumerics/jama/#Package").  You may be able to examine the source code from the files at that URL  Or, you could be lucky and your thread may be discovered by someone familiar with the package.  Was JAMA written for Oracle Java, or will it work with OpenJDK?

From the URL:  
> JAMA was originally created as a proof-of-concept; a potential primary linear algebra package that could be adopted for Java. As such, it is no longer actively developed to keep track of evolving usage patterns in the Java language, nor to further improve the API. We will, however, fix outright errors in the code.

Since the last version is dated 2012, the disclaimer above does not bode well.  Much has changed in Linux.  When you install Java on Windows, you are generally installing Oracle Java.  The legacy may be unbroken.  Linux distros usually default with OpenJDK, so legacy code may break.

Unfortunately, when I was getting my Applied Mathematics degree in the '70s, we did everything in Fortran or BASIC -- or used the Stubby Pencil Operating System for Linear Algebra.

---

### Post by MAFoElffen on 2022-10-01
Even with Oracle Java, versioning matters. When I took Object Oriented Programming in College, I taught the Professor how to use Eclipse and updated his JAVA examples so he could lecture on them... When Java versions deprecate something, it is not always carried on as Legacy to still work and give warnings... It just fails.

In 2012, there was no OpenJava, that didn't occur until 2017 with OpenJDK6. Java6 was released by Sun (and transitioned to Oracle). Java 7 was released by Oracle.

So my recommends would be to ensure that if it works in Windows, use the same Java Version and branding of the SDK or runtime in Linux. If you really need it to run, I think in 2012, the current Java versions were 6 or 7... Vulnerabilities were found and updated many times in the past 10 years since then.

---

