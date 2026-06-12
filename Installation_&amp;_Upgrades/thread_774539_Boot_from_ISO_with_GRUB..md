---
title: "Boot from ISO with GRUB."
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by jesusfreak107 on 2008-04-29
How do I use GRUB to boot directly off of an iso? I have a ubuntu 7.10 ISO (Gutsy, I do not want to upgrade to Hardy yet), but my old lappy that I found in the garage recently has no CD drive, and I cannot get it to boot off of our external DVD drive, it apparently cannot boot off of any USB device.  I know it is possible to do this, I have just not found a good tutorial.  I used grub to boot an installer, but it needed to download the file, once I booted off of it, and it could not detect my internet connection, and I tried both wireless G, and ethernet.  I am running Windows 98SE on a Toshiba Sattelite 1730, with 192MB RAM, 700MHz Proccesor, and a 10GB HDD, although I have 3.75GB worth of SD cards that I can use if I need to.  I have GRUB, already, and I know how to modify it.  I found this lappy in our garage, and once I bought a new power cord, it works fine, except for a few flaws, one being the CD drive does not work.  oh, and I do have a floppy drive, and a spare floppy, if I need one, but I have ne experience using one, and if I need to do something with it, you will need to dumb it down as much as possible.  Any help will be appreciated, I don't really care how, I just need to boot the ISO without using any external devices.  Oh, and if you know how to fix the internet problem in the ubuntu install thing, that would work, too.   Ideal situation:  Someone provide me with a couple files to download, where to put them, and a string of code to enter into the menu.lst file.  


Oh, and partitioning part of my HDD to act as a make-shift CD drive is not an option.  I cannot partition my drive without booting off of an ISO in the first place, as Windows 98 does not have the capability to partition the HDD it is currently using.

Thanks in advance!
:guitar::guitar::guitar:

---

### Post by scragar on 2008-04-29
you can remap an ISO file to be treated as a partition as far as the system is concerned:

```
grub> map (hd1,1)PATHtoISO.iso (hd4)
grub> map --rehook
grub> chainloader (hd4)+1
grub> rootnoverify (hd4)
grub> boot
```

But be warned that this doesn't always work based on grub versions(the feature of --rehook has been taken out and put back in more times than I care to count)

---

### Post by jesusfreak107 on 2008-04-29
> **scragar said:**
> you can remap an ISO file to be treated as a partition as far as the system is concerned:

```
grub> map (hd1,1)PATHtoISO.iso (hd4)
grub> map --rehook
grub> chainloader (hd4)+1
grub> rootnoverify (hd4)
grub> boot
```

But be warned that this doesn't always work based on grub versions(the feature of --rehook has been taken out and put back in more times than I care to count)
So that little peice of code is EXACTLY what I enter at the bottom of the menu.lst file (except I put the path to the iso, of course)?  That sounds like it just might work!  I am actually still downloading the iso file, and, this being an older lappy, it is going to take another 2&1/2 hours.  However, in the meantime,  I would appreciate further input.  You can never have too many right answers.

---

### Post by scragar on 2008-04-29
no, you don't do it like that, you run grub directly from a command line, and then copy those lines into it, changing hd1,1 to your HD/partition (if you don't know it use ```
find /boot/grub/stage1
```)

---

### Post by jesusfreak107 on 2008-04-29
Ok, in response to your warning about the grub version, I am using grub4dos.  Also, what I am looking for is a code of string to add to the bottom of the menu.lst file.  If I need to download any extra files, and add them, too, I am willing to do that.  I am a Linux user, and do not have any experience using DOS, so modifying anything that way is not really an option, for me.  I can open the menu.lst file, and modify it however I want, and I have a bit of experience doing that.  If someone could tell me what to add/do to that, I would be most grateful. 

:guitar::guitar::guitar:

---

### Post by jesusfreak107 on 2008-05-01
> **scragar said:**
> no, you don't do it like that, you run grub directly from a command line, and then copy those lines into it, changing hd1,1 to your HD/partition (if you don't know it use ```
find /boot/grub/stage1
```)
I get what you are saying, now.  I tried that, and it had some hard drive errors, I forget what they were, specifically.  If I run into them again, I will remember them, and post them here.  If I could boot off of a USB device, that would work best.  However, when running GRUB, it does not know I have a USB device (as far as I can tell, I might not be doing something that I need to be doing.  Any ideas/code on mounting/booting off of a USB device (w/iso) with GRUB?

---

### Post by Legre on 2009-06-11
[FONT=Lucida Console][SIZE=3]------------------------
[/SIZE][/FONT][FONT=Lucida Console][SIZE=3]timeout 3
default 0


title Test ISO Boot
map (hd0,0)/Test.iso (hd3)
map --rehook
chainloader (hd3)+1
rootnoverify (hd3)
boot[/SIZE][/FONT]  [SIZE=3][FONT=Lucida Console]
------------------------[/FONT]
I put this code in menu.lst,[/SIZE][SIZE=3] tried 3 different images (Windows PE, Hiren's and Ubuntu 9.04) [/SIZE][SIZE=3] and got the same error[/SIZE]  :

[IMG]http://www.geocities.com/legreman/images/testisoboot.png[/IMG]
[SIZE=3]any clues?..[/SIZE]

---

### Post by FuturePusher on 2009-06-15
Hi Legre!

I'm doing a bit of research on this, actually with about half an hour of googling "from all angles" just behind me... and some previous laboration as well.

I think You may be on to it there... and suspect You're getting the HDD errors because the ISO You're using most likely is actually a CD/DVD disc... very much different from HDD's from a hardware & hardware level accessing code's point of view.

So, try this if You can:
see if switching out "(hd3)" in the "map", "chainloader" & "rootnoverify" instructions to "(cd)" is possible... that _could_ be the trick!

If I had the time to lab further myself right now, I'd be on it in a split second...

I'll post again if I either test it out before You, or hopefully to congratulate You on Your success with it.. ;)


/Mike



> **Legre said:**
> [FONT=Lucida Console][SIZE=3]------------------------
[/SIZE][/FONT][FONT=Lucida Console][SIZE=3]timeout 3
default 0


title Test ISO Boot
map (hd0,0)/Test.iso (hd3)
map --rehook
chainloader (hd3)+1
rootnoverify (hd3)
boot[/SIZE][/FONT]  [SIZE=3][FONT=Lucida Console]
------------------------[/FONT]
I put this code in menu.lst,[/SIZE][SIZE=3] tried 3 different images (Windows PE, Hiren's and Ubuntu 9.04) [/SIZE][SIZE=3] and got the same error[/SIZE]  :

(( --- Image cut out --- ))) 

---

### Post by PukingPenguin on 2009-06-15
[Like this?]("http://ubuntuforums.org/archive/index.php/t-457318.html")

---

### Post by milesprowl on 2009-06-17
Total noob here....

I tried the following using grub4dos in a usb stick. The iso booted but the live os would not boot. It stopped at an (initramfs) prompt

```

title Ubuntu 8.10 (Live CD)
map (hd0,0)/ubuntu810.iso (hd32)
map --rehook
chainloader (hd32)
rootnoverify (hd32)
boot

```

Thinking it might be an issue of the iso getting unmounted I tried dumping the contents of the iso into a folder and pointing it to the kernel but got the same results using the following:

```

title Ubuntu 8.10
find --set-root /U810/casper/initrd.gz
kernel /U810/casper/vmlinuz boot=casper persistent rw splash
initrd /U810/casper/initrd.gz
boot

```

---

### Post by MichiGreat on 2010-12-29
> **jesusfreak107 said:**
> How do I use GRUB to boot directly off of an iso? 

English speaking users, go here: [http://ansi.interblc.com/2010/02/06/howto-boot-iso-images-via-grub2-with-ubuntu/comment-page-1/#comment-49077](http://ansi.interblc.com/2010/02/06/howto-boot-iso-images-via-grub2-with-ubuntu/comment-page-1/#comment-49077)

German speaking users, go here: [http://michigreat.a.wiki-site.com/index.php/GRUB](http://michigreat.a.wiki-site.com/index.php/GRUB)

---

