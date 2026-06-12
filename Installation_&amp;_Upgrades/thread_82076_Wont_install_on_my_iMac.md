---
title: "Wont install on my iMac"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by shade11 on 2005-10-25
I have an iMac. A pretty old one. Running a G3 processor running Mac OS 8.6. I wanted to install ubuntu. However It wont work when i get to the install the base system. To make things more specific. I have formatted the drive on the partitioner to have it as ext3 format. The whole hard drive is about 6Gb total. The hard drive's 2nd partition which is about 6Gb. (The first partition has around 14KB). When I install the base system it turns out with this error:

```
[!!] Install the Base System
Base System error
The debootstrap program exited with the following error (Return Value 1).
Check /var/log/messages or see Virtual console 2 for the details.
```

I recieve this message around the 40% zone.
I cant format the Harddrive into Fat16
When I attempt to format it into Fat32 it freezes up.

What am I supposed to do?

---

### Post by N8K99 on 2005-10-26
Try using [SIZE="2"]noapic nolapic[/SIZE] as the qualifier when you install, instead of just pressing enter on the installation splash page. This should let you get through base system without any hangups.

---

### Post by shade11 on 2005-10-26
So how do I do that?

---

### Post by N8K99 on 2005-10-27
when you reboot with the install cd, there will be a screen that has a brown rectangle with the Ubuntu logo in it. There will be a paragraph which gives directions for installation, you know the one where somewhere it says just "push enter." Well, instead of pushing enter at the prompt, press F5 and you should see a new screen which gives you many differnet options of what sort of installation requirements you want to add or leave out. <<Noapic nolapic>> is one of those choices. Type that and then press enter. Your installation will continue the same as before, but should not hang up any more.

---

### Post by shade11 on 2005-10-27
Ok thanks. Umm just one thing. I dont know if It makes any diffrence but. . . It doesnt show the Ubuntu logo when I boot form the CD.

---

### Post by N8K99 on 2005-10-27
i'm sorry I mean when you  are installing from the cd, not boot from. There should be a splash page which looks alot like this. [IMG]http://eckenrodehouse.net/sandbox/001boot.png[/IMG] it's at this poin that you type noapic nolapic. Or better yet, try the Function keys to see the additional installation notes that are availalbe.

---

### Post by shade11 on 2005-10-28
Mine doesnt have a splash screen. Just some text. Pressing F5 doesn't work.

---

### Post by missmoondog on 2005-10-31
exactly what I was looking for. i hope!! 

had this issue with 7 of the 10 disks i got from the free shipit site. 8th one finally caught and finished installing. had the issue occur at least 1 time on 3 other installs over the last few days. even burned a cd of my own and had same thing happen.

---

