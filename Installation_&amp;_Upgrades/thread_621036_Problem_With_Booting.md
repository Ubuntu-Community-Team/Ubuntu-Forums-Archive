---
title: "Problem With Booting"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by R-World on 2007-11-23
Hi Every one,

I first started using Linux on my graduation Project on RedHat 8 and since then I haven't changed a thing.

I downloaded ubuntu 7.10 for my AMD Athlon 64-bit 3000+ with 1 GB or RAM. I have a 200GB HDD with 150GB NTFS for Windows XP and the rest is unpartitioned. When I booted the LiveCD and tried to install it every thing went smoothly. When The partitioning part came I choose manual and made 2 partitions on my free space with 40GB ext3 mounted at"/" and a SWAP with 2GB. The installation formatted them and continued copying and configuring  till the a success message appeared to me telling me to get the LiveCD out and rebooting my system to use Ubuntu from my HDD.

But when my system restarted Windows XP booted up without any GRUB boot Loader or GRUB starting or any kind of an OS selection method. ( Its like Ubuntu never existed on the HDD ! ).

I searched the Forum and the closest thing to my problem was This : 
[http://ubuntuforums.org/showthread.php?t=490973](http://ubuntuforums.org/showthread.php?t=490973)  

which takes you to This one
 [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But when I started the GRUB command from the terminal and typed :
grub> find /boot/grub/stage1

And error message appears saying " Error 15: File not found"

Now, My space is with no use and I can't use my Ubuntu.

thank you for your help.

---

### Post by dabl on 2007-11-23
Here's a lot of help with Grub issues:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)


:)

---

### Post by Drastix on 2007-11-23
Hi R-World,

I installed Ubuntu today from a CD included in a magazine and ran into the same problem as you.

I tried the same solution you found and also got the error in Grub> , It turns out I forgot to add the "sudo"-command when I started Grub. Problem was even after that procedure windows xp would still boot as if grub wasn't installed at all :(

I finally went into my bios and found out that my computer didn't boot from the first hard-drive but from the third. (don't ask me why i forgot it, this is a long running system :p ) 
Grub had planted itself on the first hard disk so I changed the boot-sequence so my pc would boot from the first drive and it worked.

I now have a grub-menu where I can choose Ubuntu or Windows :)

I hope this helps.

---

### Post by R-World on 2007-11-24
Thanks dabl, Drastix .

I'll try booting from my first HD and give you the result.

---

### Post by R-World on 2007-11-24
It worked.

I have 3 HDD in my System. 2x320GB and 1x200GB

The Windows and Ubuntu are both installed on my 200 GB HDD and it was the first one in boot. The Other 320 GB disk are data. But when I changed the boot order GRUB started normally.

Thank you for your help Drastix and dabl.

---

