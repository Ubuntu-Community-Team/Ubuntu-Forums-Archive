---
title: "Have &quot;lost&quot; Ubuntu boot-up menu!"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2013-08-18
Hello,

I had a dual-boot Ubuntu 12.04 / Windows XP system. XP became corrupted so I decided to install it again.

Now, when I boot-up the machine, I no longer get the Ubuntu menu.  I can only login to XP.

I did not delete the Ubuntu partition so 12.04 is still there.

How can I get the Ubuntu menu back on start-up so that I can select whether I want to load Ubuntu or XP?

Thanks.

---

### Post by oldfred on 2013-08-18
You need to reinstall grub2's boot loader to the MBR of your hard drive.

How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by Bobby_James on 2013-08-19
I followed the first link which eventually led to ([http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)).

This returned my GRUB menu and worked perfectly.

Thanks!

---

