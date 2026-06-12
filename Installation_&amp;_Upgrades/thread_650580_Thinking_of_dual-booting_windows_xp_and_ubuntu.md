---
title: "Thinking of dual-booting windows xp and ubuntu"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by Virgilio on 2007-12-26
On my computer i currently only have ubuntu installed but of the rest of my family misses Windows xp and im having issues with my new mp3 player i made a thread about that but nobody wants to help :( so i've decided to dual-boot it. But how can i do this? If i bought an external hard-drive could i install windows on that? Or if that does not work could i somehow resize ubuntu's partition then dual-boot xp or does xp absolutely have to be installed first in order to dual-boot:confused:

---

### Post by Pumalite on 2007-12-26
XP first and Ubuntu is the ideal and the best way not to have issues later. Nevertheless, you can resize XP with Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and right click on XP partition, choose 'resize' from the menu. The new partition has to be formatted ntfs. I have to warn you that XP likes to be in sda1.

---

### Post by Virgilio on 2007-12-26
So does this mean i have to uninstall ubuntu first then install xp then finally install ubuntu again?

---

### Post by Craigus on 2007-12-26
> So does this mean i have to uninstall ubuntu first then install xp then finally install ubuntu again?

No, but you will have to do some extra work to replace grub after installing XP, because the XP installer will overwrite the MBR. That's OK it's easily fixed (you will find how easily with a search on the forum).

Installing XP on an external HD is possible, but not easy.

---

### Post by Virgilio on 2007-12-26
> **Craigus said:**
> No, but you will have to do some extra work to replace grub after installing XP, because the XP installer will overwrite the MBR. That's OK it's easily fixed (you will find how easily with a search on the forum).

Installing XP on an external HD is possible, but not easy.

Ok thank you for the suggestion. Why is it hard to install xp on an external HD? What if i buy an internal one, is it also as hard to install xp on?

---

### Post by Craigus on 2007-12-26
XP is designed to be installed on the primary drive in the system (ie sda / hda in linux parlance). It can be installed on other drives, but this requires various work-arounds.

What I generally do if installing XP on a separate drive is to make that drive the primary drive, install XP and then change the drive physically to its permanent channel. Then in grub, you do something like:

> title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

to boot. The map command fools the XP loader into thinking that it is booting from the primary drive.

---

### Post by Pumalite on 2007-12-26
It is not a wuestion of drives, but of order of inatallion. XP will overwrite your MBR and Grub will disappear. You can reinstall grub then with this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Don't worry, fixing your menu.lst is easy. Come back after you have done the prior steps. Installing to USB has the problem that Grub many times gets installed half in the internal drive and half in the external drive. This can be remedied installing to USB with all internal drives disconnected.

---

### Post by Virgilio on 2007-12-26
So basically what i have to do is run the gparted live cd then make a partition for xp then install xp on the partition that i just made after that run the ubuntu live cd to replace grub...please correct me if i got it wrong. And by the way what's sda1(mentionned in post 2)

---

### Post by Pumalite on 2007-12-26
If you intend to reinstall XP, I suggest you do something different. Boot Gparted, delete everything in your hard drive, then make a new large partition of your whole hard drive formatted ntfs. Install XP. Boot Gparted again, and resize XP. In the new partition, this is a good scheme:
10 GB for '/'
1 GB for /swap
The rest for /home.
Then install Ubuntu, go Manual and use the partitions already made.

---

### Post by Virgilio on 2007-12-27
I found this great guide for doing just what i want but it was written for feisty and i just wanna check if there's anything that needs to be changed here's the link [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by revision on 2007-12-27
From the looks of it that would be everything. I personally run Vista and Ubuntu on my ThinkPad without issue, well other than Gutsy being more stable than Vista haha. If you have a lot of stuff setup the way you want in Gutsy already and really don't feel like reinstalling it etc then I see no reason not to follow that tutorial, my personal preference is a wipe of the drive and start over but that tutorial appeared to include everything that would be needed.

---

