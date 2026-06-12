---
title: "Can't boot 8.04 Live CD - Graphics Scrambled"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by RTucker on 2008-05-15
Hi,

I cant get the Live CD of Hardy 8.04 to boot.I get as far as the end of the Ubuntu loading screen, were it should start loading gnome, etc. and the screen goes to a scrambled pixel pattern.

7.04 and 7.10 worked fine.

The system is:
P4 530 (3GHz)
1GB DDR RAM
Geforce 6600GT PCIe
Gigabyte 915P based MB

Any help will be grealy appriciated.

Thanks.

PS. I have tried "vga=771"

---

### Post by Pumalite on 2008-05-15
Try the Alternate CD. If it doesn't work; I'll give you some boot parameters to try.

---

### Post by Pumalite on 2008-05-15
Did you try 'Safe Graphics Mode'?.

---

### Post by RTucker on 2008-05-16
Thanks heaps for the qiuck reply, as always this forum is awesome. Unfortunatley I dont have access to this PC until tonight. I really need a live CD at the moment so the alternate CD is not really a solution. I think I did try safe mode and had the same problem, but I'm not 100% sure (so many CDs/Distros). I'll try it again and let you know.
 
Also, if its any help I had this same problem with Linux Mint, but it worked in safe graphics mode.
 
And idea why this would have become a problem since 7.10?

---

### Post by PryGuy on 2008-05-16
That's very strange, 'cause I haven't had any problems with nVidia cards in Ubuntu. One of my PCs has 6600 and it works just fine! Have you tried 'vesa'?

---

### Post by RTucker on 2008-05-16
Ok,

In safe graphics mode it does get to the desk top but it takes a LONG time (several minutes). And when it does get to the desktop the first thing to come up is a dialog box which says:

> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
Should I expect the same problems from an installed version? It seems strange that there are problems with this very common and usually very well supported hardware. What is VESA?

---

### Post by PryGuy on 2008-05-17
Hmmm, it usually happens when you've got not enough memory, that is below 512Mb and no swap partition that installer could handle. VESA is a safe graphic card driver that is in almost all BIOSes and allows you to boot up to an OS with very basic functions. Are you sure you don't want to try installing Ubuntu with alternative installer?

---

### Post by RTucker on 2008-05-17
Ok, so does that mean that the live cd actually does write to the HDD? (for a swap partition something?) Because if so a severe lack of HDD space might explain it, the system has a 160GB HDD in 2 partitions with the freespace measured in MB not GB...
 
When it comes down to it I'm fine with the alternate installer, but I dont want to put ubuntu on this system at the moment, just mess around with a live CD. I need to get a new HDD and transfer all that DATA first :)

---

### Post by PryGuy on 2008-05-18
No, look, it doesn't touch your EXT3 or NTFS partitions, it just checks if there is a swap partition and mounts it if there's one. Yes, it does write on the swap partition. I had this sutuation a couple of times on PCs with low memory (>512Mb). Solved the problem adding a swap partition with [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php"). You've got enough memory even for Vista so I'm really confused here... :confused:

---

