---
title: "linux kernel 2.6.35 installation guide if anyone wants it"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2010-08-17
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#444444][FONT=Lucida Grande][B][SIZE=2]from [here]("http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/")[/SIZE]
[/B]





**[Linux Kernel 2.6.35 installation guide for Ubuntu Linux]("http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/")**

[COLOR=#bbbbbb]Published on [COLOR=#777777]2 August, 2010[/COLOR] in [Linux]("http://www.ramoonus.nl/category/projects/linux-projects/"). [17 Comments]("http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/#comments")Tags: [Linux]("http://www.ramoonus.nl/tag/linux/"), [Ubuntu]("http://www.ramoonus.nl/tag/ubuntu/").[/COLOR]

[LEFT][COLOR=#444444]This short walkthrough describes how to get the latest linux kernel working under Ubuntu Linux without having to compile it yourself.
This tutorial should work with the latest version of Ubuntu Linux (10.04 and 10.10 ) and most distributions based on these versions of Ubuntu Linux like Mint.
The included kernel files have been compiled using the generic ubuntu configuration.
**Note:** nVIDIA ForceWare drivers are automatically installed using DKMS, if you have these installed and up-to-date.
**Installation Guide**

[LIST]
[*]Download [linux-headers-2.6.35-020635_2.6.35-020635_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/linux-headers-2.6.35-020635_2.6.35-020635_all.deb")
[*]Download your kernel headers package;
I386: [linux-headers-2.6.35-020635-generic_2.6.35-020635_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/linux-headers-2.6.35-020635-generic_2.6.35-020635_i386.deb")
AMD64: [linux-headers-2.6.35-020635-generic_2.6.35-020635_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/linux-headers-2.6.35-020635-generic_2.6.35-020635_amd64.deb")
[*]Download your kernel compile;
I386: [linux-image-2.6.35-020635-generic_2.6.35-020635_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/linux-image-2.6.35-020635-generic_2.6.35-020635_i386.deb")
AMD64: [linux-image-2.6.35-020635-generic_2.6.35-020635_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/linux-image-2.6.35-020635-generic_2.6.35-020635_amd64.deb")
[*]Install the files in the _same_ order (else it won`t work!)
[*]In the terminal run:
sudo update-grub
[*]Reboot and select the kernel from the bootloader menu
If it`s not there check all steps (and ofcourse errors)
[/LIST]
For those who want to do their “own” compiles, the source is also available; [linux-source-2.6.35_2.6.35-020635_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/linux-source-2.6.35_2.6.35-020635_all.deb")
[/COLOR][/LEFT]
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]

---

### Post by shantiq on 2010-08-19
well i put this on my lucid machine for 3 days and it seems it gives me the desktop freezes i was getting on 2.6.32 back in may 2010


so i have gone back to 2.6.34 


[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][SIZE=3][COLOR=DarkRed]**[Linux Kernel 2.6.34 installation guide for Ubuntu Linux 10.04]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/") **[/COLOR][/SIZE]

Published on 19 May, 2010 in [Linux]("http://www.ramoonus.nl/category/projects/linux-projects/"). [19 Comments]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/#comments") Tags: [Linux]("http://www.ramoonus.nl/tag/linux/"), [nVIDIA]("http://www.ramoonus.nl/tag/nvidia/"), [Ubuntu]("http://www.ramoonus.nl/tag/ubuntu/"). 

This short walkthrough describes how to get the latest linux kernel working under Ubuntu Linux without having to compile it yourself.
This tutorial should work with the latest version of Ubuntu Linux (10.04 ) and all distributions based on these versions of Ubuntu Linux like Mint.
The included kernel files have been compiled using the generic ubuntu configuration. 
**Note:** nVIDIA ForceWare drivers are automatically installed using DKMS
**Installation Guide**

[LIST=1]
[*]Download [linux-headers-2.6.34-020634_2.6.34-020634_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb")
[*]Download your kernel headers package;
I386: [linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb")
AMD64: [linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
[*]Download your kernel compile;
I386: [linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb")
AMD64: [linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
[*]Install the files in the same order (else it won`t work!)
[*]In the terminal run:
sudo update-grub
[*]Reboot and select the kernel from the bootloader menu
[/LIST]
[/FONT][/FONT][/COLOR]

which seems to be the best fit for lucid on my machine


if you want to revert or move about install


```
sudo aptitude install startupmanager
```
gives you easy movement  ====> default operating system

i ran a  ```
sudo update-grub
``` afterwards to make sure do not know if startupmanager does it automatically

to check what you have running after or before a change

```
uname -r

```



**also useful (to remove old kernels)**


Open the Synaptic package manager from the System->Administration menu.

Click the &#8220;Search&#8221; button on the tool bar and search for linux-image-2.

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one. Find the package corresponding to the kernel to you running currently (this is the kernel you found in the terminal window). Make sure you keep that one. Now you can uninstall the old kernels from the list by clicking their boxes and selecting &#8220;Mark for Removal&#8221;.

Caution! Be careful of what you remove. Ensure that you don&#8217;t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.

Click the apply button on the tool bar to complete the changes.

Your computer and Grub menu should now be free of old kernels.

---

### Post by shantiq on 2010-09-04
and then i moved up to maverick

and found again the same old freezes so back down to 2.6.34 while we wait for a 2.6.35 which does not do that


2.6.35.20 looking good so far

---

### Post by dino99 on 2010-09-04
glance at errors logged to go ahead with this issue

---

### Post by shantiq on 2010-09-04
hi dino sorry did not understand what you wrote; could you please say a little more?

do you mean set it back to 2.6.35 and see what errors are shown when it freezes?

how do i find a reading for that?   i think the terminal usually survives a freeze 

is that where i look and what do i need to enter?


shan

---

