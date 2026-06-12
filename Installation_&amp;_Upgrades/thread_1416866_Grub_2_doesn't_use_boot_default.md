---
title: "Grub 2 doesn't use boot default"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by tedquick on 2010-02-26
[B]I loaded Kubuntu 9.1 and got a mess in the Grub 2 Boot Menu, which I can't correct.
[/B] 			
 			 			 		   		 		 		I get extra  choices in the Boot menu, and the first few, which are supposedly for  Kubuntu Karmic Koala all put me in a shell, which ends in a black screen, then  shows up a shell once I hit "enter". Then I just have a "intramfs" (?)   prompt. 

So I went into Grub2 to change it, and it refuses to do it. All I get is  a screen full of error messages every time I try, with no change.  Apparently it is looking to access drive sdb8, which is non-existent. I  DO have a drive sda8, though.

So with all the wonderfulness of the indirect system to change Grub 2   how am I supposed to set it right? The old Grub worked fine, and just  took simple changes to the menu.lst file. 

Can't somebody write a program that lets Grub 2 be changed from within  the program, rather than all this running around trying to find what  file to change, and how to get the change to work?

Just to be clear, here are the errors as they show up when grub-update  is flailing around:
"error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
Generating grub.cfg
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
Found Linux image: /boot/vmlinuz-2.6.31-19-generic
error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
Found Memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
error: cannot open '/dev/sdb' while attempting to get disk size
  error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
Found Windows Vista (loader) on /dev/sda3
error: cannot open '/dev/sdb' while attempting to get disk size
  error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
Found Ubuntu 9.10 (9.10) on /dev/sda8
error: cannot open '/dev/sdb' while attempting to get disk size
  error: cannot open '/dev/sdb' while attempting to get disk size"

There my be some typos in there, this is off a hand scribbled list.....

---

### Post by darkod on 2010-02-26
What does fdisk say, why is it looking at /dev/sdb if it doesn't exist?

---

### Post by tedquick on 2010-02-26
Device Boot      Start         End      Blocks   Id  System
/dev/sda1    *           1        9540    76630018    7  HPFS/NTFS
/dev/sda2             9541       19048    76364977    5  Extended
/dev/sda5             9541       14160    37102117   83  Linux
Warning: Partition 5 does not end  on cylinder boundary.
/dev/sda7           14161       16309     17253810    b  FAT32
Warning: Partition 7 does not end on cylinder  boundary.
/dev/sda8           16310       18671    18964732   83   Linux
Warning: Partition 8 does not end on cylinder boundary.
/dev/sda9            18672       18780      867510   82  Linux swap
Warning:  Partition 9 does not end on cylinder boundary.
/dev/sda6            18781       19048     2144677   82  Linux swap
Warning: Partition 6  does not end on cylinder boundary.
/dev/sda3           19049        20023     7823655    7  HPFS/NTFS

---

### Post by presence1960 on 2010-02-26
> **tedquick said:**
> [B]I loaded Kubuntu 9.1 and got a mess in the Grub 2 Boot Menu, which I can't correct.
[/B] 			
 			 			 		   		 		 		I get extra  choices in the Boot menu, and the first few, which are supposedly for  Kubuntu Karmic Koala all put me in a shell, which ends in a black screen, then  shows up a shell once I hit "enter". Then I just have a "intramfs" (?)   prompt. 

So I went into Grub2 to change it, and it refuses to do it. All I get is  a screen full of error messages every time I try, with no change.  Apparently it is looking to access drive sdb8, which is non-existent. I  DO have a drive sda8, though.

So with all the wonderfulness of the indirect system to change Grub 2   how am I supposed to set it right? The old Grub worked fine, and just  took simple changes to the menu.lst file. 

Take a look at your device.map file in /boot/grub.

Can't somebody write a program that lets Grub 2 be changed from within  the program, rather than all this running around trying to find what  file to change, and how to get the change to work?

Just to be clear, here are the errors as they show up when grub-update  is flailing around:
"error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
Generating grub.cfg
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
Found Linux image: /boot/vmlinuz-2.6.31-19-generic
error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
error: cannot open '/dev/sdb' while attempting to get disk size
Found Memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
error: cannot open '/dev/sdb' while attempting to get disk size
  error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
Found Windows Vista (loader) on /dev/sda3
error: cannot open '/dev/sdb' while attempting to get disk size
  error: cannot open '/dev/sdb' while attempting to get disk size
 error: cannot open '/dev/sdb' while attempting to get disk size
Found Ubuntu 9.10 (9.10) on /dev/sda8
error: cannot open '/dev/sdb' while attempting to get disk size
  error: cannot open '/dev/sdb' while attempting to get disk size"

There my be some typos in there, this is off a hand scribbled list.....

Take a look at your device.map file in /boot/grub. If you only have one hard disk it should look like this:

```
(hd0)	/dev/sda
```

I have 3 SATA disks and mine looks like this:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

---

### Post by tedquick on 2010-02-26
No, all I have is sda, 
with Windows 7, Windows Vista, and Kubuntu 9.10 on it in various partitions.

Think I've got a handle on it now from the first reply. Will just take a little while.

---

### Post by tedquick on 2010-02-27
Now I've tried all the advice I could find online, it refused to mount anything when I needed it to in order to follow the so-called instructions I was trying to follow.

Finally got totally disgusted with the whole mess, I was just trying to straghten out the stupid idiotic thing called GRUB 2.

If that's an advance somebody needs to THINK what they're doing!!!!!

SO I reloaded all of Kubuntu 9.10. which only took a few hours, and the CD didn't work right after I downloaded it once again, so I had to burn a second one. FINALLY I got it reloaded from scratch, then I rebooted and found Linux worked fine, but when I had reset  grub 2 to default to SAVE so I could get it to reset to the system I'd used last..... then rebooted and found it doesn't think I have Windows 7 on /dev/sda1, or anywhere else for that matter. It DOES show the Windows Vista rebuild partition that came on the hard drive when I bought it before I got Windows 7 installed later on.

SO, how do I get this system to load Windows 7 at all, and that is where several years worth of work is.

I see nothing that helps with this mess.

---

### Post by tedquick on 2010-02-27
Got it straightened out. Since Karmic Koala only messes up no matter what I try to do with it I reloaded Jaunty Jackelope, which doesn't use the stupid unfinished and totally unworkable Grub 2.

---

### Post by aqk on 2010-03-01
> **tedquick said:**
> .... I reloaded Jaunty Jackelope, which doesn't use the stupid unfinished and totally unworkable Grub 2.

That's the spirit!  Think and act positively!
Honestly This Karmic wotever 9.10 has given me nothing but grief.
I had 9.04 working quite well in a Win-Vista Toshiba laptop. Well, 9.10  took it out and damn near killed my Vista as well! 
  Now I have just installed WinXP on a new larger drive in an old desktop, and it installed and did the Windows updates so flawlessly, that I became inspired and thought I would install Ubuntu 9.10 as a 2nd system on it.
  Well, so far the Grub2 has somehow trashed my win-boot, and given me many other headaches as well.
Dont tell me about "Don't touch grub.conf"...  I have been all through the chmod x and various /etc/grub.d scripts.
And I STILL get this "cannot open `/dev/sdb'"  message when I do a grub2 update!
And  AND!  I still cannot get my  beautiful up-to-date WinXP to boot!  Grrr...
Oh yeah- one more point.  In my 3rd world country (Canada) I am restricted to DIAL-UP! Even with a fiber-optic cable less than one Km from me! 
  The winXp updates took an hour or two (I Dled the SP3 and other fixes from a friends Hi-speed connection in the city)   but these Ubuntu "Karmic" updates...  250Meg!!!  Geez,,,gimme a break! I am smashing the Ubuntu CD as I type this...

  What's going to happen when Ubuntu 10.04 is released? Will it be as crappy as 9.10?  If so, too bad.
Will Canonical survive this mess?  Mark S.?  Are you listening? Or stuck in some space station?

---

### Post by aqk on 2010-03-01
> **darkod said:**
> What does fdisk say, why is it looking at /dev/sdb if it doesn't exist?

Most likely it DOES exist.
It is probably one of these multi-card readers-  CD MD CM whatever picture card devices plugged into a USB connector on the motherboard.

In Windows' case, it shows the empty devices as "disks"  but does not flag them as errors, the way Ubuntu does.   
That's one of my problems now.  I could pull the USB plug off of the mboard, but it seems simpler to say goodbye to Ubunto and stick with Win7...
Alas, my win-7 7100 beta just expired today, so I shall have to shell out (no pun intended) $190 for a production Win-7.
Question:  Would I do this for Ubuntu 9.10?  Take a guess.

---

### Post by darkod on 2010-03-02
> **aqk said:**
> Most likely it DOES exist.
It is probably one of these multi-card readers-  CD MD CM whatever picture card devices plugged into a USB connector on the motherboard.

In Windows' case, it shows the empty devices as "disks"  but does not flag them as errors, the way Ubuntu does.   
That's one of my problems now.  I could pull the USB plug off of the mboard, but it seems simpler to say goodbye to Ubunto and stick with Win7...
Alas, my win-7 7100 beta just expired today, so I shall have to shell out (no pun intended) $190 for a production Win-7.
Question:  Would I do this for Ubuntu 9.10?  Take a guess.

I understand you might be annoyed by some issues, but this is pure speculation on your side. And for example, my netbook has a SD card reader built in and Karmic never showed any issue with it at all.
On the other hand, I've seen plenty of cases of people moving drives around, plugging unplugging because of "fear" to leave a disk with another OS connected during install, I have even seen advice to unplug disks, when in most case that's how they create the issues for themselves.
Few days ago someone complained the instalelr is not seeing the hdd at all, we spent hours troubleshooting to finally realize the hdd is not even installed and working properly.
I'm not saying you don't have your issues with Karmic, but only the OP can know what he/she has in the computer and until we are given information lets not speculate and scare other people off.
Again, my netbook SD card reader is perfectly fine with Karmic.

---

