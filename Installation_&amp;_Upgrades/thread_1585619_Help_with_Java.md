---
title: "Help with Java"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by stevenm0519 on 2010-09-30
I am a noob when it comes to linux so please bare with me.  I checked the software center and saw that it told me i had Java installed but i cant seem to find out how to enable it. I am just trying to play Yahoo! Texas Hold em or any big poker gaming website for fun but i am having no luck. Please someone help

---

### Post by GregBrannon on 2010-09-30
I assume you play that with a web browser.  Which browser are you using?  Answering that will help someone help you, but you can also Google something like "ubuntu java (browser name)" to find guides on how to make Java work on the browser you're using.

---

### Post by stevenm0519 on 2010-10-01
I only have Mozilla firefox and google chrome installed i will use either one that you guys think will work easier

---

### Post by lykeion on 2010-10-01
This question must have been answered hundreds of time in this forum already). So for future troubleshooting, please search the forums first!

But OK here we go again
1. By default the Java Web Plugin in Ubuntu is IcedTea Plugin
2. Many websites requiring Java will fail if not the Sun Java Plugin is installed
3. If you're using latest Ubuntu (v10.04 Lucid) you'll have to enable the repository where Sun Java Plugin is first to install it

This can be done with 3 commands in the terminal, see _[HERE]("http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html")_ how that's done.

If you're a visual guy who never used a terminal before, _[HERE]("http://www.youtube.com/watch?v=AsYdroTnjXk")_ is a video tutorial on how to do it the GUI way (plus for the funny german accent)

---

### Post by stevenm0519 on 2010-10-05
Lykeion,
Thank you so much yes your right i should have done more research i apologize, i do have one more problem but i will try searching for this one more.

---

### Post by Sef on 2010-10-05
> This question must have been answered hundreds of time in this forum already). So for future troubleshooting, please search the forums first!

But OK here we go again
1. By default the Java Web Plugin in Ubuntu is IcedTea Plugin
2. Many websites requiring Java will fail if not the Sun Java Plugin is installed
3. If you're using latest Ubuntu (v10.04 Lucid) you'll have to enable the repository where Sun Java Plugin is first to install it

This can be done with 3 commands in the terminal, see HERE how that's done.

If you're a visual guy who never used a terminal before, HERE is a video tutorial on how to do it the GUI way (plus for the funny german accent)

Easier is with the Ubuntu Software Center.
Just a few clicks and both can be installed.  Just type in restricted in the search bar for the restricted drivers.

---

### Post by lykeion on 2010-10-05
Yes installing the ubuntu-restricted-extras package might be easier, but you'll also get lots of extra packages besides java (lots of gstreamer plugins, flash plugin, microsoft fonts, etc). For some people this might be ok, but if you don't need this overhead my directions aren't that hard to follow.

---

