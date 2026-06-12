---
title: "[SOLVED] Installing Hardy on external HDD"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Piraja on 2008-08-10
Dear all!

I decided to try and follow, *mutatis mutandis*, DaBruGo's archived tutorial titled **SUCCESS - Breezy loaded on external USB drive!** (started in Oct. 2005):
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
Now as I reached Step 3, i.e. partitioning, and more specifically, "Prepare partitions > Edit partition", I began to wonder about the mount point. I suppose it must be just "/", but I'd like to be absolutely sure.

If you did not already figure it out, I'm trying to install Hardy on a partition of 20GB on an external HDD (WD 500 GB), i.e. /dev/sda4 in my desktop PC, running WinXP on the internal HDD (kids wanna play Sims, that's my only excuse to keep WinXP on /dev/hda1...).

I could not find much information on installing Hardy on an external USB hard drive, so help would be very much appreciated! Thanks!

---

### Post by logos34 on 2008-08-10
yep, '/' on sda4.  Don't forget /swap.

Make sure to install grub to the mbr of the external and toggle the boot drive in the BIOS--otherwise you won't be able to boot windows when the external is disconnected.

-> Ready to Install' screen>'Advanced' button lower right>change '(hd0)' to /dev/sda.

Continue using the live cd after installation completes.  Mount your new / partition and edit menu.lst:

gksudo gedit /path/to/boot/grub/menu.lst

change the 'root' lines (and 'groot' line near top) to (hd**0**,3).

---

### Post by Piraja on 2008-08-10
Thanks Logos34!

Another question: I'm using the Ubuntu LiveCD (Hardy) in spite of the caveat in the original tutorial (saying you should use "install cd" instead — I'm not sure if this is actually a difference between Breezy and Hardy rather than between install cd and live cd).

Now as I rebooted the live cd, there appears to be no "rescue" option. If I press F1 and get the Help Index, and choose F4 (Additional boot methods; rescuing a broken system), I'm told "There is no dedicated rescue mode on this CD. However, since the entire system runs from the CD, it is possible to use the command line and/or graphical tools provided to rescue a broken system, [etc. etc.]".

So, I'm a bit cautious to proceed now...

---

### Post by logos34 on 2008-08-10
well, like it says you don't need a 'rescue' option since it's a live cd--you can do just about anything repairs from the live session, which gives you a terminal and everything you need to edit stuff. 

Not sure what you're worried about but there is another way if you want to be absolutely certain ubuntu and grub goes where it's supposed to and doesn't overwrite windows/ntloader on the internal drive:  simply disconnect the internal drive before running the ubuntu installation.  Select 'manual' and choose sda4 as target '/' partition.  Grub will by default go on the MBR of that disk--no need to edit anything.

Only thing is you will have to manually add a windows entry to /etc/fstab if you want to access it from linux:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.04%20LTS%20(Hardy%20Heron](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.04%20LTS%20(Hardy%20Heron))

---

### Post by Piraja on 2008-08-10
> **logos34 said:**
> it's a live cd
:)
Precisely... and I'm not only cautious but also impatient, so I started using the live cd option already before receiving your reply. 

One of the beautiful things at the Ubuntu Forums is the kind very real-time live support from the community and speedy replies. So thanks again!

---

### Post by Piraja on 2008-08-10
Once again... Now I'm running the live cd. This is what DaBruGo's tutorial tells me:

[INDENT]> ( STEP 5 ) When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your external drive from the list.
(Mine was mount /dev/discs/disc1/part1 ... but yours may be different depending on the number and/or types of drives in your system)

COMMENT: /dev/discs mount points start with disc0 (with 0 meaning the first drive in a system). So, my mount point of /dev/discs/disc1/part1 was really the second disk [disc1] (the sda drive we are working with) and the first partition [part1] on that disk.

( STEP 6 ) When it comes up to a terminal window (with RESCUE MODE in the upper left corner) and just sits there, hold down Ctrl-Alt-F2 to open another terminal window for us to do our edits in.

( STEP 7 ) Type in these lines before we start editing out files ...

mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>
[/INDENT]

Running the LiveCD, my mount point for the correct partition appears to be /media/disk-1. Now after discovering that, I open a terminal. Now I begin to wonder whether I should navigate to /media/disk-1 (cd /media/disk-1) and type the lines in question from that location, or just at the LiveCD user prompt (ubuntu@ubuntu). Well, I tried both ways. However, both times I sudoed the line "mount -tproc proc /target/proc" I got the message: "mount: mount point /target/proc does not exist". 

Hmm... I begin to feel I'm doing something stupid here. Should I replace the word "/target" with "/media/disk-1" or what? Maybe so... [EDIT: Heck no! see below...]

But do I dare to try... well, let's see... maybe I'll see whether there's a Wiki about mount, proc and -tproc... [that's right, let's see... and ponder for a minute...]

---

### Post by Piraja on 2008-08-10
I also tried "ls -la /target" and the response is:
```
ls: cannot access /target: No such file or directory
```

---

### Post by Piraja on 2008-08-10
Oh, I discovered that there does not seem to be a /target (or /target/proc for that matter) directory at all, just /proc. Should I drop /target from the syntax and try this instead:

```
sudo mount -tproc proc /proc
```

Any suggestions? You can see what a nOOb I am.

---

### Post by logos34 on 2008-08-10
no, you double-click the 'Install' icon on the desktop...That will start up the ubiquity installer...choose 'manual' partitioning option and go from there...it should be apparent which disk is your external and which the internal

post back if unsure

---

### Post by Piraja on 2008-08-10
Oh, thanks, I've done the install and am running the live CD now and I'm confident with the partitions (/dev/sdb4 mounted and all); it appears that the syntax was wrong. I tried this one &#8212;

```
mount -t proc/target/proc
```

&#8212; and in response, I got just the command prompt, so it seems that it must be the correct syntax(?).

However, the next line in the tutorial &#8212;

```
chroot /target
```

returns

```
chroot: cannot change root directory to /target: No such file or directory
```

I searched for the "target" directories and found actually several, but in the following locations: 

/usr/src/linux-headers-2.6.24-16-generic/include/config/netfilter/xt [With a lock emblem in Nautilus; I suppose this is the /usr directory of the LiveCD??)

/media/disk-1/usr/src/linux-headers-2.6.24-16-generic/include/config/netfilter/xt  [The external drive partition, /dev/sdb4, I presume. No lock emblem here]

---

### Post by logos34 on 2008-08-10
forget the chroot stuff--don't need it.  

If / (sdb4) is mounting at /media/disk-1 or whatever, do:

gksudo gedit /media/disk-1/boot/grub/menu.lst

---

### Post by Piraja on 2008-08-11
OK! Actually, before I went to sleep (it's now 8:43AM in Helsinki), I finally skipped the chroot /target step (part of Step 7 in DaBruGo's post #1). Everything went smoothly after that and I rebooted and got the Grub menu from the new Ubuntu installation (yippee!) which looked really promising: the three Ubuntu kernels in /dev/sdb4 first and then WinXP in /dev/hda1 just as they should be (and even yet another Ubuntu installation from a previous try in /dev/sdb2, but that's another story).

So I press ENTER and hope for the best &#8212; but what I see next is Grub Error 17. I fiddled about with the Super Grub Disk for a while but could not boot into /dev/sdb4 from SGB either.

I suppose I will have to try and edit the menu.lst file again, or replace it with the backup I made before following DaBruGo's instructions in Step 11, and try what happens. Wish me luck, I will report the eventual success (for there shall be victory)!

---

### Post by Piraja on 2008-08-11
Yess!! Diddit! I changed the boot order so that new kernel in /dev/sdb4 has 0,3 (and not 0,0). Now I have Ubuntu up and running from my external HDD!

Many thanks again to Logos34, DaBruGo whose thread I followed, and all those who contributed to that archived thread!

P.S. Might be a good idea to update the tutorial for Hardy. There are some differences between Hardy and Breezy that must be taken into account, and it appears that Dave's Step 7 can be skipped, etc.

---

### Post by logos34 on 2008-08-11
glad to hear everything worked out for you

enjoy

---

