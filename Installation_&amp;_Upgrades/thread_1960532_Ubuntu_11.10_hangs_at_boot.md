---
title: "Ubuntu 11.10 hangs at boot"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by garpin01 on 2012-04-17
Hey guys, I am not a heavy linux user, but I do appreciate what it can do and enjoy playing around with it from time to time. I have gotten a new computer and am attempting to boot Ubuntu 11.10 from a USB that has persitant memory. I know the Ubuntu image and the imaging of the USB are good because I can boot it on other PCs. To keep it simple, I have uploaded a youtube video of what happens.
 
[http://www.youtube.com/watch?v=NIWekJMtS1E&context=C452fd18ADvjVQa1PpcFNYJo3KGjYkMHkNoCU-NxKkkKgieWT40KU](http://www.youtube.com/watch?v=NIWekJMtS1E&context=C452fd18ADvjVQa1PpcFNYJo3KGjYkMHkNoCU-NxKkkKgieWT40KU)=
 
For those who can't see it, I get through grub as per norm. It begins running scripts then stops with no scrolling or command line entry possible.
 
My computer hardware follows:
 
AMD 8150 processor
Nvidia 570 graphics
OCZ Solid 3 SSD (OS HD)
Western Digital HD (storage HD)
Gigabyte GA-970A-D3 motherboard
 
I'm stumped. I've googled for about a week now, tried many supposed solutions, to no avail.

---

### Post by oldfred on 2012-04-17
Welcome to the forums.

With nVidia, you need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by garpin01 on 2012-04-17
[COLOR=black][FONT=Verdana]That's awesome! The "nomodeset" worked to get it booted. If I only ever want to boot from this USB, should I just install the drivers when it boots? Can I fix it permanantly that way if the USB has 4Gb of persitant memory?[/FONT][/COLOR]

---

### Post by oldfred on 2012-04-17
I do not know how it works with persistent installs. 

I have a full install in a 8GB / partition on my 16GB and added the nomodeset. That works with my Desktop with nVidia and seems ok on my older laptop with Intel's internal video.

I also have added nomodeset to my installers as I use grub2 to boot those. You may be able to add it to syslinux, but you normally cannot update the actual install and only save extra data into the persistent space.

---

### Post by efflandt on 2012-04-18
I don't know if there is a way to modify kernel boot parameters for a bootable install iso on USB (without modifying the iso file first) to include **nomodeset** as a default.  But I know that you cannot install video drivers on the iso already on USB because with the system initially boots from a fixed squashfs (compressed) file system before persistent data is mounted.

Persistent data will keep track of certain system settings (like timezone and wireless security settings) and can be used to add programs that run after booting, but cannot modify things that happen during initial boot (kernel version, video drivers, etc.).

I do find it strange that the same exact nvidia driver version can work in 10.10 without nomodeset, but 11.10 requires nomodeset (or I would get "no video signal" on my display).  Something changed in the boot sequence between Ubuntu 10 and 11 Ubuntu that default kernel mode setting (KMS) does not work with both nouveau and nvidia, but they work fine together as modules.

---

### Post by garpin01 on 2012-04-18
Understood. Can't modify the ISO to permanantly insert the correct drivers. Got it. Thanks guys!

---

