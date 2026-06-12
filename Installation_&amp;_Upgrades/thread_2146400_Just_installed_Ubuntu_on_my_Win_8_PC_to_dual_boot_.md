---
title: "Just installed Ubuntu on my Win 8 PC to dual boot but after install I get error!"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by LJA66 on 2013-05-18
Hi there,

I had a perfectly working Windows 8 pc installed on a 1TB HDD then downloaded latest Ubuntu. I burned it to a DVD, rebooted, chose to install alongside my Win 8 and was hoping to get the dual boot option after installation. But, all I got now is an almost blank screen with the following error message on it. Please can anyone help!!?? >>>>>>>>

error: no such device: 1bc1e107-0c1c-40f9-abcb-0ffb10c486d9
grub rescue>

---

### Post by oldfred on 2013-05-18
We need details. You can add this to your Ubuntu installer or download a full repairCD.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by LJA66 on 2013-05-18
Thanks very much for your reply but I'm sorry, I don't understand! What details do you require that I haven't already mentioned??

Btw, I am using another pc to write on here.

---

### Post by oldfred on 2013-05-18
Use the flash drive you used to install and boot in live mode.

Then install boot repair to the live mode and run the BootInfo report. It gives lots of detail.

Or you may just need to reinstall grub to the MBR which Boot-Repair will automatically do.

---

### Post by LJA66 on 2013-05-18
Thanks for your reply again.

I didn't use any flash drive. Like I put in my post, I created a DVD (using Ashampoo) from the .iso image downloaded from the main website.

You say to install bootrepair, but how do I do that? I am totally new to ubuntu!! Then you say I could reinstall something called grub!?? What is 'grub' and how on earth do you install that? So, what's the best thing you reckon I should try first?

Does it matter that I had one large HDD with Win8 on it and before trying to install ubuntu, I didn't create any partition for it? There was one problem I recall during the installation, and that was an option to create a swap space(?) but it gave me too many drives as options, so I didn't choose it. (I have an external usb drive attached that has about 3 partitions I think, although in Windows it only shows one large one).

Sorry for my ignorance but this is all totally new to me!

---

### Post by oldfred on 2013-05-18
Grub2 is the boot loader. Windows does not have a name for its boot loader.

Was this system with Windows 8 pre-installed? And what brand & model.

Instructions on installing Boot-Repair are in the linked site. You need to boot your DVD installer in live mode and open a terminal. See the step by step detailed instructions in the first link. 
 You can then just copy & paste each of the two commands one at a time and that installs boot repair.
Since it is a DVD it will not save & if you reboot you have to reinstall each time you reboot.

---

### Post by LJA66 on 2013-05-18
No, the pc did have Win7 on it, but I downloaded Win8 Pro and installed it myself. I am still confused at what you mean when you say I will have to reinstall this boot repair thing everytime I load ubuntu. Why would that be?

---

### Post by oldfred on 2013-05-18
If you download liveCD version you do not have to reinstall. But booting from the Ubuntu live DVD will not let your save it as it only is in RAM and cannot be written back to DVD.
If you use a flash drive and have persistence set then it may save it, but I have not tried that.

---

### Post by LJA66 on 2013-05-18
Thanks again for reply. 

I think you missed what I originally put...I have Win8 Pro and I used the DVD to actually install ubuntu permanently onto my pc to then run alongside my Win 8 already on there. I chose to keep my Win 8 and opted for a dual boot. But this didn't work and I don't know why!

---

### Post by oldfred on 2013-05-18
I do not know where to start on suggestions as there can be many reasons. If you run Boot-Repair and post the link to the BootInfo report we can see exactly where you are at and then suggest what to do.

---

### Post by LJA66 on 2013-05-18
I will have another look at reinstalling and see what happens. Thanks again!

---

