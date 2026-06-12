---
title: "XP S3 and ubuntu 9.10 ext 4"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2010-01-26
Hey guys,

I have just tried to install xp sp3 after one-time booting from my cd drive. When I try to install xp , I get a message back saying that it cannot detect any harddrives. 

I am running ubuntu 9.10 with ext 4 at the present moment.Only reason why I want to install xp is to use office 2007.

How can I install xp? Do I have to format Ubuntu to ext3 and reinstall XP and ubuntu...?

---

### Post by limey_rick on 2010-04-26
This is probably because windows does not recognize the ext4 formatted partition. 

What you will have to do is run GParted to resize the ext4 partition. You can start GParted System->Administration menu. 

Select the disk you want to resize, then leave enough room for your windows XP system.

If you only have one disk, Windows install will overwrite the MBR record and you won't be able to boot into Ubuntu. Once you've installed XP, use the Live CD for Ubuntu and then re-install GRUB. Read the topic below for help. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) 


Post back for more help if you have problems.

---

### Post by v1ad on 2010-04-26
OpenOffice.org

Give it a chance. don't think office is worth the xp.

---

### Post by TBerk on 2010-04-26
1) I agree with both these fellas, (gender non-specific).

2) It will be hard to resize a partition you are booted from, is in play so to speak. Boot from the LiveCD and use GParted to shrink the Hard Drive's ext4 partition from there.

You can then create another partition; format *that* one with ntfs (or just bail and let the XP install 'discover' the empty space).

3) Reiterating the option, a good one, to install OpenOffice instead of MS anything.


berk

---

