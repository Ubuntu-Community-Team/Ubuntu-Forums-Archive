---
title: "how to port  &amp; install successful compiled modules on other installations ?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by fran13 on 2010-04-22
I succesfully patched, compiled and installed the mac80211 module using a hard disk installed ubuntu 9.10. On doing that I followed some online resources that I don't totally comprehend (linux nebie); nevertheless it works fine. 

Now I want copy & install the patched modules on other Ubuntu installations (without doing this whole stuff of getting kernel source and compiling). I just want to install the mac80211 module from the one Ubuntu onto other Ubuntu installations.

e.g.
*) ubuntu 9.10 on a pendrive 
*) ubuntu 9.10 in a virtual machine

1)
How can I do this ? With what topics should I be familiar ? Can you give me any resources/links/keywords, what I should read, comprehend ?  What should I read?

2)
Is there a tutorial how to port compiled components from one installation to an other ? 

3) 
does it make sense to do future compiling in a virtual machine and move the compiled modules into a hard disk or pendrive based Ubuntu (of the same version) ?

THX in advance

---

### Post by kbielefe on 2010-04-26
This is what I love about Linux.  Talking to a guy who patched and compiled a kernel module, yet describes himself as a newbie.

Anyway, it's been a while since I've done something like you've described, but I can at least point you down the right road.

First be aware that kernel modules are very version and architecture specific.  Copy to the same version and you will be okay.

Modules are installed under /lib/modules/ and have a .ko extension.  Just find yours and copy it to the exact same place on the other system.

Have a look at the depmod command.  I believe if you copied a new module to your running kernel you should be able to just run "sudo depmod" to integrate it with the new system but I'm not 100% sure on that.

You might want to file a feature request to get the patch included in the stock ubuntu kernel.

---

