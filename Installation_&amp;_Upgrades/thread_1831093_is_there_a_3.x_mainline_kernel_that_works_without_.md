---
title: "is there a 3.x mainline kernel that works without breaking services in Natty?"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by joelbue on 2011-08-22
is there a 3.x mainline kernel that works without breaking services in Natty?

a url would be handy.  thank you

---

### Post by garvinrick4 on 2011-08-22
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Use 3 of them, all.deb, headers, image of your 32 or 64 bit architecture.

Below you have to upgrade this package before you install 3.0 and up kernel in Natty.
Here is 32 or 64 bit in .deb build. of module-init-tools
[https://launchpad.net/ubuntu/+source...+build/2555500]("https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555500")
[https://launchpad.net/ubuntu/+source...+build/2555502]("https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1/+build/2555502")

---

### Post by joelbue on 2011-08-29
hello sir

is there a more recent module-init-tools i can fetch somewhere ?  

also, on my 3.0.3 kernel i have lost all fsck ability on natty.  i've like to restore as much as possible that has been left out that was there before the new ubuntu development version.

thanks for your assistance.

---

### Post by joelbue on 2011-08-29
i found the latest module-init-tools.  thank you sir.  i had one additional question if you don't mind.  anyway to reenable apparmor ?  is apparmor really not necessary ?

---

### Post by garvinrick4 on 2011-08-29
Are you using "fsck"  on a unmounted partition example. Either using another partition or a Live CD
```
sudo e2fsck /dev/sda12
```rick@rick-HP:~$ sudo e2fsck /dev/sda12
[sudo] password for rick: 
e2fsck 1.41.14 (22-Dec-2010)
oneiric: clean, 211267/658368 files, 1438017/2628627 blocks

---

### Post by joelbue on 2011-08-29
i'm trying to auto fsck on a 3.0.3 kernel like normal using natty.  in the event you can help me my msn IM is eat <dot> brains <at> hotmail.com.

i also want to restore anything that disappeared from ureadahead.  i promise i won't bother you.  i could use a hand now and then for the more complicated tasks.  

thank you

---

