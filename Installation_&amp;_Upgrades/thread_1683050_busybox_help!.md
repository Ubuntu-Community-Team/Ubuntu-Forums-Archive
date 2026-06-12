---
title: "busybox help!?"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by VuLMz on 2011-02-06
hello people of Ubuntu forums, i am new to Linux so be easy on me please.

i am trying to install Ubuntu onto my desktop [Acer Aspire AST180-EA350M] and im having trouble. the history of my desktop is that it came with XP, got a trojan, so i installed Vista Home Premium onto it, my mistake as i didn't know i couldn't use the key [super noob to computer at the time] so it expired after my 30 days and now i don't have a fully functional OS on my desktop.

i just downloaded Ubuntu 10.10 to a usb drive then tried to install it on my desktop, i got a BusyBox v.1.15.3 error
[i can write the whole error if anyone needs it]

then, i Googled it and tried to find a fix..
i couldn't really find anything that helped me.

so i downloaded Ubuntu 10.10 to a DRD+R disk and tried to install it on my desktop, same error

so i was wondering if there was a fix to this.. i need a working OS for my desktop and this seems like the best one, if i can get it to work. any help is appreciated

V

---

### Post by VuLMz on 2011-02-06
error:

BusyBox v1.15.3 (Ubuntu 1:1.15.3-lubuntu5) built-in shell (ash)
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: invalid arguement
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs



any help? thanks
V

---

### Post by Rubi1200 on 2011-02-07
Hi and welcome to the forums :-)

Let's start with basics:

what are the specifications for the computer, especially RAM and graphics card.

did you check the md5sum of the iso?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

did you burn at the lowest possible speed?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Finally, boot the LiveCD/USB and post the results of the boot info script. There is a link at the bottom of my post with instructions.

---

