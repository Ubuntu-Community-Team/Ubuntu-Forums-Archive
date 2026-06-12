---
title: "Trying to install program that needs different java version"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by mr tim esquire on 2007-04-10
Im trying to install a java program but it dosnt seem to like my current version of java:  
```
tim@desk:/tmp$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

If you look below the program rejects my java as not being SUN or Blackdown.   But ol google tells me that hotspot IS sun java.
Id really like to have the sun version running, does it work well on unbutu (dapper)  and if so could you please dive me some direction in regards to this.

Otherwise is there a simple way to swaqp between java versions

thanks in advance
tim

```
tim@desk:/tmp$ freemind
ERROR:   Your Java virtual machine is neither Sun nor Blackdown,
         =======================================
         FREEMIND WILL MOST PROBABLY *NOT* WORK,
         =======================================
         define JAVACMD, JAVA_BINDIR, JAVA_HOME or PATH in order
         to point to such a VM. See the manpage of freemind(1) for details.

Looking for user properties:
/home/tim/.freemind/user.properties

User properties not found. It will be automatically created.
Done.
Default (System) Look & Feel: com.sun.java.swing.plaf.gtk.GTKLookAndFeel
javax.xml.bind.JAXBException
 - with linked exception:
[java.lang.NoClassDefFoundError: org/relaxng/datatype/ValidationContext]
        at com.sun.xml.bind.ContextFactory_1_0_1.createContext(ContextFactory_1_0_1.java:56)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at javax.xml.bind.ContextFinder.newInstance(ContextFinder.java:142)
        at javax.xml.bind.ContextFinder.find(ContextFinder.java:259)
        at javax.xml.bind.JAXBContext.newInstance(JAXBContext.java:372)
        at javax.xml.bind.JAXBContext.newInstance(JAXBContext.java:337)
        at javax.xml.bind.JAXBContext.newInstance(JAXBContext.java:244)
        at freemind.common.JaxbTools.getJAXBContext(JaxbTools.java:59)
        at freemind.common.JaxbTools.<init>(JaxbTools.java:43)
        at freemind.common.JaxbTools.getInstance(JaxbTools.java:48)
        at freemind.controller.Controller.<init>(Controller.java:180)
        at freemind.main.FreeMind.<init>(FreeMind.java:227)
        at freemind.main.FreeMind.main(FreeMind.java:647)
Caused by: java.lang.NoClassDefFoundError: org/relaxng/datatype/ValidationContext
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at freemind.controller.actions.generated.instance.impl.runtime.GrammarInfoFacade.class$(GrammarInfoFacade.java:156)
        at freemind.controller.actions.generated.instance.impl.runtime.GrammarInfoFacade.createGrammarInfoFacade(GrammarInfoFacade.java:155)
        at freemind.controller.actions.generated.instance.impl.runtime.DefaultJAXBContextImpl.<init>(DefaultJAXBContextImpl.java:61)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
        at com.sun.xml.bind.ContextFactory_1_0_1.createContext(ContextFactory_1_0_1.java:50)
        ... 15 more
Exception in thread "main" java.lang.RuntimeException: getJAXBContext failed.
        at freemind.common.JaxbTools.getJAXBContext(JaxbTools.java:62)
        at freemind.common.JaxbTools.<init>(JaxbTools.java:43)
        at freemind.common.JaxbTools.getInstance(JaxbTools.java:48)
        at freemind.controller.Controller.<init>(Controller.java:180)
        at freemind.main.FreeMind.<init>(FreeMind.java:227)
        at freemind.main.FreeMind.main(FreeMind.java:647)

```

---

### Post by Goliath! on 2007-07-12
I have the same problem with Freemind.  Mr. TIm Esquire, did you find a solution?

---

### Post by Wnutt on 2007-09-19
> **Goliath! said:**
> I have the same problem with Freemind.  Mr. TIm Esquire, did you find a solution?

Hi !

I had the same probleme with Freemind.0.9.0.

In the end downloading and installing this version of the installer did the trick:
freemind-bin-max-0.9.0_Beta_13_icon_butterfly.zip

The first time didn't realise that I had downloaded the source package...

If that can be of any help.

++Nut - Nut++

---

