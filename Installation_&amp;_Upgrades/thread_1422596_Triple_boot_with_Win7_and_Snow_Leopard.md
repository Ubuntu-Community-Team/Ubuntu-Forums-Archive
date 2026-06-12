---
title: "Triple boot with Win7 and Snow Leopard"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2010-03-05
O.K. Here's my setup. 3 separate hard drives. 
80gig=win7
wd 500gig=Ubuntu 9.10
seagate 500 gig=OS X 10.6.2 Snow Leopard.

My goal is to triple boot, from grub. 


All three drives are loaded with there own OS, and are working fine.
I Can boot into the mac drive, and dual boot with windows 7 but it doesn't show Ubuntu
I haven't tried adding Snow Leopard to grub yet. Question is, can I? And is it just a matter of updating grub? I booted to the Ubuntu drive and only saw ubuntu and win7 in grub.

Getting Snow Leopard on the pc was no easy task in itsef! hahaha! But I did it.

Any help is greatly appreciated! Thanks,
Smitty

---

### Post by immerohnegott on 2010-03-05
Well in my experience, I've been able to get Leopard into GRUB by adding the following to menu.lst in legacy GRUB:

title *whatever you wanna call it*
root (hd*mac disk*,*mac partition*)
makeactive
chainloader +1

basically the same entry for Windows, with the right partition. Depending on how you partitioned your OSx86 disk, it may give you an error about HFS+, which may be fixable by running fdisk in linux and setting the OS X partition type to af as mentioned [here]("http://wiki.osx86project.org/wiki/index.php/Talk:Install_On_A_Partition_Simple_And_Accurate#Grub_HFS.2B_Error").

Good luck

---

### Post by immerohnegott on 2010-03-05
Crap. Forgot to add, if you're using the new GRUB, there's a config file in /etc/grub.d/ called 40_custom. Syntax is pretty similar, and can be found in the User Defined Entries section of [this page.]("https://wiki.ubuntu.com/Grub2")

---

### Post by bigsmitty64 on 2010-03-05
Thanks  ! I'll give that a go, and the "CRAP" is ditto here, I am using new grub and forgot to say that  :)

---

### Post by oldfred on 2010-03-05
Do not know about OSx. You can chainboot to a partition if a boot loader is in the partition. Windows has a real simple boot loader in the MBR that just jumps to the PBR so grub does the same thing. If using grub legacy that can be installed in a partition to chainboot to for systems using grub. 
You also can chainboot to the MBR.

Grub2 with chainboot examples
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

Partition:
menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1\
}

MBR:
menuentry "Chainload Other System on sdc" {
set root=(hd2)
chainloader +1
}

---

