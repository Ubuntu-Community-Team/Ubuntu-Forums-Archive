---
title: "Ubuntu Dual Boot - Going to Terminal after recovery boot"
date: 2021-08-01
forum: Installation &amp; Upgrades
---

### Post by Dafong on 2021-08-01
Going to try and provide as much info here as I can.

I bought a new laptop to put Linux on specifically, it is a G713 Rog Strix, AMD CPU, Nvidia RTX 3060 GPU.

I followed the instructions in this tutorial:

[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

The URL says windows 8 - but the actual content has been updated to Windows 10.

I get to the boot loader screen.  After a long period on the bios screen, Ubuntu will load - the first time.

On the second boot, it will not load, it will sit on the bios screen - indefinitely.

I followed advice I read online, went to the recovery screen, checked file system, fixed DPKG, and then resume boot. That would boot into Ubuntu.  For awhile I simply went to the recovery screen and resumed boot, and this worked and got me into Ubuntu.

However, after updating the Nvidia drivers to 460 - when I attempt to do this, it loads into a Terminal View. - i.e. I get a prompt much like you would see when you open Terminal.  It is just a black screen with this prompt.  From this prompt I can see the directory via LS (Desktop etc) but there is no desktop environment.

My biggest issue is that the HDMI port on the laptop doesn't work on the nouveau drivers (port works fine on windows - so not the port or the cable) - hence my trying to update to the Nvidia drivers.  Under nouveau it recognises a generic Nvidia device - not a specific device and the HDMI port doesn't work.

However, updating appears to break the ability of Ubuntu to load into the desktop environment and I can't find anything that would assist me in loading that environment.

I have turned off secure boot - as that was advice I found online in relation to the Nvidia drivers - it didn't make any difference.

I have re-installed Ubuntu - twice now - and it doesn't appear to make any difference.

Anyone got any advice on how I can get Ubuntu to load into the desktop environment AND recognise my GPU so I can use the HDMI port?

---

### Post by Dafong on 2021-08-01
For the record, I thought I would give 21 a chance, so installed that.

It all worked fine.  HDMI port worked, boots straight in.  Not sure what the issue is with 20 but whatever it is, it is fixed in 21. (I didn't even bother updating the Nvidia drivers).

I forgot to mention that while installing 20 - the screen size went funky and I had to tab down to the continue buttons because I couldn't see them on the screen.  Not sure that is relevant, but forgot to mention it.

---

### Post by tea for one on 2021-08-01
> **Dafong said:**
>  Not sure what the issue is with 20 but whatever it is, it is fixed in 21.

Probably a later kernel has improved support for your new hardware.

---

### Post by garvinrick4 on 2021-08-04
tea for one commented on new kernel here is how to install one.
 [COLOR=#ff0000]_**There are more Nvidia drivers after 5.9 Kernel**_[/COLOR]

[URL="https://kernel.ubuntu.com/~kernel-ppa/mainline/"]https://kernel.ubuntu.com/~kernel-ppa/mainline/
[/URL]
Choose a kernel such as 5.13 is latest or what you want.
if low latency choose the three marked as such  and the all.deb and if
not use the generic three and the all deb
if Download has other deb packages transfer to Desktop just
as long as no other .deb only the 4 you downloaded.

#Lets install all 4 at once
> cd Desktop
> ls
#no other .deb packages continue to install
> sudo dpkg -i *.deb
#after install complete reboot
> shutdown -r now
#run to see kernel you are now running 
> uname -a

---

