---
title: "Unable to install packages-Ubuntu tries to mess up my boot manager!"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by santi_ on 2010-04-22
I cannot get package installer, either Synaptic, Ubuntu Center, sodo aptitude install or plain double clicking on .deb files I have already downloaded on my PC to work.

I get this:

 dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

When I do(even after a clear)
sudo dpkg --configure -a

, Ubuntu goes and tries to mess up with my boot configuration. wtf does installing a package have to do with messing up my lilo? I get this regardless of how I  try to install the package and it makes no sense(ok, If I do this graphically, I get the same errors from a widget window)

Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
ERROR lilo fails for new /boot/initrd.img-2.6.31-19-generic:

Warning: LBA32 addressing assumed
Warning: /dev/sdd3 is not on the first disk
Added Karmic9.10
Added vmlinuzSlack13
Added LinuxOLD
Fatal: Default image doesn't exist.
dpkg: subprocess instal failed


Any idea what is wrong here? I have no clue what business Ubuntu has trying to mess up with all the other distros I can boot.

---

### Post by Dayofswords on 2010-04-22
your using LILO?

that really out of date 
"Stable release 	22.8 / February 19, 2007; 3 years ago"

idk if ubuntu can even use it, why cant you use grub?

---

### Post by santi_ on 2010-04-22
Yes, I have another 4 linux distros on my PC, including Slack which is my favorite.
Why should a package installer care or try to mess up with my boot loader????

---

