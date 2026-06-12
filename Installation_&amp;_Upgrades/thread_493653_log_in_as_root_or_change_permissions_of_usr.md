---
title: "log in as root or change permissions of /usr"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by fishbite on 2007-07-06
How can I log in as root or change the permissions of mozilla-firefox to get java run time to work? Am I in the right forum for this ??:p

---

### Post by NeoLithium on 2007-07-06
No need to change the pemissions of /usr  How did you install java to work with firefox and what version are you using? 32 or 64 bit?

---

### Post by fishbite on 2007-07-06
32, downloaded the jre1.6.0_01.bin to my home folder expanded and need to make a link in the mozilla-firefox/plugins folder, but can't because it is root only permission.

---

### Post by NeoLithium on 2007-07-06
Ahhh. Ok.  the best way to install java, is to enable the additional repositories, and then just install it via the package manager:

Add the repositories:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

And then install Java:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Java](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Java)

Simple, and clean for you to do.  Those are Feisty guides, if you're running an earlier version than 7.04, just look at the top and there's links for edgy and dapper installs of Java :)

---

