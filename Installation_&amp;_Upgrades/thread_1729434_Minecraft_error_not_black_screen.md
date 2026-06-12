---
title: "Minecraft error not black screen"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by GangusKhan on 2011-04-14
Ok so i have just searched and searched and i have minecraft on my cumputer and i run it and click run offline and it goes black and after about 5-10 seconds this error comes up in the minecraft window




--- BEGIN ERROR REPORT a1dce528 --------
Generated 15/04/11 12:49 PM

Minecraft: Minecraft Alpha v1.1.2
OS: Linux (i386) version 2.6.35-28-generic
Java: 1.6.0_21, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.1.0
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:829)
    at org.lwjgl.opengl.Display.create(Display.java:767)
    at org.lwjgl.opengl.Display.create(Display.java:748)
    at net.minecraft.client.Minecraft.a(SourceFile:196)
    at net.minecraft.client.Minecraft.run(SourceFile:554)
    at java.lang.Thread.run(Thread.java:619)
--- END ERROR REPORT 851ff943 ----------


if anyone knows how i can fix it please help

---

### Post by frank604 on 2011-04-15
Looks like a java error. I'm no expert but I would delete the .minecraft folder in home, its hidden and reinstall.

Next, delete java through apt-get and its dependencies. Reinstall Sun Java instead of Open Java.  If after all this fails, try to uninstall Sun and try Open.  If these two workarounds don't work, then the issue is related to something else and needs further investigation/information.

Hope that helps!

EDIT:  Try the reinstalling of minecraft first.  Also, looks like you may want to update your kernel and see if that helps? You are using 2.6.35-28, latest is 2.6.38-8 on 11.04 at least.

---

### Post by GangusKhan on 2011-04-17
yeh i tried reinstalling minecraft and switching java's but i still get the same error each time i open it, do you know anything else i could do?

---

### Post by frank604 on 2011-04-24
Seems to be a video card issue.  I noticed you had an older version of the game? Alpha?  Current version of the game is Beta 1.5.  Maybe upgrading the game will provide a natural fix to this issue?

I looked into this and the problem seems to be common with intel graphics card (integrated).  

[http://www.minecraftforum.net/viewtopic.php?f=17&t=38863](http://www.minecraftforum.net/viewtopic.php?f=17&t=38863)
[http://www.minecraftforum.net/viewtopic.php?f=17&t=38068](http://www.minecraftforum.net/viewtopic.php?f=17&t=38068)

Can you write down some more hardware info?  Specs? Driver versions? 
Also can you write down your bash script to start the game?  IE, "java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame" ?

---

