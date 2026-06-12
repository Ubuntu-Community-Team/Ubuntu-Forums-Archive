---
title: "New install on partition that already has OS installed on it"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2014-04-15
I have a number of partitions on my ASUS EeePC.  What I want to do is install the new version, Lubuntu 14.04, when it is released, on sda1 which currently has Lubuntu 12.04 installed.  It has already reached EOL (the Lubuntu part - not the Ubuntu part).  That would normally be pretty easy according to my research but I also have the boot installed on sda1.   Since I want a new install and not an upgrade, what special steps do I need to do so I do not screw up my computer as well as the other OS installed and the GRUB.

---

### Post by oldfred on 2014-04-15
The boot flag is not used by grub, that is a Windows requirement, but a few BIOS want to see a boot flag. So we still suggest having a boot flag on a primary partition.

What does matter to grub is which boot loader is in the MBR, if you have more than one install.
The version of grub with the boot loader in the MBR will be in control and its install will be first on menu, other installs will be at bottom of menu.

If you have two installs which one do you now boot with? 
A new install will normally install its boot loader to the MBR of sda, unless you use manual install or Something Else and then can choose which drive to install into. Usually best not to install to a partition, but installer does not offer a choice to not install, so occasionally you can install to a partition more as a throwaway or not used boot loader. But then your other install has to be updated to boot new install.

---

### Post by Double.J on 2014-04-15
Hi there! 

Hope I can help, I currently have windows 7, pc-bsd and 5 linux distros in dual boot.

from what I understand of your set up, you don't need to do much. Obviously backup your data, taking care to back up /home. I also like to keep a track of my packages, ppa's and repo's I added in to aid configuring the new system. Check out this [thread]("http://ubuntuforums.org/showthread.php?t=2216533") re that.

as for the bootloader, it should be okay- Lubuntu is currently in charge of boot? When you install new *buntu, it will search the partitions and configure the grub menu as before. If you have distros on there that you had to make custom entries for, it may be worth backing those up as well. (Somethings have gotten easier; for years my ubuntu grub did not see my suse install, with 14.04 beta, it does!)

in terms of special steps, i suppose the easiest way to avoid any errors is to not delete /dev/sda1, just reformat it. That way you don't move any partitions around and your sda1 stays as sda1 (if you delete it and make a new partition it will be called /dev/sda9 this may or may not affect your other installs if they have fstab entries for sda1? 

Jj

---

### Post by Rex Bouwense on 2014-04-15
Thank you for the reply oldfred.  I have three OS's installed; Lubuntu 12.04 on sda1, and two on my extended partition (Lubuntu 13.04 on sda7 and Lubuntu 13.10 on sda8).  I used Grub Custimizer to change the order six months ago to have 13.10 boot first.  I was concerned by using sda1 as the partition for the new install over 12.04 that I would screw up the MBR and thus make the computer unbootable.  I guess my concerns are really not valid.

---

### Post by Rex Bouwense on 2014-04-15
Thanks for the reply Double.J.  With your response and that of oldfred I believe that I am safe to reformat and install Lubuntu 14.04 when it is released in a few days.  I have been using Lubuntu for some time now and want to put the LTS (first ever) on sda1 to which I will move all my data so I can once again play around with other distros.

---

### Post by oldfred on 2014-04-15
If you used grub customizer to change boot order which install is actually in control?

May be best to see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But if you just want new install to be in control then there would be no issues.

---

### Post by Rex Bouwense on 2014-04-15
> If you used grub customizer to change boot order which install is actually in control?
I believe Lubuntu 13.10 is in control now.  It was the last OS installed.
> But if you just want new install to be in control then there would be no issues. 
Yes I will want Lubuntu 14.04 when it is installed to be in charge so I guess I am OK.

Thank you for the Boot Info site.  I was not aware that it existed and have been using one variety of Ubuntu since 8.04.

---

### Post by Double.J on 2014-04-15
> **Rex Bouwense said:**
>  I was not aware that it existed and have been using one variety of Ubuntu since 8.04.

I know that feeling! I always like to have my lts in charge of primary boot from the mbr, then chain boot to the other distro's partitions. Whenever i'd get one of those pinickity installers that doesn't let you modify boot loader installation i'd boot into another distro and go through the old mount and chroot process to get ubuntu back in charge - it was only when i recommended to someone on this forum to do it, another user directed me to boot repair. It's a fantastic tool!

good luck with the install! 

Jj

---

### Post by Rex Bouwense on 2014-04-20
To close this thread out.  I did a fresh install of Lubuntu 14.04 and all is well.  A few adjustments had to be made because I also deleted a whole bunch of kernels from 13.10, all of 12.04 which was overwritten anyway, and the 13.04 OS which had readed EOL.  Grub Customizer makes all that stuff easy.  Thanks again old fred and Double.J.

---

