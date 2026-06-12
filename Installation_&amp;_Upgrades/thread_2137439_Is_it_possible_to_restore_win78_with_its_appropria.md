---
title: "Is it possible to restore win7/8 with its appropriate drivers etc?"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by pavelexpertov on 2013-04-20
Hi, I know it's may be not about ubuntu, but i felt that I could not put the post anywhere else.
However, I was thinking about getting a gaming laptop so I can start playing serious games and create games, but since they are overpriced and extra-featured(3d, video graphics, sound graphics etc), I am a bit scared if I try to triple boot (if it's ever possible to do that!!!!!) on the laptop and it crashes and looses all imporatant software part. So, is it possible for windows to identify appropriate drivers for all them extra features as well as fundamental one?

---

### Post by grahammechanical on 2013-04-20
I am not sure I understand your question. I am more familiar with Ubuntu than with Windows. As we know in Linux drivers for the hardware are compiled into the kernel. That is, if drivers exist. As we also know sometimes drivers do not exist or we have to use proprietary drivers, if they exist.

I think that things are different in Windows. Because the OS comes pre-installed all the necessary drivers are put in and set up by the manufacturer. Would an off the shelf copy of Windows have all the necessary hardware drivers for all kinds of hardware. I very much doubt that. When building a computer to run Windows we have to make sure that the hardware is Windows certified. That means that a driver comes with the hardware.

I built my own computer five years ago. The motherboard came with Windows drivers and utilities that I never used because I did not install Windows. If you buy a laptop with Windows pre-installed, I do not think that you will get copies of all the drivers. This is why these machines have recovery partitions and utilities. But as I say I have no experience with Windows and like you I would be scared to try to dual or triple boot a machine with Windows 8 pre-installed.

Regards.

---

### Post by Mark Phelps on 2013-04-20
If you buy a laptop with all these features, it will have all the drivers already installed -- and if you make NO changes to the partitioning, it will also be able to restore itself to factory condition -- including all of the apps and drivers.

But ... if you make changes to the partitioning, to install another OS, or simply, to shrink the OS partition to create a shared data partition -- there is no guaranteed that the factory restore will work after that.  In fact, there's a good likelyhood that it will not.

So, for multiboot situations, what you need to do to have a restorable setup is the following:
1) Shrink the Win7/Win8 OS partition ONLY using the Windows Disk Management tool
2) Boot into Win7/Win8 a couple of times after that to allow the filesystem to make any adjustments needed
3) Download and install Macrium Reflect
4) Image off the boot and OS partitions to an external drive
5) USe the MR option to create and burn a Linux Boot CD
6) Connect the external drive containing the images, boot from the Linux Boot CD, start a Restore operation -- and confirm that you can see the saved images.  Do NOT do the actual restore -- this just confirms that you can see them later if needed.

NOW, you can install another OS in the unallocated space -- since you have the ability to restore Win7/Win8.

---

### Post by carolin3 on 2013-04-20
I think it would be possible , but the worst case scenario is that you would just have to install each driver manually. My friend had to do that when he switched from ubuntu to windows.

---

### Post by pavelexpertov on 2013-04-21
thank you guys for all ur supportive info,  I will keep them when I choose my laptop :D

---

