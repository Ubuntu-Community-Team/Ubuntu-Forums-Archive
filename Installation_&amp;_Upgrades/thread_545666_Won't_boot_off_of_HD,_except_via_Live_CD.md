---
title: "Won't boot off of HD, except via Live CD"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by ruberad on 2007-09-07
Hi,

I am enjoying (as much as possible) my recent install of Ubuntu, but for some reason I cannot boot normally.  The boot process goes kind of fast for me to see exactly what is going on, but it appears to try the hard drive and CDROM, give up on both, and then recourse to a net-boot (which sits and spins).

HOWEVER, when I leave my live CD in the CDROM drive, the splash screen comes up fine, and when I go down to the final option (boot from first hard drive), it proceeds directly to grub, and boots up great.

The best theory I have heard is that my SATA drive is not understood until the Live CD splash screen comes up, because by that point the necessary extra driver file has been loaded.

I am using Gutsy Tribe 4, because stable Fiesty didn't recognize the LAN/sound on my new motherboard (Intel DG33BU).  

If there are any commands I can run to show more diagnostic information than the above, just let me know,

thx!

r

---

### Post by David Corrales on 2007-09-08
I'm having the exact same problem...

I installed grub into my hard drive (SATA), and if I use another boot cd to boot off the main MBR it boots without problems. However, if I remove the cd and expect the bios to pick up the MBR from the drive, it won't boot.

Any pointers :)?

---

### Post by forestpixie on 2007-09-08
ruberad - > I am using Gutsy Tribe 4 - if you're going to use gutsy before it's released - I'd get the most [recent]("https://wiki.ubuntu.com/GutsyReleaseSchedule") one and try that 


David Corrales - > I'm having the exact same problem...

are you using tribe 4 too? if not have you reinstalled grub?

---

### Post by ruberad on 2007-09-08
> ruberad -  - if you're going to use gutsy before it's released - I'd get the most [recent]("https://wiki.ubuntu.com/GutsyReleaseSchedule") one and try that 

Well, when I installed it was the most recent.  Can I get to Tribe 5 with an apt-get update or an apt-get upgrade or something, or do I need to burn the CD and install it?

---

### Post by Pumalite on 2007-09-08
Re -install; my preference.

---

### Post by David Corrales on 2007-09-08
I'm using tribe 5 and I already tried reinstalling grub to no avail. As an extra pointer, my machine does not have a floppy drive installed.

---

### Post by Pumalite on 2007-09-08
I meant a clean install. Sorry. I'm using Tribe 4 in one and Tribe 5 in another, No problems from day one. Updates have gone flawlessly.

---

### Post by ruberad on 2007-09-08
> **David Corrales said:**
> I'm using tribe 5 and I already tried reinstalling grub to no avail. As an extra pointer, my machine does not have a floppy drive installed.No floppy drive in mine either, if that makes a difference

---

### Post by Pumalite on 2007-09-08
If it's any help; both, Tribe 4 and Tribe 5 recognize SATA drives and boot fine in both systems. Check your hardware for compatibility in ubuntu.org

---

### Post by David Corrales on 2007-09-09
> **Pumalite said:**
> If it's any help; both, Tribe 4 and Tribe 5 recognize SATA drives and boot fine in both systems. Check your hardware for compatibility in ubuntu.org

I installed using tribe 5. Then tried reinstalling grub using the same CD but not luck yet. Maybe need a newer grub version?

---

### Post by Pumalite on 2007-09-09
Tell me what you did re-installing Grub and why did you have to do it. Refresh my mind.
BTW, I don't think you need a new version of Grub.

---

### Post by David Corrales on 2007-09-09
I booted the livecd, opened a root terminal and ran **grub**. Then issued **root (hd0,0)** and **setup (hd0)**.

---

### Post by Pumalite on 2007-09-09
Did you run 'find' first?. Maybe this will help: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by David Corrales on 2007-09-12
> **Pumalite said:**
> Did you run 'find' first?. Maybe this will help: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I tried that, even with a cd called "super grub disk" but it doesn't work. It tells me grub was installed correctly and so on, but the bios isn't seeing the MBR at startup.

---

### Post by bobgunnison on 2007-09-12
I am having the same pb roblem.  mine will only boot if i have the winxp or super grub boot disc in the computer while it starts.

---

### Post by David Corrales on 2007-10-18
Bump. Any news?

---

### Post by GhodMode on 2007-10-18
I'm having the same problem.  When I boot the computer, nothing happens.  After the POST, I see only a blinking cursor.  However, if I boot to the Kubuntu Install/Live CD, then choose to boot to the first hard disk (even though it's actually the third hard disk), everything works fine.

I'm using the newly released Kubuntu that I downloaded this morning.

I have three hard drives.  Two of them are IDE and the third is SATA.  The SATA drive is new and hasn't been used before.

I don't intend to run any other operating systems, but my first IDE drive has Kubuntu 7.04 on it.  That was detected and added to the menu.lst file.

All three hard drives are mounted and work well.

Thank you,

-- Ghodmode

---

### Post by Pumalite on 2007-10-18
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

---

### Post by GhodMode on 2007-10-18
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

As far as I can tell, that's a completely unrelated issue.  I'm not booting multiple operating systems.  I'm not getting errors (or anything else) from Grub.  My menu.lst file is accurate as is my device.map file.

When I choose the option to boot from the first hard disc in the menu from the LiveCD, I get the grub Bootloader from the SATA disc and choosing the newly installed 7.10 kernel boots the OS properly.

---

### Post by GhodMode on 2007-10-18
I've found that the solution for me was to re-install Grub:
```
sudo grub-install --root-directory=/boot hd2
```After that, I rebooted and got an error message that was something like "File not found" and I knew that the problem was the difference in the disk order as grub sees it.  I followed the instructions in the grub shell to edit the boot command and change the line from root(hd2,0) to root(hd0,0) and it booted properly.  After that, I edited /boot/grub/menu.lst to make the change permanent.

-- Ghodmode

---

### Post by drtvasudevan on 2007-10-19
> **GhodMode said:**
> I'm having the same problem.  When I boot the computer, nothing happens.  After the POST, I see only a blinking cursor.  However, if I boot to the Kubuntu Install/Live CD, then choose to boot to the first hard disk (even though it's actually the third hard disk), everything works fine.....



same problem with ubuntu 7.10
needs the install cd to boot
tv

---

### Post by z35 on 2007-11-02
Just another person with the same problem. I have tried re-installing grub as well... no avail. I played around with the BIOS settings... I installed Windows XP and all works well (on drive 1 of my RAID)... rebuilt, installed grub, nothing. lilo, nothing. The only thing I have been able to boot from the hard drive is windows xp... ?

---

### Post by z35 on 2007-11-05
I found a solution:

I made a partition on my hard drive bootable. In my case, It was sda1 which is my swap partition...

---

### Post by David Corrales on 2007-11-06
z35 thanks for the tip, it worked for me :) I made my boot partition bootable and voilá, it works!
This is one of those problems where, after given the solution, you see how obvious it was... thanks again :guitar:

---

