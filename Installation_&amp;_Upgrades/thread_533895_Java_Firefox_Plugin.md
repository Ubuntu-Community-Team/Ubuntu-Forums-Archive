---
title: "Java Firefox Plugin"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by stuque on 2007-08-24
I can't get the Java Firefox plugin to work ... I've run

    sudo apt-get install sun-java6-plugin

and also installed the Sun java6 runtime environment. I appear to have the right version of Java when I check at the command-line.

$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

I've also removed Java 5 (including the Java 5 plugin). I've re-started Firefox, ensured Java/JavaScript are allowed.

But any Java applet I view in Firefox is blank, with a request to install Java. I've looked at about:config, and it does not show anything about Java.

I am at loss for what to do next ... any help would be appreciated!

---

### Post by rainwalker on 2007-08-24
I'm assuming you're using the Firefox that came with Ubuntu?
For a whlie that same thing happened to me, but then I figured out that it WAS installing the plugin, but only for the included Firefox (I was using a custom install that I did).

If that's not it, all I can say it to check out this thread: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
If you've tried that, I don't know what else to do

---

### Post by stuque on 2007-08-25
Aha, thanks Rainwalker ... it turns out I was indeed using a different instance of Firefox ... using the Ubuntu appears to fix everything.

---

### Post by rainwalker on 2007-08-25
Ah! Well good, I'm glad that fixed it :)

---

