---
title: "Kernel Upgrade failure - Karmic"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by anishd on 2009-11-27
Dear friends,
Yesterday, a new kernel was downloaded and updated automatically by Karmic. Upon restart, a crash was reported. Today, i started update manager, it told to run sudo dpkg --configure -a
I ran the command..and here is the result.


anish@anish-desktop:~$ sudo dpkg --configure -a
[sudo] password for anish: 
Setting up linux-headers-2.6.31-15-generic (2.6.31-15.50) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-15-generic          
 *  nvidia (96.43.13)...                                                        nvidia (96.43.13): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-15-generic (2.6.31-15.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-15-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Debian background: Lake_mapourika_NZ.tga
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sdb9
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-15-generic          
 *  nvidia (96.43.13)...                                                        nvidia (96.43.13): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-15-generic; however:
  Package linux-image-2.6.31-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.15.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-15-generic; however:
  Package linux-headers-2.6.31-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.31-15-generic
 linux-image-2.6.31-15-generic
 linux-image-generic
 linux-generic
 linux-headers-generic


Can this be corrected? Should I use old kernel only?
Thanks in advance.

---

### Post by baytuni on 2009-11-27
same issue still searching..

---

### Post by anishd on 2009-11-27
because of this problem, i uninstalled the new kernel and dependencies via synaptic. (First i tried to remove nvidia-common, and tried to run the command again. but was found of no use, thats why the new kernel was uninstalled). Now the problem disappeared.
But it is only a sort of escaping from the problem rather than taking it as a challenge and correcting it (time problem).

---

### Post by Ozzman on 2009-11-28
My system had a full system failure upon upgrading. would dump me to a flashing login prompt (outside of xserver)... trying to login resulted in many lost inputs making the password input impossible. Choosing the old kernal from grub fixed this issue right away... This must be resolved. since  2.6.31-14 now has a limited life spawn.

---

### Post by BioVirtual on 2009-11-29
> 
My system had a full system failure upon upgrading. would dump me to a flashing login prompt (outside of xserver)... 

This may be a driver issue. What is your Graphic card?

---

### Post by caliorangekb on 2009-12-05
> **Ozzman said:**
> My system had a full system failure upon upgrading. would dump me to a flashing login prompt (outside of xserver)... trying to login resulted in many lost inputs making the password input impossible. Choosing the old kernal from grub fixed this issue right away... This must be resolved. since  2.6.31-14 now has a limited life spawn.

I had the same problem.  Since there has been another update and even a new kernel release the problem for me has changed from Ozzman's a little. 

 Now 2.6.31-15 does not continuously flash making login impossible.  However, it still takes me to the login prompt and my desktop doesn't load. My network card apparently also doesn't work.  

In the latest kernel 2.6.31-16, I get to select to run the desktop in low-graphics mode and a message saying some nvidia modules failed to load.  When I tried to make a new graphics config, I was told to restart and when I did my desktop graphics failed to load leaving me with frozen "glitchy" graphics on my screen until I did a hard restart.

Since none of these updates have been functional for me I am still using 2.6.31-14-generic.  If it is possible for me to fix these issues, I would be grateful to anyone who has input.

THANKS!

---

### Post by Ozzman on 2009-12-13
> **caliorangekb said:**
> 
In the latest kernel 2.6.31-16, I get to select to run the desktop in low-graphics mode and a message saying some nvidia modules failed to load.  When I tried to make a new graphics config, I was told to restart and when I did my desktop graphics failed to load leaving me with frozen "glitchy" graphics on my screen until I did a hard restart.

Since none of these updates have been functional for me I am still using 2.6.31-14-generic.  If it is possible for me to fix these issues, I would be grateful to anyone who has input.

THANKS!

2.6.31-16 works for me, however I had to reinstall my Nvidia graphics drivers 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Nvidia should give you a .run file, download it somewhere you can access easily from terminal. 

load 2.6.31-16, once you get the low graphics options, choose dump to console.. Once in console log in and sudo run the .run drivers you downloaded from nvidia and follow the directions. It should uninstall the old ones and reinstall.

that fixed it for me and I'm now using -16 Kernal..


alternatively you might be able to use the Nvidia PPA 

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa) 

But you would have to figure out how to update the drivers from console on your own, as I found and added the Nvidia PPA after getting -16 to work.

---

### Post by caliorangekb on 2009-12-18
> **Ozzman said:**
> 2.6.31-16 works for me, however I had to reinstall my Nvidia graphics drivers 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Nvidia should give you a .run file, download it somewhere you can access easily from terminal. 

load 2.6.31-16, once you get the low graphics options, choose dump to console.. Once in console log in and sudo run the .run drivers you downloaded from nvidia and follow the directions. It should uninstall the old ones and reinstall.

that fixed it for me and I'm now using -16 Kernal..


Thank You!!!

I tried to open the -16 kernel to run in low graphics mode, however this time that option didn't come up... actually nothing came up but a black screen... So I restarted and ran recovery mode. I dropped to root shell prompt then I changed the runlevel to 3 with the command ```
telinit 3
``` and signed into my user account.  I then proceeded to bash the run file and restart... I am now running -16 kernel... about a month after it's release.

Oh well, better late than never. :P

---

### Post by nibirumarduk on 2009-12-18
anishd, the error message seems to indicate one of the package scripts (i.e. postinst) having an issue running a command, specifically that of configuring your nvidia driver.

I see that you have since uninstalled the new kernel and reverted to using an older one. I do have some questions:
1.) Are you using an nvidia driver or even X packages from a ppa repository? As to why I ask is because I have an nvidia card i.e. GeForce 8400 GS and I'm also on the 2.6.31-17 kernel. Although admittedly, I'm using the 190 driver for my nvidia card i.e. one not carried in the official karmic repos but on a ppa that I'm tracking.

2.)
a.
Your issue was with the 2.6.31-15 kernel. apt-cache policy linux-image informs that 2.6.31-17 is already karmic-proposed. Have you enabled the karmic-proposed in your sources.list? 
b.
If not, would you consider enabling it to upgrade to 2.6.31-17 and see if you still run into the same problem? For what it is worth, I'm running the 2.6.31-17 kernel and have been for a few days now without any glitches.

3.) Have you filed a bug report at launchpad?

I'm not sure if this is appropriate for you but I know for some users, they do keep at least one other kernel lying around for just such a contingency. You can consider following suit as well.

Also something you may want to consider the solutions outlined in this post [http://ubuntuforums.org/showthread.php?t=1357523](http://ubuntuforums.org/showthread.php?t=1357523), which are effective in bailing yourself out of most difficult upgrade situations for most normal packages but in the case of kernel upgrades, do exercise the utmost caution. But if you are desperate, my usual advice in such an instance would be to use Option 1 and to do so only if you desperately want to try out the kernel but is stuck with a botched upgrade due to some buggy package scripts e.g. the postinst script in your particular instance, in all likelihood, porbably thanks to some tired, sleepyhead or plain careless maintainer. But be warned, if you are to exercise Option 1, you may run into certain graphics and display issues later. Your 1st priority should always be to try the 2.6.31-17 kernel by enabling the karmic-proposed repo. You have been warned.

All the best!

---

