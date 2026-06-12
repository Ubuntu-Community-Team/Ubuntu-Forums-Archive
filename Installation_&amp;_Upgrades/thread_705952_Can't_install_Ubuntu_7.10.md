---
title: "Can't install Ubuntu 7.10"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Cyntrox on 2008-02-23
Okay, so I downloaded the Ubuntu 7.10 ISO from the site, burned it, verified it, and ran it. I got the following errors:

[  593.999153] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  606.0476770] Buffer I/O error on device sr0, logical block 0

They were repeated many times with different values, before the screen went completely black. What could be the problem?

I just formatted the thing and installed Windows XP, and made a separate partition for Ubuntu. I've tried burning the disk 2 times. I have no idea what's happening. Help? Thanks in advance.

---

### Post by CRCarl on 2008-02-24
What type of computer? Model, manufacturer would be helpful.

---

### Post by toa on 2008-02-24
> **Cyntrox said:**
> Okay, so I downloaded the Ubuntu 7.10 ISO from the site, burned it, verified it, and ran it. I got the following errors:

[  593.999153] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  606.0476770] Buffer I/O error on device sr0, logical block 0

They were repeated many times with different values, before the screen went completely black. What could be the problem?

I just formatted the thing and installed Windows XP, and made a separate partition for Ubuntu. I've tried burning the disk 2 times. I have no idea what's happening. Help? Thanks in advance.

How did you make a partition, and what type. can you be specific in exactly when you have the error, after boot, after logo, ... blue screen ... ?

---

### Post by Cyntrox on 2008-02-24
> **toa said:**
> How did you make a partition, and what type. can you be specific in exactly when you have the error, after boot, after logo, ... blue screen ... ?
Okay, sorry.

I made the partition while installing Windows with the Windows XP disk. It is about 15 gb, so size shouldn't be a problem. What do you mean by what type of partition? It is not yet formatted.

When I press "install" after booting from the disk,  I can see the Ubuntu logo and loading bar-like thing, it goes back and forth a few times before the errors start coming.

And I don't get any bluescreen.

---

### Post by Pumalite on 2008-02-24
You have to format that space, preferably ext3. Ubuntu does not install on unallocated space.

---

### Post by Cyntrox on 2008-02-24
> **CRCarl said:**
> What type of computer? Model, manufacturer would be helpful.
Sorry, I did not see your post at first.

I built it myself. Here's my list of components:

NorthQ power supply 4775 ATX 400W
Silent, 140mm Fan, 12-17dBA, 20/24pin

Asus P5P800, I865PE, Socket-775, ATX
SATA, GbLAN, DDR, Sound, AGP8X

Intel Pentium 4 630 3.0GHz Socket
LGA775, 2MB, EM64T, BOXED w/fan

Logitech OEM Ultra X Flat Keyboard (As if it would matter, I'm not using thsi any more... Awesome keyboard though.)
PS/2, High End Silver Finish, Bulk

MSI GeForce 6800GT 256MB GDDR3 (NOTE: I've upgraded this to a nVidia GeFrorce 7900 GS)
AGP8X, NX6800GT-TD256, DVI/TV-Out,Retail

NZXT Guardian Gaming Case Sort
Intelligent Led (Without power supply)

Sony DVD-brenner DWQ28AB2 IDE OEM Black
DVD+R/+RW and DVD-R/-RW (Dual Layer)

TwinMOS PC3200 DDR-DIMM 1024MB Dual Pack
Kit w/two matched PC3200 CL2.5 DDRs

> **Pumalite said:**
> You have to format that space, preferably ext3. Ubuntu does not install on unallocated space.
Tried, didn't work. It doesn't surprise me, though, as I don't get far enough to select where to install it anyways.

---

### Post by Pumalite on 2008-02-24
Get Gparted Live CD and format that partition: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Unallocated space is seen grey.. Format it.
Install Ubuntu, go Manual and create a partition for '/' (mount point '/'), 1 GB for /swap (mount point 'swap'), then press 'Forward'

---

### Post by Cyntrox on 2008-02-24
> **Pumalite said:**
> Get Gparted Live CD and format that partition: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Unallocated space is seen grey.. Format it.
Install Ubuntu, go Manual and create a partition for '/' (mount point '/'), 1 GB for /swap (mount point 'swap'), then press 'Forward'
There is no gray space... Pictures:

[http://img178.imageshack.us/img178/8471/dscn0693sg2.jpg](http://img178.imageshack.us/img178/8471/dscn0693sg2.jpg)
[http://img99.imageshack.us/img99/1773/dscn0694fb3.jpg](http://img99.imageshack.us/img99/1773/dscn0694fb3.jpg)

---

### Post by Pumalite on 2008-02-24
You have to choose from the menu how you are going to boot it. 'autoconfiguration' would be my first try.

---

### Post by Cyntrox on 2008-02-24
Okay, thanks, I did, now I got some kind of command prompt and I'm not sure what to type... I'm still on the Gparted CD by the way:

[http://img442.imageshack.us/img442/16/dscn0696qx6.jpg]("http://img442.imageshack.us/img442/16/dscn0696qx6.jpg")

---

### Post by Pumalite on 2008-02-24
Choose the 'vesa' option.

---

### Post by Cyntrox on 2008-02-24
Okay, I've now got an ext3 partition for Ubuntu..
> **Pumalite said:**
> Install Ubuntu, go Manual and create a partition for '/' (mount point '/'), 1 GB for /swap (mount point 'swap'), then press 'Forward'
Do you mean from the Ubuntu disc? I tried that, and I somehow got into a prompt that said "boot:" I don't  know if it's right, but when I tried to type "mount point'/'", it says "Could not find kernel image: mount." Am I doing it wrong:

---

### Post by Pumalite on 2008-02-24
I mean to boot Gparted.

---

### Post by Cyntrox on 2008-02-24
The Gparted command line tells me that "mount point '/'" is an unrecognized command (error 27)...

---

### Post by Pumalite on 2008-02-24
Where it says 'mount point' you just have to plant a /

---

### Post by Cyntrox on 2008-02-24
I can find two command lines - one that I access by hitting 'c' the first thing after booting from the Gparted CD, and one that I can access by going into auto-configuration, where I after some time get a GUI, and can click "command" or something like that.

First command line:
> grub> mount point /

Error 27: Unrecognized command

grub> mount point '/'

Error 27: Unrecognized command

grub> mount point swap

Error 27: Unrecognized command

Second command line:
> gparted ~ # mount point /
mount: spacial device point does not exist
gparted ~ # mount point '/'
mount: spacial device point does not exist
gparted ~ # mount point swap
mount: mount point swap does not exist
gparted ~ # mount point 'swap'
mount: mount point 'swap' does not exist

So yeah, I'm not sure where I'm supposed to type it... =/ Excuse my stupidity, please.

---

### Post by Pumalite on 2008-02-24
Enumerate to me all the choices listed in Gparted Live CD when you first boot it.

---

### Post by Cyntrox on 2008-02-24
The main menu:
> ***** Select a row, using arrow, and press Enter, please  *****
GParted-liveCD 0.3.4-11 (auto-configuration)
GParted-liveCD 0.3.4-11 (auto-configuration & enable cd ejection)
GParted-liveCD (Do X Configuration = mkxf86config)
GParted-liveCD (auto-configuration - noapic - acpi=off)
GParted-liveCD (auto-configuration and framebuffer)
GParted-liveCD (boot off External -usb -cd : /dev/sr0)
GParted-liveCD Macbook option
GParted-liveCD Force VESA driver
GParted-liveCD Force I740 driver
GParted-liveCD Force I810 driver
GParted-liveCD HP laptop (pci=conf1)
GParted-liveCD HP laptop (pci=conf2)
GParted-liveCD HP laptop (pci=conf3)
Boot MBR on first hard drive
Boot partition #1 on first hard drive
Boot partition #2 on first hard drive
Boot partition #3 on first hard drive
Boot partition #4 on first hard drive
Boot MBR on second hard drive
Boot partition #1 on second hard drive

Beneath it:> Use the (arrow pointing up) and (arrow pointing down) keys to selevt which entry is highlighted. Press enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for a command line.

---

### Post by Pumalite on 2008-02-24
use 'Force Vesa Driver'

---

### Post by Cyntrox on 2008-02-25
Okay, did that, lots of text was printed, and after some time I could select which keyboard language to use. After selecting that, I got this:

[http://img265.imageshack.us/img265/4947/dscn0697mp8.jpg]("http://img265.imageshack.us/img265/4947/dscn0697mp8.jpg")

(you should be able to read what it says everywhere)

---

### Post by Pumalite on 2008-02-25
Get to work: post # 5

---

### Post by Cyntrox on 2008-02-25
I have formatted space for it - /dev/hda5 (the 3rd entry down the list on the picture)

---

### Post by Pumalite on 2008-02-25
Post # 7:
'Install Ubuntu, go Manual and create a partition for '/' (mount point '/'), 1 GB for /swap (mount point 'swap'), then press 'Forward'
__________________

---

### Post by Cyntrox on 2008-02-25
I am sure I must seem terribly stupid... But what do you mean by go manual? How do I do it?

---

### Post by Pumalite on 2008-02-25
Boot up your Live CD, start the installation and you'll see it:
option 1.-Available space,etc. Last option: Manual

---

### Post by Pumalite on 2008-02-25
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Cyntrox on 2008-02-25
> **Pumalite said:**
> Boot up your Live CD, start the installation and you'll see it:
option 1.-Available space,etc. Last option: Manual
Well, my problem all along has kinda been that after I start the installation, I see the Ubuntu logo and loading bar, then I get errors, as seen in my first post...

---

### Post by Charcoal1981 on 2008-02-25
edit: miss read post - please ignore me

---

### Post by Pumalite on 2008-02-25
> **Cyntrox said:**
> Well, my problem all along has kinda been that after I start the installation, I see the Ubuntu logo and loading bar, then I get errors, as seen in my first post...

Try the Alternate CD.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by Cyntrox on 2008-02-25
That works, thanks a lot! =D

Not the end of my problems, but that's a topic for another thread...

---

### Post by Pumalite on 2008-02-25
You are welcome. Good luck.

---

