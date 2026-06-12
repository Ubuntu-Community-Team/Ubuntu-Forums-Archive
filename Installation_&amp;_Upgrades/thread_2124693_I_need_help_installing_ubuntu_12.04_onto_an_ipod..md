---
title: "I need help installing ubuntu 12.04 onto an ipod."
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by PrinceofLight on 2013-03-11
The ipod in question is a 5th gen Ipod Video that has a cracked screen. Considering it can't be used as an ipod, I thought I'd be able to make more use of it through removable storage. I have tried to install ubuntu using the windows installer after reformatting the ipod to blank fat32 and blank ntfs, to no avail. I am going to try installing it with the ipod's original OS on the drive when I get a chance.

The first strange thing that I noticed was that after rebooting from the windows installer and selecting ubuntu, ubuntu would fail to boot once or twice, with the bios giving me an error I haven't recorded, then I'd have to hit F12 again at startup and it would boot ubuntu's installation process without a hitch.

I was able to get to the point where the installer had started actually installing ubuntu onto the ipod after booting from it, only to have it hang while copying files and then totally crash. I didn't have a way to save the error messages that came up but I'll  update this thread with any further results of experimentation. I don't believe there's something wrong with the hard drive itself, as I've run windows's disk check utility on it multiple times without any errors being shown.

Something else I'd like to know. I plan on installing windows xp alongside ubuntu on this ipod, if possible. Is it necessary to partition the drive to do that, or can both operating systems run on the same partition?

To finish, I have some conjecture about why this problem could be occurring. Do I absolutely have to disconnect my internal hard drive for the bootloader to be installed correctly? Is the ubuntu installation wizard not detecting the bootloader in the ipod and crashing as a result, because it's in the hard drive which isn't running while I'm doing this? I ask because even after uninstalling the failed installation of ubuntu and disconnecting the ipod I noticed that ubuntu would still be listed as a bootable option in startup.

---

### Post by Maheriano on 2013-03-11
You have me confused with how you'd install Ubuntu on a mp3 player. Are you sure it is an iPod?

---

### Post by PrinceofLight on 2013-03-11
> **Maheriano said:**
> You have me confused with how you'd install  Ubuntu on a mp3 player. Are you sure it is an iPod?

That sounds like a bit of a silly question. Yes, I'm positive it's an ipod.

Note that I'm not trying to run ubuntu on the ipod itself, I want to hook it up to my computer and run ubuntu from it as if it were any other removable hard drive.

---

### Post by bfmetcalf on 2013-03-11
I think your issue arises in the the fact that the ipod is not a removable hard drive, but a small computer itself.  It needs an OS that it can use like the iOS that it had on it, or rockbox or something similar.  I have a pretty good feeling that you will not be able to do what you want no matter what you try.

---

### Post by PrinceofLight on 2013-03-12
> **bfmetcalf said:**
> I think your issue arises in the the fact that the ipod is not a removable hard drive, but a small computer itself.  It needs an OS that it can use like the iOS that it had on it, or rockbox or something similar.  I have a pretty good feeling that you will not be able to do what you want no matter what you try.

Well if I could get rid of that stinking ipod firmware I think I'll be in the clear.

---

### Post by TK999 on 2013-03-13
Hey, I found the following article about your problem:
[https://wiki.archlinux.org/index.php/IPod#Introduction](https://wiki.archlinux.org/index.php/IPod#Introduction)
While written for Arch Linux, I think it should work under Ubuntu flawlessly. Just use "sudo apt-get install" instead of "pacman -S" if you happen to encounter it.

---

### Post by PrinceofLight on 2013-03-13
> **TK999 said:**
> Hey, I found the following article about your problem:
[https://wiki.archlinux.org/index.php/IPod#Introduction](https://wiki.archlinux.org/index.php/IPod#Introduction)
While written for Arch Linux, I think it should work under Ubuntu flawlessly. Just use "sudo apt-get install" instead of "pacman -S" if you happen to encounter it.

Wow, this is all Greek to me. Can I assume that this works for the ipod I'm using? The one in question is an gen 5 ipod video, not an itouch or iphone.

---

### Post by TK999 on 2013-03-14
You could try just plugging in your device to see if it is mounted as an USB drive before that. After plugging in, run
```

lsblk

```
to find it; it will likely be under /media.

---

### Post by Redalien0304 on 2013-03-14
unbuntu on ipod thts probly worhtless. but would be knida cool to throw it in Apples face. sorry no Apple ipod fan here. I would Recycle it is my job to recycle worthles Computer Parts Responibly. I will take any Apple Product apart Gladly with Pleasure working or not working.

---

### Post by Maheriano on 2013-03-14
The program  you're looking for in Ubuntu is Startup USB Creator. If that doesn't pick up your iPod as an installable drive then it won't work.

---

