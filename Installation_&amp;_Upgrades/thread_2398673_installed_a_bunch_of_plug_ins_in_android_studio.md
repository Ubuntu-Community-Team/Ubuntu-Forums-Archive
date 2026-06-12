---
title: "installed a bunch of plug ins in android studio"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by idkwhatimdoing1.0 on 2018-08-15
Hi, I've installed all the plugins I could find in android Studio thinking it would be a good idea... It was not a good idea as now I can't even open android studio as I get a bunch of error messages. Does anyone know what to do that would be best? Internal error. Please report to [https://code.google.com/p/android/issues](https://code.google.com/p/android/issues)

 ```
com.intellij.ide.plugins.PluginManager$StartupAbortedException: Fatal error initializing 'com.intellij.openapi.actionSystem.ActionManager'
    at com.intellij.ide.plugins.PluginManager.handleComponentError(PluginManager.java:276)
    at com.intellij.openapi.components.impl.PlatformComponentManagerImpl.handleInitComponentError(PlatformComponentManagerImpl.java:43)
    at com.intellij.openapi.components.impl.ComponentManagerImpl$ComponentConfigComponentAdapter.getComponentInstance(ComponentManagerImpl.java:515)
    at com.intellij.util.pico.DefaultPicoContainer.getLocalInstance(DefaultPicoContainer.java:239)
    at com.intellij.util.pico.DefaultPicoContainer.getComponentInstance(DefaultPicoContainer.java:206)
    at org.picocontainer.defaults.BasicComponentParameter.resolveInstance(BasicComponentParameter.java:77)
    at org.picocontainer.defaults.ComponentParameter.resolveInstance(ComponentParameter.java:114)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.getConstructorArguments(CachingConstructorInjectionComponentAdapter.java:129)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.doGetComponentInstance(CachingConstructorInjectionComponentAdapter.java:100)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.instantiateGuarded(CachingConstructorInjectionComponentAdapter.java:80)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.getComponentInstance(CachingConstructorInjectionComponentAdapter.java:63)
    at com.intellij.openapi.components.impl.ComponentManagerImpl$ComponentConfigComponentAdapter.getComponentInstance(ComponentManagerImpl.java:474)
    at com.intellij.openapi.components.impl.ComponentManagerImpl.getComponent(ComponentManagerImpl.java:181)
    at com.intellij.openapi.wm.WindowManager.getInstance(WindowManager.java:61)
    at com.intellij.openapi.ui.impl.DialogWrapperPeerImpl.<init>(DialogWrapperPeerImpl.java:93)
    at com.intellij.openapi.ui.impl.DialogWrapperPeerFactoryImpl.createPeer(DialogWrapperPeerFactoryImpl.java:37)
    at com.intellij.openapi.ui.DialogWrapper.createPeer(DialogWrapper.java:849)
    at com.intellij.openapi.ui.DialogWrapper.<init>(DialogWrapper.java:231)
    at com.intellij.openapi.ui.DialogWrapper.<init>(DialogWrapper.java:227)
    at com.intellij.openapi.ui.DialogWrapper.<init>(DialogWrapper.java:223)
    at com.intellij.openapi.ui.DialogWrapper.<init>(DialogWrapper.java:272)
    at com.intellij.diagnostic.errordialog.PluginConflictDialog.<init>(PluginConflictDialog.java:60)
    at com.intellij.diagnostic.PluginConflictReporter.reportConflictByClasses(PluginConflictReporter.java:56)
    at com.intellij.ide.plugins.PluginManager.processException(PluginManager.java:151)
    at com.intellij.ide.IdeEventQueue.processException(IdeEventQueue.java:423)
    at com.intellij.ide.IdeEventQueue.dispatchEvent(IdeEventQueue.java:349)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:201)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:116)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:105)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:101)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:93)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:82)
Caused by: java.lang.VerifyError: class git4idea.GitVcs overrides final method getName.()Ljava/lang/String;
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:763)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:642)
    at com.intellij.util.lang.UrlClassLoader._defineClass(UrlClassLoader.java:281)
    at com.intellij.util.lang.UrlClassLoader.defineClass(UrlClassLoader.java:277)
    at com.intellij.util.lang.UrlClassLoader._findClass(UrlClassLoader.java:246)
    at com.intellij.ide.plugins.cl.PluginClassLoader.loadClassInsideSelf(PluginClassLoader.java:142)
    at com.intellij.ide.plugins.cl.PluginClassLoader.tryLoadingClass(PluginClassLoader.java:74)
    at com.intellij.ide.plugins.cl.PluginClassLoader.loadClass(PluginClassLoader.java:61)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:348)
    at com.intellij.openapi.actionSystem.impl.ActionManagerImpl.processGroupElement(ActionManagerImpl.java:668)
    at com.intellij.openapi.actionSystem.impl.ActionManagerImpl.processActionsChildElement(ActionManagerImpl.java:967)
    at com.intellij.openapi.actionSystem.impl.ActionManagerImpl.registerPluginActions(ActionManagerImpl.java:467)
    at com.intellij.openapi.actionSystem.impl.ActionManagerImpl.<init>(ActionManagerImpl.java:146)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
    at org.picocontainer.defaults.InstantiatingComponentAdapter.newInstance(InstantiatingComponentAdapter.java:193)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.doGetComponentInstance(CachingConstructorInjectionComponentAdapter.java:103)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.instantiateGuarded(CachingConstructorInjectionComponentAdapter.java:80)
    at com.intellij.util.pico.CachingConstructorInjectionComponentAdapter.getComponentInstance(CachingConstructorInjectionComponentAdapter.java:63)
    at com.intellij.openapi.components.impl.ComponentManagerImpl$ComponentConfigComponentAdapter.getComponentInstance(ComponentManagerImpl.java:474)
    ... 29 more


```

---

### Post by wildmanne39 on 2018-08-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by idkwhatimdoing1.0 on 2018-08-15
well I can't even open andriod studio... It loads and at the 3/4 mark it stops and shows this errors

---

