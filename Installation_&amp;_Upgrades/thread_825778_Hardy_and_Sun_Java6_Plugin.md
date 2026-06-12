---
title: "Hardy and Sun Java6 Plugin"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by T_W on 2008-06-11
Has anyone discovered the magic formula to get the Sun Java6 plugin to work in Hardy?

I have tried
[LIST]
[*]update-java-alternatives
[*]removing icedtea
[*]Modifying /usr/lib/jvm/.java-6-sun.info
[*]Manually softlinking the plugin into /lib/firefox /lib/firefox-3 /lib/firefox-addons /lib/xulrunner-addons
[/LIST]

Does hardy work with the Java6 plugin or not?

I can seem to get Firefox to recognize its existence.

Thanks for any help.

---

### Post by prostar on 2008-06-11
I've also tried all the above.  I am on AMD 64 though.  I had Gutsy running great, but I had to hit the shiny red upgrade button...  Now I've spent a week getting things back to "normal"  I still cannot get Java to go in firefox 3.  

One thing I haven't tried, that I vaguely remember doing before is the manual link has to go in /usr/lib/firefox/plugins then you have to delete your ~/.mozilla/firefox/(crazy number).default/plugin.dat to get it to reload.  Maybe you have to delete the whole folder...  I'd have to search to find that post.

---

### Post by NilsE on 2008-06-11
I don't remember how I got to this point other than removing anything that was related to java runtime and plugin such as icetea and gcj versions of java and installing sun-java.  

However, when I got to the point that the packages in the screenshot below  are the only things installed (plus their dependencies) it started working.

Important, when you search in Synaptic search by name only not description. Also, I did have to reboot once or twice before it started working.

This is a good site to test it on

[http://www.darkfish.com/checkers/index.html](http://www.darkfish.com/checkers/index.html)

---

### Post by T_W on 2008-06-11
Well an update, the manually linking the java plugin into /usr/lib/firefox/plugins works **IF** I run Firefox-2.

Firefox-3 seems to be incapable of running the Sun Java plugin.

How the heck did this get screwed up so badly?  It used to work perfectly in Gutsy.

---

### Post by T_W on 2008-06-11
Well a bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/226911](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/226911)

I guess Sun Java was never tested.

---

