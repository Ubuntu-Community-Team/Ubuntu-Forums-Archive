---
title: "full install of ubuntu on USB is the most painful experience ever."
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by jack5 on 2013-08-01
I have installed and run ubuntu usb and it shows a blinking underscore ("_") at boot. I have checked google extensively and researched the topic but still could not find the answer. I have tried installing Ubuntu 12.04, 13.04 and Lubuntu 13.04 without any success. 

I do not want:
1) persistent USB
2) partition my USB 
3) use complicated instructions involving terminal commands

Here are my specs:
Intel i5-3450
AMD Radeon HD 7800 series.

Here are the steps taken:
1. winMd5sum check on ISO
2. install ubuntu onto USB drive (installer drive) using universal usb installer.
3. unplugged all my hardrives
4. run ubuntu without installing
5. unmounted the USB drive (Ubuntu drive) that I want to install it on.
6. run gpart to create new partition and formatted the drive to ex4
7. run installer - selected the "Ubuntu drive", selected boot to / and format to use ex4
8. fail.

---

### Post by ajgreeny on 2013-08-01
You may need to use the boot option "nomodeset" because of that graphic card.

Is ubuntu actually installed on that USB disk?  Attach it to your machine when alrerady running a live DVD or USB system, and navigate to the usb disk you have installed to to see if the system really did install.

If everything seems to be there, open the /media/[COLOR=#ff0000]usbdrive[/COLOR]/etc/default/grub file and edit the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to read
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

You will need to open the grub file mentioned with gksudo gedit /media/[COLOR=#ff0000]usbdrive[/COLOR]/etc/default/grub in order to be able to edit and save it in the live session.

PS:  The usbdrive (red above) will show as some other named folder in your system, so use whatever is showing as that disk in your commands.

---

### Post by ian-weisser on 2013-08-01
Wait...you want to overwrite the same USB drive that you are using to run the installer?
Yeah, that won't work. Last time I looked, the USB installer loads into RAM, but all of the packages that need to be installed don't load into RAM. So you are overwriting them during the initial partitioning.

I have installed to USB, and it's not difficult at all. The easy method is to use a CD drive or another USB drive.
If you insist on using the same USB drive, or installing from an existing system, it's quite doable (done it), but there is no "easy" method.
I suggest the Minimal .iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If you are using anything less than USB 3.0, expect a long boot (I had 30-40 seconds to a command prompt, 90-120 seconds to a lightdm prompt) and a fairly slow, laggy system. I used command line only - graphical desktops were unusably slow.

---

### Post by jack5 on 2013-08-02
thank you for all your replies. 

> **ajgreeny said:**
> You may need to use the boot option "nomodeset" because of that graphic card.

If everything seems to be there, open the /media/[COLOR=#ff0000]usbdrive[/COLOR]/etc/default/grub file and edit the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to read
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

You will need to open the grub file mentioned with gksudo gedit /media/[COLOR=#ff0000]usbdrive[/COLOR]/etc/default/grub in order to be able to edit and save it in the live session.


I opened the Ubuntu USB and all the files seems to be there. I opened /media/ and nothing is inside it. I located a similar file at [COLOR=#ff0000]usbdrive[/COLOR]/etc/default/grub, but could not save due to permissions. How can I use gksudo gedit to edit grub on the usbdrive? *note: i am on Ubuntu 13.04

edit: I found how to edit grub on an installed OS but not onto a USB stick via Live Ubuntu. [http://askubuntu.com/questions/128128/how-to-boot-without-nomodeset](http://askubuntu.com/questions/128128/how-to-boot-without-nomodeset) 

Clarification: I am using two USB. One as an installer and another for Ubuntu.

---

### Post by sudodus on 2013-08-02
What you try should be possible unless the graphics card won't cooperate with any available driver. So please continue along the tips of *ajgreeny*.

There is one more step though. You need to transfer the added/changed boot option to /boot/grub/grub.cfg, which is normally done when booted into the system (with **[FONT=courier new]sudo update-grub[/FONT]**) but it can be done manually by editing the lines in containing 'quiet splash' in that file

```
 gksudo gedit [COLOR=#ff0000]usbdrive[/COLOR]/boot/grub/grub.cfg
```

You can also try booting in ***recovery mode*** from the grub menu.
-o-

I suggest that you try a short-cut according to the following link to get a portable Lubuntu system (16 GB 13.04 or 4 GB Saucy alpha-2).

[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)

You may still need to use a boot option and later on a proprietary driver for your graphics chip/card, but since USB is slower than internal drives, it can be a good idea to have a light version of Ubuntu (Lubuntu instead of the standard flavour with Unity).

---

### Post by jack5 on 2013-08-02
> **sudodus said:**
> What you try should be possible unless the graphics card won't cooperate with any available driver. So please continue along the tips of *ajgreeny*.

There is one more step though. You need to transfer the added/changed boot option to /boot/grub/grub.cfg, which is normally done when booted into the system (with **[FONT=courier new]sudo update-grub[/FONT]**) but it can be done manually by editing the lines in containing 'quiet splash' in that file

```
 gksudo gedit [COLOR=#ff0000]usbdrive[/COLOR]/boot/grub/grub.cfg
```

You can also try booting in ***recovery mode*** from the grub menu.
-o-


Thank you for your reply.

I am new to the terminal and have difficulty accessing other hard drives through the terminal. In Files, I see the name of the USB drive as: "32 GB Volume". However, on top of the window I see it says d48ff598-f4b8-4279-9d14-c4046c79a4d3. What do i type in [COLOR=#ff0000]usbdrive[/COLOR] you stated in the code above?

---

### Post by sudodus on 2013-08-02
Run the command ```
df
``` which will show something like this

```
/dev/sdd1        3627640   2190060      1253264  64% [COLOR=#ff0000]/media/lubuntu-saucy-a2[/COLOR]
```

It means that the device /dev/sdd1 is mounted on the directory [COLOR=#ff0000]/media/lubuntu-saucy-a2[/COLOR] in the file system, the mount point. Use that (corresponding to the [COLOR=#ff0000]red[/COLOR] text here).

---

### Post by jack5 on 2013-08-02
thanks. followed the instructions and added nomodeset to "quiet splash". 

the problem still occurs, namely the blinking underscore

---

### Post by sudodus on 2013-08-02
Did you add nomodeset in[COLOR=#ff0000] **[FONT=courier new]usbdrive[/FONT]**[/COLOR]**[FONT=courier new]/boot/grub/grub.cfg [/FONT]**?

Next step:

Remove **[FONT=courier new]quiet splash[/FONT]** and add **[FONT=courier new]text[/FONT]** boot options and try again. This time you should get text scrolling during startup, showing which programs that start properly (or not). Finally you arrive at a text screen (the graphical desktop environment is not started). If this works, it is likely that the problems are connected to the graphics.

Or try with a live session (boot a live session (try [X]Ubuntu) from the install USB drive) and check if you get a graphical desktop.

---

### Post by jack5 on 2013-08-02
I did not add nomodeset to [COLOR=#ff0000] **[FONT=courier new]usbdrive[/FONT]**[/COLOR][B][FONT=courier new]/boot/grub/grub.cfg

[/FONT][/B][FONT=courier new]the file looks significantly different. Where do I add nomodeset?

thank you for your quick response.
[/FONT]

---

### Post by sudodus on 2013-08-02
You need to transfer the added/changed  boot option to /boot/grub/grub.cfg, which is normally done when booted  into the system (with sudo update-grub) but it can be done manually by [COLOR=#ff0000]editing the lines containing 'quiet splash'[/COLOR] in that file.

```
gksudo gedit [COLOR=#ff0000]usbdrive[/COLOR]/boot/grub/grub.cfg
```

So in your editor: search for [COLOR=#ff0000]'quiet splash' [/COLOR]and edit there (in several places).

---

### Post by jack5 on 2013-08-02
I added nomodeset to all the places with quiet slash. some problem occurs. 

I will follow your next steps later today > Next step:

Remove **[FONT=courier new]quiet splash[/FONT]** and add **[FONT=courier new]text[/FONT]**  boot options and try again. This time you should get text scrolling  during startup, showing which programs that start properly (or not).  Finally you arrive at a text screen (the graphical desktop environment  is not started). If this works, it is likely that the problems are  connected to the graphics.

Or try with a live session (boot a live session (try [X]Ubuntu) from the  install USB drive) and check if you get a graphical desktop.

---

### Post by cshubhamrao on 2013-08-02
Same with me also

---

### Post by Keithustus on 2013-08-02
I'm getting [the same problem on a Lenovo]("http://ubuntuforums.org/showthread.php?t=2164943"): 
Intel i7-2630QM
8 GB RAM
Toshiba 64 GB SSD & WDC 750 GB traditional HDD
NVidia GeForce GT555M (may be faulty), but the onboard integrated graphics works fine
Optiarc Blu Ray drive

So far, just a blinking cursor.  I've tried Ubuntu 13.04 and am now downloading 12.04.

---

### Post by sudodus on 2013-08-02
@ *cshubhamrao* and *Keithustus*

Please try without installing: run live from the install desktop CD/DVDUSB drive.

Try boot options according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and if it does not work, please start your own threads (and make good descriptive titles), because you probably have different problems, and this thread will get confusing trying to help three persons with three problems (even if they look similar at first).

---

### Post by Keithustus on 2013-08-02
My thread is linked in the first line of my post here.  And I was not offered the chance to install.  I see the SYSLINUX screen, then an image of a wide rectangle and of a humanoid in a circle, then the black screen with cursor.

....holy crap those boot options are complicated.  I'm just trying to recover my Windows 7 partitions!

---

### Post by jack5 on 2013-08-03
> **sudodus said:**
> 
Remove **[FONT=courier new]quiet splash[/FONT]** and add **[FONT=courier new]text[/FONT]** boot options and try again. This time you should get text scrolling during startup, showing which programs that start properly (or not). Finally you arrive at a text screen (the graphical desktop environment is not started). If this works, it is likely that the problems are connected to the graphics. 

I done this to grub and grub.cfg. same problem occurs- blinking underscore. I did not remove the nomodeset though.

>  Or try with a live session (boot a live session (try [X]Ubuntu) from the  install USB drive) and check if you get a graphical desktop.

I don't quite understand. I run the Ubuntu installer USB drive and click use Ubuntu without installing and I get a graphical desktop.

---

### Post by sudodus on 2013-08-03
So it works live but not installed. Then the problem can be solved :-)

Exactly which version and flavour are you running live? What is the output of the following commands?

```
 lsb_release -a
```

```
 uname -a
```

And which desktop are you running (Unity)?

Are you running Windows? And UEFI?

Maybe you can try to 'flash' a USB system directly from a compressed image to get a system that works with most computers (but may have problems with some hardware, particularly for graphics and wifi). I run it in a Toshiba laptop and an HP which both have Intel i5 CPUs. The Toshiba has Intel graphics and the HP has ATI/AMD/Radeon graphics and it works with the built-in free drivers.

[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)

If it works, you can gain momentum and in the next steps modify it and get a desktop environment that you prefer.

---

### Post by jack5 on 2013-08-04
**Are you running Windows?**
I run windows 7. But using ubuntu USB to install to another USB.

**UEFI?**
not sure. how do i check?
[B]
Code: lsb_release -a[/B]
No LSB Modules are available
Distrubtor ID: Ubuntu
Description: Ubuntu 13.04
Release: 13.04
Codename: raring

**Code: uname -a**
Linux ubuntu 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x 86_64 GNU Linux

**[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)**
I am pretty reluctant to follow this tutorial since it seems pretty complicated. Chances are that I would mess up the installation.

---

### Post by jack5 on 2013-08-05
Gave up. 

New issue at:
[http://ubuntuforums.org/showthread.php?t=2165496&p=12746197#post12746197](http://ubuntuforums.org/showthread.php?t=2165496&p=12746197#post12746197)

---

### Post by sudodus on 2013-08-06
From the other thead, it seems that the OP has UEFI and needs a 64-bit system, so the Lubuntu-fake-PAE methods which use 32-bit systems will not work. But a persistent live 64-bit system system booted from grub works according to the link to the new issue.

---

### Post by James_V._Conace on 2013-08-07
Hi jack5

I have had the same problem trying to put unix(ubuntu) on a flash drive. I also tried several different installation methods. The best way I could find is to use unetbootin to install it. It worked flawlessly. The only problem I found was that I "assumed" that I should update the OS right after the install, but that clogged up the drive and threw numerous errors. I installed "without" updating the OS and it runs great.

Good Luck!

---

