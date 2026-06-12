---
title: "boot problem"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by algrundy on 2010-12-11
Hi,
  I have a HP DV6233se with AMD Turion TL50 with GeForce 6150.  I have been running Version 8.10 desktop with no problems, after installing Version 10.10 when it gets past the Ubuntu screen with the 5 white/red dots the screen locks up with alternating horizonal white and black lines.  Do you have any suggestions?
                                        Thanks,
                                                Alan

---

### Post by ryadav on 2010-12-12
download, build & install the NVidia driver for your GeForce 6150

you may need to install the build tools if you don't have them installed

sudo aptitude build-essential make

you can also install the following (optional)
sudo aptitude install bison autoconf

you may also need to install kernel header files
type, 'uname -r' and find out version of your kernel

do a search for your linux header and install it, type:

sudo aptitude search linux-header

to install the header files, type:
sudo aptitude install linux-header-<your version>

for example on my system i would type
sudo aptitude install linux-image-2.6.35-23-generic

now you can start to install your nvidia driver

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by sikander3786 on 2010-12-12
> **algrundy said:**
> Hi,
  I have a HP DV6233se with AMD Turion TL50 with GeForce 6150.  I have been running Version 8.10 desktop with no problems, after installing Version 10.10 when it gets past the Ubuntu screen with the 5 white/red dots the screen locks up with alternating horizonal white and black lines.  Do you have any suggestions?
                                        Thanks,
                                                Alan
Welcome to the forums :-)

Press and hold down Shift key from your Bios screen until you see the Grub menu. Highlighting the first entry in Grub menu, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" instead (without the quotes). Press Ctrl + X to continue boot. Hopefully, you would be able to boot to the desktop this time.

Once booted successfully, go to System > Administration > Additional Drivers and install the current drivers for your card and the problem should go away for ever ;-)

---

