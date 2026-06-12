---
title: "java.awt.HeadlessException"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by dakrizma on 2012-10-12
[FONT="Verdana"][COLOR="DarkSlateGray"]Hi peeps,

I have installed SQL Developer and when trying to run it i get this error:[/COLOR][/FONT]

java.awt.HeadlessException
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
	at java.awt.Window.<init>(Window.java:477)
	at java.awt.Frame.<init>(Frame.java:419)
	at javax.swing.JFrame.<init>(JFrame.java:218)
	at oracle.ide.IdeCore$StartupWindow.<init>(IdeCore.java:1960)
	at oracle.ide.IdeCore.startupImpl(IdeCore.java:1148)
	at oracle.ide.Ide.startup(Ide.java:703)
	at oracle.ideimpl.DefaultIdeStarter.startIde(DefaultIdeStarter.java:35)
	at oracle.ideimpl.Main.start(Main.java:184)
	at oracle.ideimpl.Main.main(Main.java:146)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at oracle.ide.boot.PCLMain.callMain(PCLMain.java:62)
	at oracle.ide.boot.PCLMain.main(PCLMain.java:54)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at oracle.classloader.util.MainClass.invoke(MainClass.java:128)
	at oracle.ide.boot.IdeLauncher.bootClassLoadersAndMain(IdeLauncher.java:189)
	at oracle.ide.boot.IdeLauncher.launchImpl(IdeLauncher.java:89)
	at oracle.ide.boot.IdeLauncher.launch(IdeLauncher.java:65)
	at oracle.ide.boot.IdeLauncher.main(IdeLauncher.java:54)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at oracle.ide.boot.Launcher.invokeMain(Launcher.java:713)
	at oracle.ide.boot.Launcher.launchImpl(Launcher.java:115)
	at oracle.ide.boot.Launcher.launch(Launcher.java:68)
	at oracle.ide.boot.Launcher.main(Launcher.java:57)

[FONT="Verdana"][COLOR="DarkSlateGray"]Can anyone guide me or at least explain what does that error means, so I could try to fix it myself.

Btw, I'm new to Linux/Ubuntu so please be gentle.

:)

Thank you![/COLOR][/FONT]

---

### Post by dakrizma on 2012-10-12
I've installed latest version of JDK and now it works. :)

---

