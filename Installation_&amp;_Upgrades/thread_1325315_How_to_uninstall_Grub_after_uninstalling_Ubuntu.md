---
title: "How to uninstall Grub after uninstalling Ubuntu"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Udavid on 2009-11-13
Hello world, I am a big fan of Ubuntu and I installed Ubuntu on my wife's laptop but she is not crazy about it and wanna uninstall it. but after doing that, the Ubuntu grub is still here while booting up laptop. XP/Ubuntu options. anyway to avoid this? thank you in advance.

---

### Post by darkod on 2009-11-13
You need your WinXP disc to boot up with it and go into Recovery Console. From there you can fix the MBR.

Google for "restore mbr in xp" or similar. Plenty of guides around even with screenshots.

---

### Post by Udavid on 2009-11-13
Thank you very much but the sad truth is, I don't have any restore CD any longer. any easier way to do the trick?

---

### Post by ColdFFF on 2009-11-13
I think the command was fixmbr. Alternatively there is also fixboot, but I cant remember what the exact difference between the two commands are

Edit:

There are numerous bootable rescue disks available for download that should do the trick. You could give [Bootzilla]("http://www.bootzilla.org") a try

---

### Post by darkod on 2009-11-13
But you need to boot with the cd to reach recovery console at all. Don't know any other way.

Another option is to just leave grub, no harm. It is only bootloader which windows also has, only better. :) Select windows option to be default and timeout to be 1sec, so after waiting only 1sec for a choice it will start booting the default (windows).

If you need help for this ask. But there are also plenty guides around. :)

---

### Post by geordie12 on 2009-11-13
Hi,

If you have an old win98 rescue disk(a lot of people have)boot from it and at the prompt type fdisk /mbr. The whole thing takes 4-5 minutes. HTH

geordie

---

### Post by Udavid on 2009-11-13
Thank you guys. I have just checked out Bootzilla very complicated for me. also I am not good at command prompt. Is there any easies way for a newbie? I know it is okay to leave it alone but my wife does not like it. :=)

---

### Post by kkady32 on 2009-11-13
easy way is fdisk /mrb (georgdie12 method)
to find another program i recomandet u Hiren's BootCD ([http://www.hirensbootcd.net/](http://www.hirensbootcd.net/))

---

### Post by darkod on 2009-11-13
If you can still enter XP from grub, and it sounds you can, try this if you like:
[http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html](http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html)

---

