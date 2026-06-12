---
title: "How do I dual boot with a sata (ubuntu) and IDE (winxp) drives?"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by dfcm on 2006-09-23
Hi all,

Iv been looking around the net for a few days to see if i can find the solution to this problem, yet with no avial. So i thought well might as well post.

here is what I got. I got ubuntu 6 on a sata drive, and win xp on a IDE drive. Both as self booting. I am changing the bios to load which drive i want to use. When Im in ubuntu it reads my drive as sda, and the windows as hda, or I can change some bios setting and it will read hdc. The problem is that when I add the winxp drive to grub, It will not boot into linux as default, nor will it boot into windows. I believe its trying to read the winxp drive first. Its like when I add the win xp drive to grub, that it comes the first drive, and linux is second, some how, so it just gives me errors. I can unhook the xp drive and it loads perfect into linux.

Any Ideas?
thanks for your time.
Daryl

---

### Post by Cariboo1938 on 2006-09-23
> **dfcm said:**
> Hi all,
Iv been looking around the net for a few days to see if i can find the solution to this problem, yet with no avial. So i thought well might as well post.
here is what I got. I got ubuntu 6 on a sata drive, and win xp on a IDE drive. Both as self booting. I am changing the bios to load which drive i want to use. When Im in ubuntu it reads my drive as sda, and the windows as hda, or I can change some bios setting and it will read hdc. The problem is that when I add the winxp drive to grub, It will not boot into linux as default, nor will it boot into windows. I believe its trying to read the winxp drive first. Its like when I add the win xp drive to grub, that it comes the first drive, and linux is second, some how, so it just gives me errors. I can unhook the xp drive and it loads perfect into linux.
Any Ideas?
thanks for your time.
DarylRead [(http://users.bigpond.net.au/hermanzone/)"]this]("[http://users.bigpond.net.au/hermanzone/), maybe you get some answers.

---

### Post by wjp.reg on 2006-09-23
> **Cariboo1938 said:**
> Read [(http://users.bigpond.net.au/hermanzone/)"]this]("[http://users.bigpond.net.au/hermanzone/), maybe you get some answers.

I think you meant to enter [this]("http://users.bigpond.net.au/hermanzone/"). [-o<

---

### Post by dfcm on 2006-09-23
ok, ill take a look, by the way here is my fdisk -l output.

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30213   242685891   83  Linux
/dev/sda2           30214       30401     1510110    5  Extended
/dev/sda5           30214       30401     1510078+  82  Linux swap / Solaris


thanks agian.
Daryl

---

### Post by dfcm on 2006-09-23
ok, maybe im just to new to this stuff, but the above link is about installing ubuntu, iv already got ubuntu installed. just need to figure out how to get grub reading my winxp disk with out any trouble.

thanks again
daryl

---

### Post by wjp.reg on 2006-09-23
> **dfcm said:**
> ok, maybe im just to new to this stuff, but the above link is about installing ubuntu, iv already got ubuntu installed. just need to figure out how to get grub reading my winxp disk with out any trouble.

thanks again
daryl

If you read throughcaribou1938's revised link, you'll come across this reference which addresses SATA/IDE dual booting..

[http://www.ubuntuforums.org/showthread.php?t=179902]("http://www.ubuntuforums.org/showthread.php?t=179902")

Hope this helps..

---

### Post by dfcm on 2006-09-24
Thanks for the link.

I was able to get it working just fine. Im going to post what I put in my grub menu.lst so others might need the info as well.

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

thanks again for your help
Daryl,

Also just a note, I noticed that i couldnt enter grub with a wireless keyboard, on boot. I went to bios and enabled the legacy usb support to mouse and keyboard only, now it works like a charm.

---

