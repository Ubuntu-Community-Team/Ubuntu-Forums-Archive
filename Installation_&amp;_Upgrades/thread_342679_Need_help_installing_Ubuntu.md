---
title: "Need help installing Ubuntu"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by dorion on 2007-01-20
Hi, I'm a pretty proficient Windows user, but I'm a complete idiot for Linux. I've been trying to install Ubuntu(6.06 and 6.10 amd64 versions) on and off for the last couple of months with no success. I'm pretty sure its my computer set up, because I've also tried Knoppix, Debian, Suse, heck even Solaris with no success. Right now when I try to install Ubuntu the first screen(GRUB) shows up fine and in color, but then the next screen with the loading bar is Black and White and the loading bar is corrupted. It stays like this awhile with the little corrupted loading bar going back and forth, then sometimes it shows some text. After this my monitor just goes to a completely black screen, still on just displaying nothing. At this point I've tried to get to the console, but the screen just stays blank. This could be that I've heard a thousand different combinations of shift, ctrl,alt, f1, and f2 and none of them have worked.

I would really like to get some kind of linux working on my computer, and I would perfer Ubuntu because I got some experience with it over the summer(mostly falling in love with the UI.)

My system is:
AMD Athlon 64 3000+
Soltek K890 Pro
ATI Radeon X850XT
Some SoundBlaster Sound Card
A really cheap TV Tuner using the Philips TV7131 chip
2 40gig SATA Hard drives running in the Via software Raid for Windows
A 30 gig ATA drive attached to the Promise Controller on my MB
A Sony DVD Drive on the slave channel for my 30gig harddrive
A SATA Plextor DVD Writer on the Promise Controller on my MB

I want to blame my video card or my convulted drive setup.

So can anyone help me?

---

### Post by mcduck on 2007-01-20
I'd blame the video card too :)

But that's not a problem. Just use the Alternate CD to install Ubuntu, and after install on the first boot select 'safe mode' (or whatever it's called) from the Grub menu, and run following commands to get your graphics card drivers installed & configured:

```
apt-get install xorg-driver-fglrx
aticonfig --initial
reboot
```
After that you should be able to boot into the desktop.

edit: If you do this, don't use the OEM install that's available with the Alternate CD. It's not any use for normal users, and only makes things more complicated..

---

### Post by AMT on 2007-01-20
I am having the same problem, with a little different setup and worse results. I tried installing Ubuntu 6.10 on my system (specs below) to see if I can make the switch from Windows to Linux. I figured I'd run a dual boot install.

The first time, I tried the 64-bit version and ended up having the same result described by dorion. Black and white distorted loading screen, then it crashes. The second time around I tried the 32-bit version. It didn't work either, it got to the Ubuntu CD OS loading screen, but then it crashed. At that point I remembered that my motherboard required specific IDE hard-disk drivers to be loaded before installing an OS. Because of this Ubuntu screwed my hard drive and I had to reformat and re-install Windows XP Pro. So my two questions are...

How do I install Ubuntu with the needed IDE motherboard drivers?
How do I install Ubuntu 64-bit on my system?

Windows XP Professional 32-bit
Intel Pentium D 920 (can run at 64-bit)
ASUS P5LD2 Deluxe Motherboard
2 Gigs RAM
eVGA GeForce 7800GT
SoundBlaster Audigy 2 Value

The CD's I burned were fine. I was able to install the 32-bit version of Ubuntu on another machine in my house, and the 64-bit CD checked out fine.

- Andrew

---

