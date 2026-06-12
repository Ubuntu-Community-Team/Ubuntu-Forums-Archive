---
title: "not allowing dual-boot"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by Affrikka on 2010-03-18
I installed windows xp on my tobisha satellite l305, then installed ubuntu 9.10...
let me back up a little bit..

okay, so my friend's laptop had vista and was SOOO bogged down from viruses, so he wanted to try ubuntu. We installed ubuntu, leaving the other half of his hard drive unallocated.
Afterwards we installed xp, on the unallocated space, but it wouldn't let me dual boot... it would boot directly into xp, however, the ubuntu partition was still there because through the file system in xp we could find it.

So then run gparted on a live CD, delete the ubuntu parition, leaving it unallocated, then installed it over that unallocated space.


now, when i dual boot it shows on the grub page the option to boot to ubuntu, ubuntu (recovery) and these two memory test things that when i ran it just shows a BIOS looking screen...testing my memory. However, on the desktop i have mounted 79gb which has all the windows files in it...

so how do I tell ubuntu to stop hoarding everything and share the boot screen with windows xp?


thanks :)



Mathieu

---

### Post by Fersure on 2010-03-18
Have you tried the following?

```
sudo update-grub
```

---

### Post by raymondh on 2010-03-18
As fersure said, try to boot into the liveCD and access a terminal. Type the command

```
sudo update-grub
```

exit terminal, exit liveCD and reboot.  See what happens and/or post back any errors.

When you installed Ubuntu the first time, it installed GRUB (the bootloader) in the MBR of that HD.  When you installed windows, it installed the windows bootloader (overwriting GRUB).  That was why you had no option to dual boot.  Installing Ubuntu the second time, again, overwrote the MBR and installed GRUB2.  Now, GRUB2 is pretty decent in picking up other operating systems.  Sometimes, sometimes, we have to 'motivate' it hence the suggestion to update grub.

Some reading materials for you

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Best.

raymond

---

