---
title: "Chaning location of bootloader menu.lst"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by derrick1985 on 2005-05-09
ok, here is my situaion:

I have Ubuntu installed on one partition, and Kubuntu on the other. I want to get rid of Kubuntu, BUT, my grub menu.lst loads from there, so if I format, i'm afraid I will loose the ability to boot into Ubuntu or Windows.

How can I sucessfully get rid of the partition and still keep my current settings?!?!?!

---

### Post by spd106 on 2005-05-09
You might want to look at 
[http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows](http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows)

this has some similarities to your problem.

It might be useful to post your /boot/grub/menu.lst and /etc/fstab here so we can see how complex the problem is.
 
Your computer's bios should be setup to boot from a particular drive. Grub is installed in the mbr of this drive. So if you make no changes to the boot sector of the drive it shouldn't overwrite grub, and all you would have to do is delete the entry for kubuntu and probably change the default to Ubuntu. It might not be this straightforward if you have multiple drives, or lot's of different partitions.

Hope this helps

---

### Post by derrick1985 on 2005-05-09
[QUOTE=spd106]You might want to look at 
[http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows](http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows)

this has some similarities to your problem.

It might be useful to post your /boot/grub/menu.lst and /etc/fstab here so we can see how complex the problem is.
 
Your computer's bios should be setup to boot from a particular drive. Grub is installed in the mbr of this drive. So if you make no changes to the boot sector of the drive it shouldn't overwrite grub, and all you would have to do is delete the entry for kubuntu and probably change the default to Ubuntu. It might not be this straightforward if you have multiple drives, or lot's of different partitions.

Hope this helps[/QUOTE]

That link worked perfectly, thanks.

---

