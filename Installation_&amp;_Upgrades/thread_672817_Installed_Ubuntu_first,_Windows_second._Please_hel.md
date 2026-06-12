---
title: "Installed Ubuntu first, Windows second. Please help unfreeze hell?"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by FilmAficionado on 2008-01-20
NOTE: Most people install Windows first, then Ubuntu, and have problems. I'm the opposite... Ubuntu first, Windows second (now), and I can't get bootloader to recognize Windows though Windows does work (when I can force it to via Super Grub CD)...

Windows does not load at all from the Grub bootloader though (it works, but after reinstalling grub, it was not in the bootloader anymore...)

Bootloader displays just Ubuntu, Ubuntu memory test, etc.

So Windows XP is missing from it.

My My sudo fdisk -l:

```
Device Boot Start End Blocks Id System
/dev/hdc1 1 497 3992121 83 Linux
/dev/hdc2 935 1307 2996122+ 82 Linux swap / Solaris
/dev/hdc3 1308 3237 15502725 83 Linux
/dev/hdc4 * 3238 5005 14201460 7 HPFS/NTFS 
```

I searched some here in this forum and got that I should add something along the lines of the following to my menu.lst file:

```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1
```

But now I'm getting a MISSING NTDLR error whenever I go to the bootloader and hit WINDOWS. Ubuntu loads fine, still, however.

I know the above is wrong for my setup (in the menu.lst file), so can anyone point me in the right direction?
```

/dev/hdc1 = UBUNTU LINUX PRIMARY INSTALLED
/dev/hdc2 = UBUNTU SWAP
/dev/hdc3 = UBUNTU SOMETHING / (home folder?)
/dev/hdc4 = NTFS WINDOWS XP
```

What should I change/add to my menu.lst file?

Thanks!

---

### Post by banewman on 2008-01-20
The reason people install windows then ubuntu is that windows overwrites the master boot record and doesn't/won't recognise linux but ubuntu will.
Try this helpful page
  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
:)

---

### Post by FilmAficionado on 2008-01-20
Hey, thanks for that page. I should have mentioned that I tried some of the stuff there, and I retried it again a few more times.

**Using the Unofficial "Super Grub Disk"**
```

      Download [WWW] Super Grub Disk
      Burn into a cdrom (better) or a floppy
      Boot from it
      Select: your language
      Select: Linux
      Select: Fix Boot of Linux (GRUB)
      Select the Linux or Grub installation you want to restore.
      You see the message: SGD has done it!
      Reboot
      You're done.
```


Works so that I can boot UBUNTU again full-time but doesn't allow me to boot Windows. I don't want to JUST recover Ubuntu, I want to recover Ubuntu AND have a spot in the grub bootloader list that allows me to pick Windows (I don't even remember how to get into Windows anymore)...

So I want to add an option for WINDOWS XP into the grub bootloader menu.

Please help anyone? I'm fairly desperate as I have an important deadline coming up :-({|=

---

### Post by torgrot on 2008-01-20
hda4 should be an extended partition and I don't think you can boot windows from there.  On the off chance that it isn't try this in menu.lst
title Windows
root (hd1,0)
chainloader +1

torgrot

---

### Post by FilmAficionado on 2008-01-20
> **torgrot said:**
> hda4 should be an extended partition and I don't think you can boot windows from there.  On the off chance that it isn't try this in menu.lst
title Windows
root (hd1,0)
chainloader +1

torgrot

A few minutes ago I found the link in someone elses post and was trying their code:
title Windows XP
root (hd0,1)
makeactivechainloader +1 

I got ERROR 13.

I just tried your code now and the screen changes, I get STARTING UP...
And the cursor blinks and the comp stays idle.

Do you have any other recommendations? I mean there has to be a way to get WIndows to start because I've done it manually through the Super Grub Disk last night...

Thanks so much, but please keep it coming :) I think we are getting closer.

---

### Post by torgrot on 2008-01-20
Try changing the line 
root(hd1,0)
to
root(hd0,3)

torgrot

---

### Post by kelvin spratt on 2008-01-20
You need Gparted SUPER DISC RESCUE boot up using the disc, go into the windows boot section first find windows restore mbr. once you have done that use the Linux section and try to restore grub. if you can't restore grub use live cd.to restore grub their are lots of tutorials on this forum.

---

### Post by FilmAficionado on 2008-01-20
So I followed some advice posted on another forum (before you two replied once more) and used fixboot to try to rid that Error 13... Now Ubuntu won't even startup... It goes to the loading screen but the bar stays fixed like at 1%.

In LiveCD sudo gparted and I see the filesystem is UNKNOWN, or damaged/corrupt because of Microsofts fixboot from an XP CD...

ARGH. Please tell me I didn't completely screw myself over here.

I hate myself.

---

### Post by FilmAficionado on 2008-01-20
> **FilmAficionado said:**
> So I followed some advice posted on another forum (before you two replied once more) and used fixboot to try to rid that Error 13... Now Ubuntu won't even startup... It goes to the loading screen but the bar stays fixed like at 1%.

In LiveCD sudo gparted and I see the filesystem is UNKNOWN, or damaged/corrupt because of Microsofts fixboot from an XP CD...

ARGH. Please tell me I didn't completely screw myself over here.

I hate myself.

I'm trying to think clearly. When I installed Ubuntu, I made three partitions as recommended. One for scratch, one for linux, one for my personal files (home folder or whatever?).

So basically, that makes me safe right?

I try to mount the damaged partition where linux is installed and it mounts but I get like 4 files that are 0kb in size with funky names (e.g. "AÇ.AÇ")

But would I have ANYTHING useful on that partition, or are my goodies likely on my other partition (I fund my Desktop and my documents stuff on another usable partition... Does my question make sense? This corrupt partition would only be home to settings and unpersonal stuff, correct? The rest of my "personal" stuff would have been saved to that other partition where desktop is and etc.? I can't think of having anything important on this corrupt partition, but I'm trying to think back, and I never really understood the whole install Ubuntu with 3 partitions deal or how the partitions worked. Am I in the clear and just good to go back and reinstall Ubuntu over the corrupt partition?

Would that even make my bootloader woes go away?
If so, how would I go about installing Ubuntu (starting form the Live CD) such that my IMPORTANT files on my noncorrupt partition don't get erased?

Thanks.

---

### Post by torgrot on 2008-01-20
You can try re-installing Ubuntu, when it gets to partitioning just uncheck format for the partitions that have your stuff on it and that format is checked for the borked partition.

torgrot

---

### Post by FilmAficionado on 2008-01-20
> **torgrot said:**
> You can try re-installing Ubuntu, when it gets to partitioning just uncheck format for the partitions that have your stuff on it and that format is checked for the borked partition.

torgrot

I did just that. Thanks guys for everything. I'm glad things worked out, though I DID have to reinstall Ubuntu. But since I had a separate home partition, it was relatively painless.

FYI, Grub was installed all over and fresh and XP is listed as an option now after the reinstallation. The code now reads: 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc4
title		Microsoft Windows XP Professional
root		(hd0,3)
savedefault
makeactive
chainloader	+1
```

Thanks again.

---

### Post by torgrot on 2008-01-20
No problem, I am sorry we weren't able to get you going with out the re-installation though.

torgrot

---

### Post by bigtom71 on 2008-01-21
The only way that I know to fix the problem is to reinstall windows and then reinstall Ubuntu on the same hard drive. This way both operating systems co-exsist on the same drive.

---

