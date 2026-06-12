---
title: "Kubuntu only works in recovery mode"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Greenflames on 2007-04-30
Help!

I installed Kubuntu 7.04 Feisty Fawn onto a very old computer of mine:

amd semphron 2500
1.5 gig ddr 333
Via400 chipset Motherboard
3 Hard drives

1st HD is Windows XP
2nd HD is Kubuntu
3rd HD is a Windows NTFS <---------store windows file.

After I install Kubuntu,  I restarted my computer and I see the GRUB screen.  My options are as follow.

Kubuntu (i fogot the kernel version)
Kubuntu recovery mode
Memory test <--- something like that
Other Operating Systems:
windows Xp media center

My problem is, I can't start Kubuntu up.  Everytime I choose option one "Kubuntu"(not the recovery mode), I see a script saying Start, Loading <---- then it disappears, and my computer screen is all dark, and hangs.  Kubuntu doesn't start.  I then have to reset the computer.

If I choose the Kubuntu recovery mode option, then I see alot of lines loading with an OK on the far right.  This list load for a while then it stops with a prompt.  I then type in KDM, and it takes me to KDE.

How come option 1 doesn't work and option 2 works.  am I going to use Recovery mode all the time?  What is the diffierence between Recovery mode and Non recovery mode.

Is this normal?



Please help!!!

---

### Post by lsilver on 2007-04-30
I'm no expert on this but I experienced what seems to be the same problem with a 7.04 install on an IBM Thinkcentre.  It turned out to be a graphics mode problem and I was able to fix it by adding vga=771 to the boot instructions.

  sudo gedit /boot/grub/menu.lst

and change the kernel line in for the main boot instruction as per below

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5c4c6695-f724-48aa-ae24-6cf3be3db050 ro splash vga=771

771 is a parameter for 1024 x 768 and is recommended as a good general fix but you may need to try some others (Google "VESA colour depth")

---

### Post by bulldog on 2007-04-30
The question could be,what kind of graphics do you have?
Maybe you have to install some graphics driver?

Try in recovery mode```
sudo dpkg-reconfigure xserver-xorg
``` and try again.

---

### Post by johnmichael on 2007-07-10
I'm having the same issue and its with Ubuntu 7.04. In fact the installation itself wouldn't work unless it was in text mode. I have an NVIDIA GeForce 8800. Installing that driver from the NVIDIA site didn't work. It actually made things worse as it worked when I first installed it and started the X Server but after rebooting I could no longer start X anymore (this all being in recovery mode, regular mode didn't change and still hung). I'm wondering as well how I can start the PC in normal mode instead of recovery.

Heres the sequence of events:

1.) Says hit escape for menu and I don't hit escape

2.) Will show Booting Kernal Alive

3.) Shows a black screen and the hard drive loads.

4.) The Floppy Light comes on

5.) The machine hangs and remains inactive with the hard drive light slowly blinking.

> **lsilver said:**
> I'm no expert on this but I experienced what seems to be the same problem with a 7.04 install on an IBM Thinkcentre.  It turned out to be a graphics mode problem and I was able to fix it by adding vga=771 to the boot instructions.

  sudo gedit /boot/grub/menu.lst

and change the kernel line in for the main boot instruction as per below

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5c4c6695-f724-48aa-ae24-6cf3be3db050 ro splash vga=771

771 is a parameter for 1024 x 768 and is recommended as a good general fix but you may need to try some others (Google "VESA colour depth")

I tried that and I got some weird device error. For the record I'm using a DVI connection. NOT a VGA monitor. My monitor is a flat LCD screen 21 inch sceptre.

My motherboard is an AB9 Pro

The chip is of course a Conroe

It has a Sound Blaster Live I think

An Epson USB Printer 740i which only prints blank pages or very light colored faded lines upon testing

2 gig of memory (I think)

Western Digital Raptor 150 GB Hard Drive

---

### Post by confused57 on 2007-07-10
Maybe this thread will help you install the Nvidia drivers you need:
[http://ubuntuforums.org/showthread.php?t=495464](http://ubuntuforums.org/showthread.php?t=495464)

To get to a GUI, you might try "vesa" or "nv" video drivers...boot into recovery mode, enter:
```
nano /etc/X11/xorg.conf
```
make sure to use a uppercase X and (one)(one)...
page down to the video device section and enter "vesa", with quotes, for the video driver...if this doesn't work you might try "nv"...once you make the change...ctrl+X, y, enter...to save the changes...then reboot:
```
reboot
```

You can also change the video driver in a more interactive mode using:
```
dpkg-reconfigure xserver-xorg
```
you can just use the defaults for most screens, except select vesa for the video driver...

---

### Post by johnmichael on 2007-07-10
Still no good, same problem. Will boot in recovery mode but not regular mode. Says Kernel Alive, a bunch of numbers flash, and thats pretty much it.

---

### Post by Dogers on 2007-07-12
In the GRUB bootloader, ensure the normal Ubuntu kernel is highlighted, hit E, then move to the long line that goes off the screen and hit E again. Remove "splash" from the end and everything boots fine for me.

I've tried removing it from the menu.lst file, but it doesn't appear to take effect, I suspect I need to rerun a GRUB command once I'm in to write it out, or something.. :o

---

### Post by Steah on 2007-09-26
Thanks, Dogers.  I was having very similar problems to those listed here on one of my machines.  I removed the splash and added noapic irqpoll and it is now happy running in normal mode.  Seems my MB was having issues with the PS/2 controller and interrupts.  I have no idea why it wouldn't boot with the splash option and boots just fine if it is removed.

---

