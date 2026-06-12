---
title: "Installed fine but was it supposed to happen the way it did?"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by sbooth on 2005-10-19
I am totally thrilled that I now have Breezy running perfectly (as far as I can tell having only had it running for a day!)...

Being rather new at the Linux thing I wondered whether anyone could answer some questions I've got now?  I have searched the forums for two evenings trying to find out if my questions have already been answered - without joy.

What I did to upgrade: I initially tried to upgrade from Hoary to Breezy using the command line apt-get dist-upgrade approach (followed instructions from the forum v carefully!) - my machine said it had something like 700 packages to download, I left it at it overnight and went back to it... then it presented me with a screen asking about language/location selection, I selected appropriately, hit return and landed up back at the command line.  Then did restart, Grub was unchanged and only gave me Hoary choices.  Didn't know what to do next, figured there must have been some problems and did a Synaptic smart upgrade... which told me there were about 550 more packages to download (which included some I thought had already downloaded)... so I watched it to do that (saw loads of errors flash past on the terminal window - which I had seen warnings about on the forum) - which seemed to work, got me a Breezy kernel option in Grub and it loaded fine.  (Subsequently reinstalled Nvidia driver without problem).

The questions: First, did something go wrong with my apt-get attempt at upgrade that meant it didn't finish - or is it normal for Synaptic to still have loads to download after apt-get is done?? (I thought they were essentially the same process - but I might be very very wrong!)

Is the fact that I have both OpenOffice and OpenOffice2 appearing in my Gnome menus (and both working, it seems) a result of having to do the upgrade 'twice'?  How do I get rid of the first OpenOffice (can't see the point of having two?)?

Finally - and possibly more complicated (?)... I run a dual Xeon machine (two 2.8 GHz, 512Mb RAM), currently have the 386 kernel and my husband (not quite so much a newbie as me but not a linux guru either) said I should run an SMP kernel to address both the processors?

If anyone can help with any of this I would really appreciate it - it's the forums that got me this far (and I'm jolly grateful to people for writing step-by-step instructions for newbies!)...

Many thanks in advance

---

### Post by Pablo_Escobar on 2005-10-19
1. Open Office was the default choice in Hoary, Open Office 2 Beta is default choice in Breezy - that is why You can have 2 sets of OO - just Synaptic remove the unwanted one.
2. About errors - dist-upgrade is bound to give You some error messages. If Your system works fine now, then You shouldn't bother to dig into the upgrade problems You've had :)
3. Kernel - dual processor - a SMP kernel must be. If it's Xeon - then You should pick SMP 686 kernel.

Good to see another happy Breezy user :)

---

### Post by sbooth on 2005-10-19
Thank you :-)
I won't worry about the error messages though... and when I'm back in front of my main machine I'll think about getting rid of the first OO.

Are there any warnings I should be aware of before I dive in to upgrading to an SMP kernel?

---

### Post by nocturn on 2005-10-19
I also did the upgrade (as I previously did from Warty).

In my experience, it is needed to do multiple dist-upgrades, until it says there are no more packages.

---

### Post by Pablo_Escobar on 2005-10-19
1. Install the SMP kernel
2. **DO NOT REMOVE THE OLD KERNEL**
3. After apt-geting the SMP Kernel - reboot
4. At boot menu choose SMP kernel
5. Play with Your system while running SMP Kernel and if everything is OK, You can think about removing the old kernel (it's not a must, but clears disk space).
6. In case of problems choose the old kernel at the boot menu.

---

### Post by sbooth on 2005-10-19
Fantastic :-)  686 SMP kernel installed, Nvidia drivers reinstalled for that kernel... and it boots beautifully.  Thank you :-)

---

