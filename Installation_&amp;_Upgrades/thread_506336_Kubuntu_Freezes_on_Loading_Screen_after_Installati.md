---
title: "Kubuntu Freezes on Loading Screen after Installation"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by Sir Funk on 2007-07-21
Hey everyone,

I've been having one helluva time trying to get Ubuntu on my system.  When I first started trying to install Ubuntu 7.04 from the LiveCD I would get the "can't access tty" error after the initial boot menu.  I tried the boot=top modprobe piix exit solution, but that didn't work for me.  I get the same problem with the Kubuntu 7.04 Live CD.  I then tried to install with the earlier versions (the LTS ones, Dapper Drake I presume?) but those wouldn't work either.  I finally managed to install Kubuntu 7.04 with the Alternate CD and adding "irqpoll" to the command line when I installed.  After it finally installed and asked me to reboot I was able to get the GRUB boot loader (I'm dual booting with Windows XP), but when I let it boot it just freezes at the Kubuntu splash screen with the loading bar.

Also, it won't let me boot into Recovery mode, after it stops scrolling so fast that I can't really catch anything it says it goes into a seemingly endless cycle between lines that begin with an increasing number (ex: [125.9044]) and then either hda, hdb, or hdc.  I don't remember exactly what they say afterwards but something like DMA recovery or timeout or something else (there's 3 different lines that they repeat between).  I left it on for at least 30-45 minutes and it kept on doing the same process just with an ever increasing number at the beginning of the line.

So I can't really do much unless I can do it from the GRUB loader.  I've tried booting with irqpoll at the end of the boot line that's like "root (hd1,hd0)" or some such, but that doesn't seem to affect anything.

Anyone have any idea as to what I can try?  If at all possible be a little specific as I haven't used linux in a long time (and even then I didn't use it very extensively).  My system specs are:

1.4Ghz AthlonXP CPU
ASUS A7V8X Motherboard
756MB RAM
ATI Radeon 9700 Pro
hda: 80GB HD (Windows XP)
hdb: 30GB HD (Potentially Linux)

If you need any other information don't hesitate to ask!  I've been at this for a couple of days now and my hair's beginning to grey from the stress!  I also have about 8 different Ubuntu/Kubuntu install discs between the different versions and alternate cds that I think I'm going to start smashing over my head if I can't get this to work soon! ;P

Thanks!

-Funk

---

### Post by Pumalite on 2007-07-21
Are you dual booting? XP? Vista? If XP; defrag several times, erase all temp files, then use Gparted. If Vista; you HAVE TO partition from WITHIN Vista, otherwise Vista will not let anything run in that computer.

---

### Post by Sir Funk on 2007-07-21
Hi, thanks for the response!

Yes I am dual booting with windows XP.  I have WinXP on my main hard drive and Kubuntu on my second hard drive.  Do you mean to defrag the main hard drive that XP is on?  If so I am doing that now.  Hopefully the solution is something as simple as this!

Thanks for your time,

-Funk

---

### Post by Pumalite on 2007-07-21
Sorry, I meant to defrag XP if you were planing to partition the same hard drive. I'll look at the problem again and come back.

---

### Post by Pumalite on 2007-07-21
Try Super Grub.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Sir Funk on 2007-07-21
I gave Super Grub a shot but it still does the same thing--freezes up on the Kubuntu loading splash screen.

Thanks for the suggestion, though!

-Funk

---

### Post by Pumalite on 2007-07-21
Something is incompatible in your harware. I think. You could give Xubuntu Alternate CD a shot:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

Good luck.

---

### Post by Sir Funk on 2007-07-21
Thanks for the quick reply,

Installed Xubuntu and got the same thing...except I'd left while it was frozen and when I came back it had dropped me to a shell prompt, giving me the old "can't access tty" error.  I imagine my other installations would've done this if I were patient enough to wait the 5 or so minutes it took to drop to the shell.  I guess I'll go research solutions to that problem as I've only encountered that problem BEFORE installing *ubuntu.  

Thanks for your help!

-Funk

---

### Post by Pumalite on 2007-07-21
I have a mix of fixes that I have collected in this forum. See if one solves your problem:

when I boot, the screen shows

Starting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

Good luck!

---

### Post by danimall on 2007-07-21
I have an HP dv6408nr notebook and I was able to get Ubuntu 6.10 to install correctly onto my computer using the live CD, but now when I try to start it up it will get to the Ubuntu loading splash screen and then just go completely blank. Is this an issue with the Nvidia drivers for my graphics card? If so then how would I work around it? I am still kind of new to linux so if you have any basic solutions then that would be great. My specs are listed below.

Microprocessor 1.8 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-56
Microprocessor Cache 512KB+512KB L2 Cache
Memory 1024 MB DDR2 System Memory (2 Dimm)
Memory Max Max supported 2048 MB
Video Graphics NVIDIA GeForce Go 6150 (UMA)
Video Memory Up to 287 MB

It probably doesn't make a difference but I am dual booting Ubuntu 6.10 and Vista.

Also I saw a mention that "YOU MUST" partition in Vista for it to work.  I did my partitioning with Gparted and it seemed to work.  I can get the grub screen to load up just fine.  It just when I try to load up Ubuntu that it freezes once it gets past the loading splash screen.

I did notice that when I originally loaded up Gparted, X.org wouldn't load correctly unless I used the Vesa video driver and set my resolution to 1024x768.  I figured that this might be related to loading Ubuntu since they both use Gnome.  So this is just a thought.

---

### Post by Pumalite on 2007-07-21
You might try the following at the command line:

sudo dpkg-reconfigure xserver-xorg (Use 'vesa as driver) If you get in, then later you can install a 'Legacy driver for your card.

If you have no command line and are frozen out, then I would start again and this time I would use the Vista partitioner.

---

### Post by Sir Funk on 2007-07-21
Thanks for the suggestions.

When I try modprobe piix at the prompt it just doesn't do anything.  The cursor will go to the next line and just sit there indefinitely.  After a while the screen will go blank but it comes back when i press a button (screensave I guess?).  The computer won't respond to anything although I am able to type.

I tried the second solution, but it doesn't recognize  the sudo command and I tried the commands leaving sudo out to no avail as well.

As for the third option, I've been able to load up a LiveCD once (the other times it freezes), what should I do once I've gotten everything booted through a LiveCD so that I can boot normally?

Thanks again for your time,

-Funk

---

### Post by upchucky on 2007-07-21
i have seen the can't find tty before, i have a post about it somewhere, perhaps u should do a new thread that states how to fix the cant find tty so others can find it easier?

nice to see u found it :)

---

