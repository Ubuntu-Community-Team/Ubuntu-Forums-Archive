---
title: "Stall during boot or installation.  Video?"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by hppyfngy on 2007-02-07
I've installed several flavors of Linux before including Ubuntu, usually on older machines. I wanted to try Beryl so I thoughtI'd try one of my newer machines.

The 6.10 cd boots and I get the options page, but no matter whether I try to install or boot from cd, after the initial splash screen, the screen goes blank and then I get a series of diagonal lines that just sit there...

Any ideas?

> Mainboard : EPoX COMPUTER CO., LTD nForce4-SLI DDR: 9NPA+SLI / 9NPAJSLI / 9NPASLI Series

> Chipset : nVidia nForce4

> Processor : AMD Athlon 64 3500+ @ 2200 MHz

> Physical Memory : 1024 MB (2 x 512 DDR-SDRAM )

> Video Card : Nvidia Corp GeForce 7600 GT

> Hard Disk : WDC (160 GB)

> Hard Disk : WDC (500 GB)

> DVD-Rom Drive : _NEC DVD_RW ND-3550A

> Monitor Type : Samsung SyncMaster - 20 inchs (dvi)

Thanks,
):P

---

### Post by volksman on 2007-02-07
I have the exact same problem.  Had ubuntu already installed on this drive.  Decided I wanted to try Beryl and it needed the lastest version.  So downloaded it and get as far as the Ubuntu splash then it hangs.

Interesting enough I tried 64 and X86 versions of both the desktop and alt CDs.  Same issue.  When I use the 64 bit version the splash is black and white.  When I use X86 its in color.

Either way though this seems like something is busted or a step backwards as this exact machine with the exact same configuration was able to load 6.06 without issue.

What's the deal?

---

### Post by volksman on 2007-02-07
Sorry guy....my fix was posted by aberry5555...this worked for me...I'm on the liveCD right now... :)  this could also be done at the grub boot loader....might wanna try removing the quiet splash from your boot string and see where your's craps out....



This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

---

### Post by hppyfngy on 2007-02-09
Yeah, but I'm Nvidia...

---

### Post by itsu207 on 2007-02-09
Exact same problem. First tried with regular shot, installation was bizarre. Then I used method safe mode graphics, same issue. Change 6.10 AMD64 media to regular i386 installation media, just to discover same bug. Is it a common problem with 6.10?
BTW, I am with NVIDIA 6600GT, donno if that is the source of the problem.

---

### Post by hppyfngy on 2007-02-09
Well, I changed the video to 12x10 16bit (even though the native resolution of my monitor is 16x12) and got the cd to boot.  Haven't tried the install yet...

---

### Post by hppyfngy on 2007-02-10
Actually, I changed resolution to 10x7 16bit and was able to boot and install.  But, now I can't boot the system.  It appears to be booting and then I think it goes to the login page, but the graphics are off the screen so I can't log in.  I can boot in recovery mode, but I don't know the commands to continue.  

I can also boot the cd and access the files.  Can I modify the file from the boot cd that will allow me to boot at 1024x768 16bit, or something else generic that will allow me to get to the gui?  

I'm a real noob so be gentle...

---

### Post by hppyfngy on 2007-02-10
I have tried several things but still only get diagonal lines after the recovery boot, no login screen just these diagonal lines.  I have even entered my name and password at this point and it seems to go on (I hear the music,) and the color of the lines changes, but I never get a desktop.

Can I boot the cd and then download a new driver for my video card and install it? (i.e. replace the old driver)

If so , HOW!

Please help, I'm so close  :(

---

### Post by hppyfngy on 2007-02-11
Well, I don't seem to be getting much help in here, but I'll give it one more try.  

I have gone back to the beginning and installed 6.06, which loads and boots normally.  I went  to upgrade to 6.10 and ended up with the same problem I've described before, diagonal lines.  

So I installed 6.06 again and did the 107 updates called for (everything except the upgrade to 6.10.)  Everything works fine but only at 1024x768, 16bit.  

I dled the Nvidia driver 1.0-9746, and tried to install it from recovery console and it first says it has failed to set runlevel, and then it says it can't find 'ld' sys util.  It also says to make sure I have binutils installed, which I do and 'ld-static' is in the path.  So at this point I can't install the driver and if I try to upgrade to 6.10, I get the same diagonal lines again.  

So, unless I get a response here, I guess I'm off to try another flavor.  :(

---

### Post by hppyfngy on 2007-02-13
onle last bump for the road...

---

