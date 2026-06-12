---
title: "Install in existing partitions - dual-boot"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Dusenberg on 2007-10-29
Hi

I'm wanting to install Ubuntu desktop on my Vista laptop in place of Fedora7 that's already there.  I therefore have all the partitions created - just need to reformat them.  Can anyone tell me how I tell Ubuntu installer which partitions to use for what?  Also how to I make sure Grub is installed in the /boot partion and not in MBR?  I have searched the forums and can't find anything definitive about the install process.  Anyone? :?

---

### Post by ThrobbingBrain66 on 2007-10-29
During the install process, you can pick the partitions you want Ubuntu to install to during the partitioning section of the install process (choose the manual partition option).

You can also select where GRUB is installed, but I don't remember which section it's located in.  It might be the Overview section right before you click the Install button.

---

### Post by Dusenberg on 2007-10-29
> **ThrobbingBrain66 said:**
> During the install process, you can pick the partitions you want Ubuntu to install to during the partitioning section of the install process (choose the manual partition option).

You can also select where GRUB is installed, but I don't remember which section it's located in.  It might be the Overview section right before you click the Install button.

Thanks for prompt reply ThrobbingBrain66. Sounds similar to the Fedora install process.  I'll give it a go.. fingers crossed!

---

### Post by Dusenberg on 2007-10-30
> **Dusenberg said:**
> Thanks for prompt reply ThrobbingBrain66. Sounds similar to the Fedora install process.  I'll give it a go.. fingers crossed!

OK - I'm at step 7 of 7 on the graphical install and if I click Advanced button I get small window that asks if I want to install boot loader and the 'device for boot loader installation'. Its defaulted to Yes (install) and location of hd(0).  According to the step 7 displayed info, my linux boot partition is: partition#3 of SCSI1 (0,0,0) sda. Is my boot partition therefore hd(0,3) - I don't know how to find out and don't want to proceed until I have a definite?

If I choose to install grub in hd(0,3) say then will the install NOT touch my existing Vista MBR?  - I've read some bug reports and threads that suggest it still writes over the MBR - but I don't know which version this referrred to!

Any guidance on what to do at this critical step? :confused:

---

### Post by ThrobbingBrain66 on 2007-10-30
Use this as your guide:

partition #1 = hd(0,0)
partition #2 = hd(0,1)
partition #3 = hd(0,2)

Partitions are numbered starting at one, but their location on the hard disk starts numbering at zero.

So as I'm sure you know/can figure out, the above example shows three partitions (0,1,2) on the first hard disk (0).

EDIT: Which bug reports are you referring to?

---

### Post by Dusenberg on 2007-10-30
> **ThrobbingBrain66 said:**
> Use this as your guide:

partition #1 = hd(0,0)
partition #2 = hd(0,1)
partition #3 = hd(0,2)

Partitions are numbered starting at one, but their location on the hard disk starts numbering at zero.

So as I'm sure you know/can figure out, the above example shows three partitions (0,1,2) on the first hard disk (0).

EDIT: Which bug reports are you referring to?

Thanks for info ThrobbingBrain66 :). I go with hd0,2.

This is one bug report I saw after googling. [https://bugs.launchpad.net/ubuntu/+bug/97174](https://bugs.launchpad.net/ubuntu/+bug/97174). 

Do you know if specifying hd(0,2) in step 7 will prevent Vista MBR from being touched??

---

### Post by ThrobbingBrain66 on 2007-10-30
The bug is shown as having a fix released.  It was filed during Feisty development, so I can't see this being an issue anymore.

I don't know if you were planning on installing 7.04 or 7.10, but if you want more insurance, go with 7.10

---

### Post by Dusenberg on 2007-10-30
> **ThrobbingBrain66 said:**
> The bug is shown as having a fix released.  It was filed during Feisty development, so I can't see this being an issue anymore.

I don't know if you were planning on installing 7.04 or 7.10, but if you want more insurance, go with 7.10

Thanks ThrobbingBrain66.  I think I've got 7.10 - I didn't check the ver when I downloaded - thats what it says in 'About' in the install desktop.

Crossed my fingers and pressed the button...... :o

33% done.......... oh dear.... I'm going for a walk!

---

### Post by Dusenberg on 2007-10-30
DONE IT! Ubuntu installed and running AND so is Vista.... Thanks for your help ThrobbingBrain66 ):P.

Now to check it out and make sure everythings working......

---

