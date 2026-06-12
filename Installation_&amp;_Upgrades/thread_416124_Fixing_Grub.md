---
title: "Fixing Grub"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by blackhole82 on 2007-04-20
Well I finally decided to try installing Feisty, and now I can't boot.  Right after I installed it grub did not even come up at boot and I was booted into Vista instead.  Now that I've played around with reinstalling grub the grub menu loads, but I get error 17: cannot mount partition for Ubuntu and error:13 invalid executeable .. something for trying to boot into Vista.  I have two hard drives with Vista and Ubuntu on the second drive.  I believe it is hd1.  My question is how do I fix grub?  I already seemed to have messed it up bad by trying to reinstall it in the first place.  I was unable to reinstall the Vista boot loader as well.

---

### Post by blackhole82 on 2007-04-20
I had to boot with noapic also if that has anything to do with my problems.

---

### Post by K.Mandla on 2007-04-20
This might be helpful for you.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

There used to be a Grub repair option on the alternate CD, but to be honest I haven't tried it with Feisty yet. Try booting your computer to the Feisty alternate, picking the rescue option and following the prompts. It'll probably look a lot like an installation sequence, but you should have certain options to recover the system later.

---

### Post by blackhole82 on 2007-04-20
I followed the grub howto (your 2nd link) the first time trying to fix my grub.  I just tried following the first link.  I still get error 13: invalid or unsupported executable format for Vista and error 17: cannot mount selected partition for Ubuntu.

---

### Post by Patrick K on 2007-04-20
Maybe this will help:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by blackhole82 on 2007-04-20
Well I just looked at my menu.lst for grub and everything appears to be right... So I don't understand.  Ubuntu is on the second hard drive second partition root (hd1,1), and windows is on the second hard drive first partition root (hd1,0).

---

### Post by blackhole82 on 2007-04-20
Well I think I found my problem.. I still had grub installed on the first hard drive and somehow that is conflicting with the grub on the second drive.  When I boot from my old harddrive it points to the same partition as the grub on the second harddrive, but will actually load.  Is there a way for me to delete it from one drive hd0?  I think that might solve my problem, but I'm not sure.

---

### Post by blackhole82 on 2007-04-20
I might be better off just running grub from the old harddrive.  I don't want to mess anything else up... lol.  It would be a pain in the *** to have to reinstall two OS again.

---

