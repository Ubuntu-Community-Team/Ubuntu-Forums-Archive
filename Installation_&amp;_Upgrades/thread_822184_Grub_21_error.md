---
title: "Grub 21 error"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Beware_Of_Pickles on 2008-06-08
Hi,

I wanted to install Ubuntu 8.04 on my external hard drive which worked perfectly well. But after the install something happened and I keep getting Grub 21 error every time I turn on my computer. On my internal hard drive i have windows vista and ubunut 8.04 installed. And I usually had the Grub screen appear where I got to choose which OS to load. 

I found a lot of documentation over the internet for the problem but b/c of my lack of knowledge I keep getting lost. I'm very new to Ubuntu and would appreciate the help. 

Thanks

---

### Post by PmDematagoda on 2008-06-08
Download the Super GRUB disc from [here]("http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/supergrubdisk_0.9677.iso"). Burn it onto a CD and then boot the PC with it, you should then be able to try and restore GRUB.

---

### Post by Beware_Of_Pickles on 2008-06-08
Hi,

I did download the supergrub disk but was not able to do it. I did load ubuntu with live cd then used partition editor to make my ubuntu partition a booting one. This brought back the grub menu. 

I guess after i installed the external it made the external the boot partition.

Thanks for the help though :)

---

### Post by adrian15 on 2008-06-10
> **Beware_Of_Pickles said:**
> Hi,
I did download the supergrub disk but was not able to do it.

Do you mean to convert it into a bootable cdrom?
Here the are the instructions: [How to make an SGD cdrom](http://www.supergrubdisk.org/wiki/SGD_Howto_make)
> **Beware_Of_Pickles said:**
> 
 I did load ubuntu with live cd then used partition editor to make my ubuntu partition a booting one. This brought back the grub menu. 

That's interesting. It does not make sense to me. The grub menu was back because your external hard disk was plugged in... isn't it?

In my opinnion activating an internal partition as active should not modify internal's grub to avoid the second hard disk's grub seek.

Can you please write more details about the steps that you actually made?

> **Beware_Of_Pickles said:**
> 
I guess after i installed the external it made the external the boot partition.

It made point internal hard disk grub to external hard disk grub.

> **Beware_Of_Pickles said:**
> 
Thanks for the help though :)

Usually I recommend to check:
[I have Linux installed on a second hard disk. When I remove it I cannot boot my Windows. (Super Grub Disk wiki page.)](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDisk)

However if you never managed to boot your Ubuntu installation your problem might be: [I install Linux in a external hard disk but even with it plugged it does not boot. (Super Grub Disk wiki page.)](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDiskNotBooting).

Waiting for the details.

adrian15

---

