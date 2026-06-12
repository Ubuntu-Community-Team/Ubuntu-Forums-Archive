---
title: "Java applet not loading properly"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by Skylinedos on 2010-09-14
When I try to load this applet

[http://www.minecraft.net/play.jsp](http://www.minecraft.net/play.jsp)

It won't load properly and doesn't do anything. I have java installed and everything.

Any help?

---

### Post by Skylinedos on 2010-09-14
I could really use some help on this :\

---

### Post by Unterseeboot_234 on 2010-09-14
I create Java a lot (mostly applications however). There are lots of recipes whereby you go into ect/opt blah, blah, blah. I don't like those kinds of mods.

For YOU to run an applet you created and placed in a folder. Install the Synaptic **sun-java-jre** . I recommend you go ahead and do that. And you might have already done that, because you say you 'have' Java. [Menu] System => Adminstration => Synaptic Package Manager. If you have 64-bit hardware, you get the 64-bit JRE.

To get **Firefox** to run the Java JRE as a **plug-in**, that is pertinent to your hardware. If you have AMD64, the ia32 libs will have to be installed and linked. Goto the Oracle site, look for the Firefox info
**[http://www.java.com/en/download/help/linux_install.xml]("http://www.java.com/en/download/help/linux_install.xml")**

Great game BTW. It works in my Firefox. I'm not a gamer but that one is sweet!

Finally, and this if FYI, if you are developing Java code... I like to install the JDK / NetBeans bundle into my Home folder as ~/JDK1.6xxx ~NetBeans. That install will link NetBeans. Projects done in NetBeans IDE will run because the install linked them. The final code will run in its own folder because of the Synaptic sun-java-jre.

There are ways to sym-link a single JRE deep within the file structure of Ubuntu, but I have found it is a full day of frustration doing it that way.

Hey, good luck. To those following this thread the game is 'Minecraft' a neat web-delivered 3D game, but it is Alpha-preview right now, it may require subscription later on.

---

### Post by endotherm on 2010-09-14
to install sun java in lucid, you must make sure the partner repositories are enabled. you can do this in System -> Administration -> Software Sources -> Third Party Repositories. just check the box, apply, and reload synaptic

---

