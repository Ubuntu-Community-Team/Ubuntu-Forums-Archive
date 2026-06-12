---
title: "How do I......?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by HP dv4 on 2010-10-10
I went to install Ubuntu from the live CD and when it asked me to choose the partition I quit the install. My question is do I have to create the new partition (I am going to dual-boot with Windows) before I do the install or is there someway of doing this from the install while not formatting my existing partitions? I just want to shrink the Windows partition a little and use that space to install Windows. I installed Ubuntu 9.10 way back when on an external drive (and have since deleted that install) and it allowed me to do whatever on creating the partitions and shifting them around.Did it only allow me to do that because it was just a giant flash drive?
Right now I'm just making due with a wubi install.

---

### Post by dino99 on 2010-10-11
i agree that installing the desktop iso is scary as you cant control the installation as you want. The easiest way is to prepare the partitions first with partedmagic for example: [http://partedmagic.com/](http://partedmagic.com/)

boot on partedmagic and prepare 3 partitions:
- / : a bootable root partition to install the system, ~ 12 gb ext4
- swap: about 2 gb
- /home: ext4 unlimited space for your data

take note of their name, you need it for installation (/dev/sdx, x is from a to z)

then make the installation with the "alternate" iso and choose manual installation to select the partitions

---

### Post by HP dv4 on 2010-10-11
If I just create one partition for Ubuntu from within Windows will the regular install iso split that up into the root, swap, etc.? If this is the case I could use my recovery partition. (though a little small and stupid to get rid of)

---

