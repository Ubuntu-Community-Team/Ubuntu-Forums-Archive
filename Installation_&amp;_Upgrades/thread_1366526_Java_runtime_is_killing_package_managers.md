---
title: "Java runtime is killing package managers"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Matt_Rapp on 2009-12-28
I just did a clean upgrade to 9.10 and after installing a few packages in the new software center and setting up catalyst I rebooted and got an error message. I have tried doing sudo dpkg --configure -a as was recommended to no avail. There is some kind of dependency issue going on with java6 rte, but I can't figure out how to stop it, I don't want to install java all that much. I also have tried sudo apt-get remove sun-java6-plugin and apt-get -f install but that didn't work either.

check out the screenshot

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141501&d=1262024175[/IMG]

I would like to fix this error if it will be quick and semi-easy otherwise I'll just reinstall again tonight.

---

### Post by gradinaruvasile on 2009-12-28
Open a terminal and type:

sudo apt-get install -f

It should install the missing dependency - sun-java6-bin
If not, install it manually:

sudo apt-get install sun-java6-bin

---

### Post by Matt_Rapp on 2009-12-28
Tired the first first option, failed so did as suggested

```

matt@matt-desktop:~$ sudo apt-get install -f
[sudo] password for matt: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
matt@matt-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-15-1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin

```

Then I tried manually installing it but I got to a blue EULA-ish screen that wants my approval before continuing but hitting enter, typing Ok, ok, y and Y do not work. Here is a screen-shot, how should I get past this screen?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141504&d=1262026530[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141505&d=1262026530[/IMG]

---

### Post by Mze on 2009-12-28
use the TAB key

---

### Post by gradinaruvasile on 2009-12-28
Interesting situation...

Dd you tried to remove the -plugin package? And then install the -jre package and the -plugin?

---

### Post by oldos2er on 2009-12-28
> **Matt_Rapp said:**
> Then I tried manually installing it but I got to a blue EULA-ish screen that wants my approval before continuing but hitting enter, typing Ok, ok, y and Y do not work. Here is a screen-shot, how should I get past this screen?


As Mze said, use Tab to highlight "Ok" then press Enter.

---

### Post by chenxiaolong on 2009-12-28
or use the right arrow key and press Enter.

---

