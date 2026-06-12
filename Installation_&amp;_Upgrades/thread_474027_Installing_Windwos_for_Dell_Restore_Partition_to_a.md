---
title: "Installing Windwos for Dell Restore Partition to a VM"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Jabran Asghar on 2007-06-14
Hello,

I have a dell partition (containing Windows XP Factory image for restore) on my laptop. I am using Feisty on this laptop, and want to install Windows XP in a virtual machine. My question is:

- How can I install windows from the Dell partition into, lets say, Virtual Box?
- Is there any way that I can, somehow, write the dell partition to a DVD, boot from the DVD in Virtual Box and install?

Just to be clear, my question is not about how to install an OS in VirtualBox/VMWare, but, how to boot from Dell Restore partition in a Virtual machine. I hope there will be a way to this.

Thanks for any pointers.

Jabran

Edit: Opps ... the title should be "Installing Windows from Dell Restore Partition to a VM" :oops:

---

### Post by lawr_rawr on 2007-06-14
You might not want to do this. I tried to do something similar with my Averatec recovery partition, to create a clean XP install under VMware. I was able to create a recovery DVD from my recovery partition and boot the DVD from a virtual machine. It installed successfully, but didn't work after that. Since my recovery partition contained not only XP but drivers and configuration specific to the laptop's hardware. the resulting virtual machine would not boot. It would bluescreen immediately with an "unmountable boot device" error, presumably because it was using the SATA drivers from the image rather than VMware disk drive drivers. 

I ended up using VMware converter to create a virtual machine from my XP install... I dual boot, so this might not be an option for you unless you still have a working copy of XP. 

Our office PCs are Dells, and if your computer is under warranty, they'll (usually) send you a recovery disc for a nominal shipping fee. That disc is an ordinary Windows install disc, so you should be able to install it under VMware. (no idea if this applies to home PCs or just corporate)

---

