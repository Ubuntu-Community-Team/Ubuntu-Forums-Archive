---
title: "Mounting root filesystem hang (the help threads haven't worked/applied)"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by rmarsch on 2006-11-06
Hi, I'm trying to install the 6.06.1-desktop-amd64 version of ubuntu. I have not used Linux before, and this was recommended to me as the best one to use. I mounted the image on a cd, and then I rebooted in an attempt to install Ubuntu. When I run the install, it will always freeze at Mounting root filesystem. When this happens, the progress bar under the Ubuntu logo stays stuck a smidge past the beginning. Also, every time my computer's cd drive will make noise as if trying to read/write, it tries this twice, then it rests before spinning the cd indefinately. I've tried a number of suggested workarounds via the help documents: debian-installer/frambuffer=false, debian-installer/probe/usb=false , hw-detect/start_pcmia=false, noapic, nolapic, defining my 512mb of ram mem=512m, acpi=false. These either bring me to the same hang at mounting the root filesystem or create a kernel panic. 
   I've tried priority=medium/low and this has revealed some interesting information. The prompt returns a line saying that the mount could not be placed on unknown_batch or something to that effect. A similar error has been returned saying that the drive it is trying to mount is "NULL". I'm guessing this is similar to if not an example of a Null pointer exception, but it is curious why exactly Ubuntu has determined the drive to mount is NULL/unititialized. 
I ought to explain my disk setup up, in case there is some manipulation I have to do to get it to recognize the proper disk. Right now I'm running Windows XP-64 Professional, and it has my disk drives ordered as such: The main local HDD is c: and it contains my OS and is the one I want to install Ubuntu on, my external HDD connected via firewire is D: (I've tried installing Ubuntu both with it connect and disconnected from the computer), the cd/dvd-rom drive is E: and is where Ubuntu is being installed from via the image I burned onto a cd.
If anyone has insight into how I can get the installation to mount to the correct HDD (c: the local disk) I'd greatly appreciate the help.

---

### Post by DaveBorealis on 2006-11-06
Hello,

I wouldn't think that the hard drives would matter during the bootup process of a live CD.  They are not used...at least not until you format the partitions and mount them for the actual install.

From your post I didn't see that you had tried the 32-bit AMD CD...why don't you see if that'll boot for you.  If it does, install it so you at least have a working system, then you can get the 64-bit AMD live CD working at your leisure!

Best regards,
Dave

---

