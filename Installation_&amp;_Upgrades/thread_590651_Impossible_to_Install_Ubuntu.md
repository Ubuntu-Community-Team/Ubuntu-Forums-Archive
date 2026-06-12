---
title: "Impossible to Install Ubuntu"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by TylerM on 2007-10-24
My Specs:

Intel Quad Q6600
2GB of PNY XLR8 RAM
NVIDIA 8800GTX
WD 320GB HDD SATA
x2 DVD Burners IDE

When using the 7.10 CD, I can get to the menu.  When I chose any of the install/livecd options, the computer loads the kernel, then the progress bar goes across... over and over. Finally the bar starts moving like it's actually loading something then the computer reboots. Before all of this it wouldn't even do that much without the floppy drive disabled in BIOS.  I'm starting to see why people don't embrace the Linux movement, if you can't even have a simple install with new hardware.  Please respond half the time someone posts something they don't get help.

---

### Post by PmDematagoda on 2007-10-24
At what speed did you burn the Live CD? If you burnt it faster than 4x then the CD maybe corrupted.

---

### Post by gtdaqua on 2007-10-25
Had similar issue - Ubuntu live CD will simply hang at some point!! Restart the installation, it will hang at some other point. 

Somewhere I read burning ISO images at high-speed could corrupt the CD. That particular Ubuntu Live CD was burned at 48x. Then I burned a fresh copy at 24x and had no problems!! 

People tend to write at high-speeds (nero defaults to max!). Lower the speed to 12x or 4x, I am sure you will get through. 

Optionally you can use the "Check CD for defects" option in the install/boot menu to check the CD.

---

### Post by TylerM on 2007-10-27
I burned them all at 1x even and the CD still does not work.  This is discouraging.  :(

I'm using a P35 chipset motherboard BTW if that has anything to do with anything :confused:

---

### Post by Ricardo_V on 2007-10-27
> **TylerM said:**
> I burned them all at 1x even and the CD still does not work.  This is discouraging.  :(

I'm using a P35 chipset motherboard BTW if that has anything to do with anything :confused:

Did you try checksum?

---

### Post by dptxp on 2007-10-27
iso should be burned with 'BURN IMAGE' command.

Infrarecorder in Windows and K3B in Linux burn CDs well with default
settings (Auto speed). They burn at about 20X speed and I
have never had any problem with over 50 iso so far.

---

### Post by Pumalite on 2007-10-27
Set SATA/IDE Controller to AHCI in BIOS.(TylerM I mean)

---

### Post by Tosa on 2007-10-27
Thanks Pumalite. I have GA P35 DS3 (Intel E2160 2GB/800 and nV 8600GT), try to install Kubuntu 7.10 64.
Enabling AHCI didn't help much, though. I got through *Installing Base System* once without lock up, but got stuck up in *Installing Software*. Right now I'm locked up in *Preparing to configure x11-common*.
I'll try again, but I'm on the verge of giving up Linux...

---

### Post by TylerM on 2007-10-27
OK, I got it to load the LiveCD *and* install the operating system by adding irq=nopoll (read about it somewhere) in the command line when installing.  But now the OS won't load from GRUB unless I disable all controllers in BIOS--USB, Firewire, etc. I've tried the AHCI thing multiple times and it hasn't helped.  Thanks for the help.

---

### Post by TylerM on 2007-10-27
Bump

---

### Post by TylerM on 2007-10-28
Bump :(

---

### Post by Triptoph on 2007-10-28
Also having problems installing using the live CD.  Can get to the menu, but after choosing to install, even in safe graphics mode, the screen goes black for me and there is no further HDD activity.  Specs:

Asus P5K Deluxe motherboard P35 chipset
Ati X800XL GPU
Intel Q6600 CPU
4GB RAM
64-bit ISO

---

### Post by Pumalite on 2007-10-28
> **Triptoph said:**
> Also having problems installing using the live CD.  Can get to the menu, but after choosing to install, even in safe graphics mode, the screen goes black for me and there is no further HDD activity.  Specs:

Asus P5K Deluxe motherboard P35 chipset
Ati X800XL GPU
Intel Q6600 CPU
4GB RAM
64-bit ISO
You should go with the Alternate CD and even then you might have problems due to your P35 chipset. But try.

---

### Post by TylerM on 2007-10-28
Alternate Install CD does not work.  Let me remind you that I got the P35 to install by using irq=nopoll in the command line before installing.  But now I can't get my install to boot unless I disable USB and Firewire on my computer.

---

### Post by Triptoph on 2007-10-28
> **Pumalite said:**
> You should go with the Alternate CD and even then you might have problems due to your P35 chipset. But try.

The alt CD worked for me... installing it anyways, when trying to boot afterwards into X I run into the same problem as before, I can only use recovery mode.

---

### Post by Pumalite on 2007-10-28
Have you guys tried to configure your xserver?
sudo dpkg-reconfigure xserver-xorg
Ctrl+Alt+F1 to get command line.

---

### Post by Triptoph on 2007-10-28
> **Pumalite said:**
> Have you guys tried to configure your xserver?
sudo dpkg-reconfigure xserver-xorg
Ctrl+Alt+F1 to get command line.

Yes, unfortunately using the vesa driver didn't help in my situation either.

---

### Post by Pumalite on 2007-10-28
Try this:

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

---

### Post by Triptoph on 2007-10-28
> **Pumalite said:**
> Try this:

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

I have the X800XL card myself, and I would love to try that with the ATi driver; however when I boot into recovery mode at the prompt, apt-get reports that it can't resolve hostnames.  I'm not sure how to troubleshoot that in Linux.  Install used DHCP to connect with my network card without problems it seemed so not sure why it's not working in recovery...

---

### Post by TylerM on 2007-10-29
> **Pumalite said:**
> Try this:

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

My problem, the original problem, is not with graphics at all.  It's something with the chipset.  I can't boot into Ubuntu unless I disable USB, Firewire, and Ethernet.  (I can only boot if I load the Fail Safe defaults in BIOS, which disables all of these). So please help with the chipset problem.

---

### Post by Pumalite on 2007-10-29
The problem with chipset unfortunately resides in the inner workings of the kernel itself. Nevertheless, here is a collection of boot parameters that you guys might want to try ( no assurances that they will work):
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by TylerM on 2007-10-29
> **Pumalite said:**
> The problem with chipset unfortunately resides in the inner workings of the kernel itself. Nevertheless, here is a collection of boot parameters that you guys might want to try ( no assurances that they will work):
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

None of the boot parameters there look to be of help.  Ubuntu will not boot unless BIOS is set to fail safe defaults (USB, NETWORK, and FIREWIRE disabled).  Anyone have any idea?

---

### Post by Triptoph on 2007-10-30
I just installed Fedora Core and that worked correctly, so I used the xorg.conf that it made to alter Ubuntu's xorg.conf, but that didn't help things.  I don't think my problem is a graphics issue now either.  But that said, the fact that Fedora Core installed correctly on my hardware (Asus P5K deluxe mobo w/ P35 chipset, q6600 cpu, ati x800, 4gb ram) might provide some clues

---

### Post by TylerM on 2007-11-02
Bumpage!

---

### Post by DonLorenzo on 2007-11-03
I have a P35 based MoBo: Asus P5K Deluxe. and a Core2 Quad 6600 CPU, 4GB RAM.
The Gutsy (7.10) LiveCD boots just fine for me. I have yet to install it, however. I'm running Feisty (7.04) in "production" here.

There are some hints (found while researching mobo) that suggest that you should set the BIOS controls to disable some specific hardware that you do not have on your machine. 
In my configuration I disabled the Floppy drive (not present) and WiFi (for security. I use wired ethernet).

HTH.

---

### Post by Triptoph on 2007-11-03
> **DonLorenzo said:**
> I have a P35 based MoBo: Asus P5K Deluxe. and a Core2 Quad 6600 CPU, 4GB RAM.
The Gutsy (7.10) LiveCD boots just fine for me. I have yet to install it, however. I'm running Feisty (7.04) in "production" here.

There are some hints (found while researching mobo) that suggest that you should set the BIOS controls to disable some specific hardware that you do not have on your machine. 
In my configuration I disabled the Floppy drive (not present) and WiFi (for security. I use wired ethernet).

HTH.

I also have the Asus P5K Deluxe, Q6600 CPU and 4GB of RAM.  Are you using the 32 or 64 bit version?  I couldn't get ubuntu's 64 bit version to load at all, and don't know why - it didn't seem to be a graphics problem.  The 32 bit version loaded, and with great pains I was able to install the proprietary ATi driver for my X800 XL card.  What video card are you using as well?  

Tyler, have you tried other distros?  I found that ubuntu 64 and MEPIS 64 could not install at all for me, but Fedora Core 7 worked fine without any modifications (8 is coming out next wednesday!).  Installing another distro might give you some tips on how to get ubuntu working for you, or might solve your problem altogether if you find that you like the distro.

---

### Post by DonLorenzo on 2007-11-29
> **Triptoph said:**
> I also have the Asus P5K Deluxe, Q6600 CPU and 4GB of RAM.  Are you using the 32 or 64 bit version?  I couldn't get ubuntu's 64 bit version to load at all, and don't know why - it didn't seem to be a graphics problem.  The 32 bit version loaded, and with great pains I was able to install the proprietary ATi driver for my X800 XL card.  What video card are you using as well?  

Tyler, have you tried other distros?  I found that ubuntu 64 and MEPIS 64 could not install at all for me, but Fedora Core 7 worked fine without any modifications (8 is coming out next wednesday!).  Installing another distro might give you some tips on how to get ubuntu working for you, or might solve your problem altogether if you find that you like the distro.

I'm running in 32bit mode.
yes, I know. I lose about 300MB of RAM by not running 64bit.

---

