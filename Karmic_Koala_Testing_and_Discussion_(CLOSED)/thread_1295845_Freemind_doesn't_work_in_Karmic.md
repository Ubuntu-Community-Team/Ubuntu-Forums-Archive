---
title: "Freemind doesn't work in Karmic"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanzj on 2009-10-20
Hi. I upgraded from Ubuntu 9.04 to 9.10 (Karmic Koala). A program called Freemind no longer works. Here is the printout from terminal:

~$ freemind
> Checking Java Version...
19-Oct-2009 9:18:46 PM freemind.main.Resources logException
SEVERE: An exception occured: 
org.jibx.runtime.JiBXException: Binding information for class freemind.controller.actions.generated.instance.XmlAction must be recompiled with current binding compiler (compiled with jibx_1_0_2, runtime is jibx_1_1_6a)
	at org.jibx.runtime.BindingDirectory.getFactoryFromName(Unknown Source)
	at org.jibx.runtime.BindingDirectory.getFactory(Unknown Source)
	at freemind.common.XmlBindingTools.getInstance(XmlBindingTools.java:64)
	at freemind.modes.StylePatternFactory.loadPatterns(StylePatternFactory.java:66)
	at freemind.modes.mindmapmode.MindMapController.loadPatterns(MindMapController.java:597)
	at freemind.modes.mindmapmode.MindMapController.loadPatternActions(MindMapController.java:520)
	at freemind.modes.mindmapmode.MindMapController.createStandardActions(MindMapController.java:466)
	at freemind.modes.mindmapmode.MindMapController.<init>(MindMapController.java:388)
	at freemind.modes.mindmapmode.MindMapMode.createModeController(MindMapMode.java:61)
	at freemind.modes.mindmapmode.MindMapMode.init(MindMapMode.java:56)
	at freemind.modes.ModesCreator.getMode(ModesCreator.java:93)
	at freemind.controller.Controller.createNewMode(Controller.java:574)
	at freemind.main.FreeMind.init(FreeMind.java:275)
	at freemind.main.FreeMind.main(FreeMind.java:716)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)

STDERR: Patterns not loaded:java.lang.NullPointerException
Then this "Repair Patterns" Window pops up. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132461&stc=1&d=1256012858[/IMG]
I click "Yes".

> 19-Oct-2009 9:18:59 PM freemind.main.Resources logException
SEVERE: An exception occured: 
java.lang.NullPointerException
	at freemind.common.XmlBindingTools.createUnmarshaller(XmlBindingTools.java:85)
	at freemind.common.XmlBindingTools.unMarshall(XmlBindingTools.java:168)
	at freemind.modes.StylePatternFactory.loadPatterns(StylePatternFactory.java:66)
	at freemind.modes.mindmapmode.MindMapController.loadPatterns(MindMapController.java:597)
	at freemind.modes.mindmapmode.MindMapController.loadPatternActions(MindMapController.java:541)
	at freemind.modes.mindmapmode.MindMapController.createStandardActions(MindMapController.java:466)
	at freemind.modes.mindmapmode.MindMapController.<init>(MindMapController.java:388)
	at freemind.modes.mindmapmode.MindMapMode.createModeController(MindMapMode.java:61)
	at freemind.modes.mindmapmode.MindMapMode.init(MindMapMode.java:56)
	at freemind.modes.ModesCreator.getMode(ModesCreator.java:93)
	at freemind.controller.Controller.createNewMode(Controller.java:574)
	at freemind.main.FreeMind.init(FreeMind.java:275)
	at freemind.main.FreeMind.main(FreeMind.java:716)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)
19-Oct-2009 9:19:03 PM freemind.modes.ModesCreator getMode
SEVERE: Mode freemind.modes.mindmapmode.MindMapMode could not be loaded.
19-Oct-2009 9:19:03 PM freemind.main.Resources logException
SEVERE: An exception occured: 
java.lang.NullPointerException
	at freemind.common.XmlBindingTools.createUnmarshaller(XmlBindingTools.java:85)
	at freemind.modes.mindmapmode.hooks.MindMapHookFactory.actualizePlugins(MindMapHookFactory.java:161)
	at freemind.modes.mindmapmode.hooks.MindMapHookFactory.searchFor(MindMapHookFactory.java:118)
	at freemind.modes.mindmapmode.hooks.MindMapHookFactory.getPossibleNodeHooks(MindMapHookFactory.java:104)
	at freemind.modes.mindmapmode.MindMapController.createNodeHookActions(MindMapController.java:715)
	at freemind.modes.mindmapmode.MindMapController.<init>(MindMapController.java:393)
	at freemind.modes.mindmapmode.MindMapMode.createModeController(MindMapMode.java:61)
	at freemind.modes.mindmapmode.MindMapMode.init(MindMapMode.java:56)
	at freemind.modes.ModesCreator.getMode(ModesCreator.java:93)
	at freemind.controller.Controller.createNewMode(Controller.java:574)
	at freemind.main.FreeMind.init(FreeMind.java:275)
	at freemind.main.FreeMind.main(FreeMind.java:716)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)


I then get a "Repair Patterns" message stating: An error occured repairing the pattern file.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132462&stc=1&d=1256012858[/IMG]

> <mode not available: MindMap>

STDERR: java.lang.reflect.InvocationTargetException
STDERR: 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
STDERR: 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
STDERR: 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
STDERR: 	at java.lang.reflect.Method.invoke(Method.java:616)
STDERR: 	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)
STDERR: Caused by: java.lang.NullPointerException
STDERR: 	at freemind.controller.Controller.getModeController(Controller.java:320)
STDERR: 	at freemind.main.FreeMind.createModeController(FreeMind.java:920)
STDERR: 	at freemind.main.FreeMind.main(FreeMind.java:720)
STDERR: 	... 5 more

I then see the following two windows:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132464&stc=1&d=1256012858[/IMG]
"freemind.main.FreeMind can't be started."


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132463&stc=1&d=1256012858[/IMG]
"Mode not available: MindMap"



How can I get FreeMind to work on Ubunut Karmic Koala 9.10?

---

### Post by hanzj on 2009-10-20
I removed freemind and then 
sudo apt-get autoremove 
to remove the java stuff.
I then reinstalled freemind. 
Now freemind works, but I don't have latest version of freemind.
8-(

---

### Post by hanzj on 2009-10-20
I removed freemind and then 
sudo apt-get autoremove 
to remove the java stuff.
I then reinstalled freemind. 
Now freemind works, but I don't have latest version of freemind.
8-(

I guess I'll be happy with this 0.7.1 version (year 2001).

---

### Post by Jingo on 2009-10-20
Look at [bug #182927]("https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/182927") for a newer version for karmic.

---

### Post by mperry on 2009-10-20
I just downloaded the RC4 build of freemind from freemind.sf.net and manually installed it under my home directory and it works fine. I have the java stuff from medibuntu or wherever. All you need to do is make the freemind.sh executable and run it. I create a launcher on my desktop and its fine.

---

