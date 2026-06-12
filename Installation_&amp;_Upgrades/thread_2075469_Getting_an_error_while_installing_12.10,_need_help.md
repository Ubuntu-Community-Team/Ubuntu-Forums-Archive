---
title: "Getting an error while installing 12.10, need help"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by luke738 on 2012-10-23
When I try to install Ubuntu 12.10 on my desktop, after I select my language in the installer and click continue, the screen goes black and this error is displayed (Not all at once, there is a delay between each line: 
```
[drm] nouveau 0000:02:00.0: GPU lockup - switching to software fbcon
[drm] nouveau 0000:02:00.0: Failed to idle channel 1.
[drm] nouveau 0000:02:00.0: PFIFO - playlist update failed
[drm] nouveau 0000:02:00.0: Failed to idle channel 2.
[drm] nouveau 0000:02:00.0: PFIFO - playlist update failed
```
After that, the screen goes black again, flashes, and the 2nd through 5th lines of the error are shown again. I am installing from a USB drive, which I know works as it installed without a problem on my laptop. I've tried to find a solution to this problem, and while nothing I've tried has worked, it seems to be related to my video card drivers. I have a Nvidia GTX 580 installed currently. Any help would be appreciated, and if you need me to supply some more information I can.

---

### Post by consultator on 2012-10-25
Same Problem here on Kubuntu 12.10 (DVD): Live-"CD": after booting in KDE surface, I can move the Cursor, but when I browse any Icon -> Blackscreen with same "failed"-reports.
Installation: in the Partition-Step, after setting the Partition size and want to go to the next Step -> Blackscreen. Also by choosing my previously created Partitions. Waiting for 2 minutes and i get a motley Screen for a few seconds.

I´ve also a Nvidia GTX 580 in use.

Thanking you in anticipation.

---

### Post by dino99 on 2012-10-25
thats often the case with too new hardware: you need the latest kernel and driver (not included into 12.10 by default)

should work with 3.6.3 kernel and nouveau from xorg-edgers ppa

boot on recovery mode (hold shift key down at bios end process to get the grub menu), and  try fixing installation (in case), then select "root command line"

run these commands:

sudo add-apt-repository  ppa:xorg-edgers/ppa     ( damn smiley, its _:_xorg )
sudo apt-get update
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install ppa-purge
sudo ppa-purge  ppa:xorg-edgers/ppa

thats the 1rst step installing the latest "nouveau" driver then resetting to genuine sources.

next step is getting a newer kernel:

sudo mkdir kern
cd kern
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/*](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/*)

ls kern
( list of the downloaded packages. You will see several files ending either with i386.deb (32 bits) and amd64 (64 bits)

you need  to install the packages related to the installed system (32 or 64):
2 headers : linux-headers......all.deb   &   linux-headers.... i386.deb (example)
2 images:  linux-image.....i386.deb   & linux-image-extra.....i386.deb

so with "ls" list now you can delete the packages you dont need:

sudo rm thepackagename2delete
( repeate for each one)

when you only have the required packages, then you can safely installed them:

sudo dpkg -i *

exit
and reboot

---

### Post by consultator on 2012-10-28
Good Morning,
now i want to share my latest findings.

Installed Kubuntu with noapic, nolapic & nomodeset - 0 Blackscreen during the complete Installation.
After boot in KDE Surface, it stops loading during the Splash Screen, greyed, unclickable Desktop in the Background.

-> worn out **dino99** to do list. Grub 2 Recovery Mode.
one Correction, * didn´t work with http:// ->>>

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa

next step: newer kernel:

sudo mkdir kern
cd kern
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb

sudo dpkg -i *

After this, the grey-Desktop-Problem remains.
->>> solution from another thread
sudo apt-get update 
sudo apt-get upgrade

The Problem remains also, installed following and it works.
sudo apt-get install nvidia-current


Last Words: dino99, thank you! :)

---

### Post by sdetheridge on 2012-11-07
I've just run into this problem, but the solution described here does not work for me. Recap:

Initial install, ran into PFIFO issue as before.
Installed fine using noapic nolapic nomodeset, but will not boot normally
In recovery mode, installed 3.6.3 kernel, xserver-xorg-video-nouveau from xorg-edgers ppa, and updated packages. Still will not boot normally.

Also tried using the whole of xorg-edgers ppa. i.e.:
add-apt-repository ppa:xorg-edgers/ppa
aptitude update
aptitude upgrade

Boot crashes hard, no keyboard/mouse response. When rebooting into recovery mode, xorg.log complains about a crash (floating point exception) inside nvidia_drv. (Don't have full contents of log here, I'm back inside Windows)

Removing nvidia-current means that I can initially boot to a login screen, but it bombs shortly afterwards with PFIFO issue as before.

Note: I have *two* GTX 580s, in SLI. Don't know if this is causing the additional problems?

---

### Post by Mangus on 2012-11-09
Same problem here.

I've a new HD where I want to install ubuntu and I can't event start the install process.

When I boot from the dvd, either I choose "try ubuntu" or "install ubuntu" I get that ugly message

[drm]nouveau 0000:01:00.0:Failed to idle channel ....

it repeats itself for some lines and then the system hangs.

I read that I should install some kernel or packages with atp but what if I cannot even install ubuntu the first time?

I've a desktop pc without integrated graphic card and an asus geforce gtx580.

---

### Post by GiGaZ on 2013-03-12
I had the same problem and I fixed it by doing this:


[LIST]
[*]When you select the device from which you wanted to boot (Ubuntu LiveUSB or CD), press any key to enable NOMODESET: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
[*]Then you install Ubuntu as usually 
[*]When you installed Ubuntu, restart PC and in the boot loader click "e" and after "quiet splash" write "nomodeset" 
[*]Click Crtl+x 
[*]Login and install Nvidia drivers as described here: [https://www.benjaminwiedmann.net/fix-nouveau-driver-issues-on-ubuntu-12-04-install-nvidia-drivers.html](https://www.benjaminwiedmann.net/fix-nouveau-driver-issues-on-ubuntu-12-04-install-nvidia-drivers.html) 
[/LIST]

This worked for me. The problem is that novueau drivers are not optimised for Nvidia GTX 580 and probably also for some other cards, but novueau drivers are included in the kernel.

You could also fix this problem by uninstalling the novueau drivers and installing nvidia's own drivers from the website but I am not experienced enought to tell you how to do it.

I hope this fixed your problem.

Žiga

---

