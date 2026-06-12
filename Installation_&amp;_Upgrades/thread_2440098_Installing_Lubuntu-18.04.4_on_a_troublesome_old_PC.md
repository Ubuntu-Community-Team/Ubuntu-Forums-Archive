---
title: "Installing Lubuntu-18.04.4 on a troublesome old PC"
date: 2020-04-05
forum: Installation &amp; Upgrades
---

### Post by fljarvis on 2020-04-05
PREAMBLE

The CloudReady web site records the fact that the
HP Compaq dc5800 pc with BIOS version 01.53 or
lower will not boot any OS running Linux kernels based
on v4.14 (or newer).  To overcome this problem, the
BIOS should be updated to version 01.60.

(The software for checking BIOS details, dmidecode,
 is pre-installed on Lubuntu-18.04.4)

The HP Customer Support centre no longer has
software upgrades for the dc5800)
**********************************************************************
I was, until today, totally ignorant of all the above information:
I simply couldn't understand why my dc5800 would not boot
any linux with kernel newer than 4.13 (kernel panic every time)
while my dc5700, an even older, smaller machine, has had no
such problem.  In my ignorance, I came up with the following
approach:

  i) install Lubuntu-18.04,4 on my dc5700
 ii) from [https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13.16](https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13.16),
     download the 3 components making up the kernel 4.13.16 used
     in Artful Aardvark 17.10 and Ubuntu 18.04 beta:
     -linux-headers-4.13.16-041316*all.deb
     -linux-headers-4.13.16-041316-generic*i386.deb
     -linux-image-4.13.16-041316-generic*i386.deb

     (in accessing this site, my Firefox browser required 2 steps:
      -go to [https://kernel.ubuntu.com;](https://kernel.ubuntu.com;) once there, append to the
       address line  ~kernel-ppa and hit enter, then follow the path
       to reach the packages).
iii)  install the 3 components with gdebi in the above order; 
     reboot and select the 4.13.16 kernel
 iv) run sudo dpkg --remove     the 8 packages listed below:
         linux-headers-5.3.0-28
         linux-headers-5.3.0-28-generic
         linux-headers-generic-hwe-18.04
         linux-generic-hwe-18.04
         linux-modules-5.3.0-28-generic
         linux-modules-extras-5.3.0-28-generic
         linux-image-5.3.0-28-generic
         linux-image-generic-hwe-18.04
 v)  reboot into the only kernel remaining,  4.13.16
vi)  install additional software to individual requirements
vii)  install and run systemback to produce a remastered .iso
      which did install successfully on the dc5800 and runs well.
**************************************************************************
This process might be useful if other recalcitrant old PC's are encountered.

Len E.

---

### Post by mörgæs on 2020-04-06
Thanks, please mark the thread solved. It will help other users.

It's a general situation for HP DCxxxx's that the BIOS needs updating. I did the same for a [dc7700]("https://ubuntuforums.org/showthread.php?t=361236&page=86&p=12775075&viewfull=1#post12775075"), and after that I have been able to install any Buntu release I tried.

---

### Post by fljarvis on 2020-04-26
Another troublesome old PC that I have is a HP Pavilion Media Centre
m8247c which has the NVIDIA GeForce 6150 SE Graphics card.

Fortunately, installing Lubuntu-18.04.4 on it was relatively easy, thanks
to the enormous past contributions by Ubuntu experts in other contexts.

There were 3 basic steps involved:

  i)  downgrade Xorg - because the original xserver-xorg-core, version 1.19.6
      was required.
 II)  downgrade the linux kernel
iii)   install the proprietary NVIDIA drivers.

*************************************************************************************
 Downgrade Xorg

Thanks to the expert advice provided by Ji M in the 
"ubuntu.handbook.org/index.php/2019/08/upgrade-ubuntu18-04-3-kernel-5-0-org"
article, there is a stupendously simple way to achieve the downgrade;
enter the following 2 terminal commands in succession:

sudo apt remove xserver-xorg-*-hwe-18.04
sudo apt install xorg

**********************************************************************************************
Downgrade kernel   --  similar to the steps described at the top of this thread

  i)  From synaptic, install the following 9 packages:
             libdw1
             linux-headers-4.15.0-96
             linux-headers-4.15.0-96-generic
             linux-image-4.15.0-96-generic
             linux-modules-4.15.0-96-generic
             linux-modules-extra-4.15.0-96-generic
             linux-tools-4.15.0-96
             linux-tools-4.15.0-96-generic
             linux-tools-common

      Reboot, select kernel 4.15.0-96

 ii)   Run sudo dpkg --remove      listing the 8
       kernel 5.3.0-28-related packages shown
       at the top of this thread

       Reboot into the only kernel remaining, 4.15.0-96

******************************************************************
Install the proprietary NVIDIA drivers.

The original definitive thread on how to do this was
created by enigma9o7, and is located on page 34
of this forum, [https://ubuntuformums.org/showthread.php?t=2396263](https://ubuntuformums.org/showthread.php?t=2396263)

It was closed on Dec. 5, 2019.

**************************************************************
Len E.

---

