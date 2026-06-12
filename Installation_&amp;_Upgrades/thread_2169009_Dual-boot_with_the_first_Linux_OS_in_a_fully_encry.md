---
title: "Dual-boot with the first Linux OS in a fully encrypted partition"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by Vladlenin5000 on 2013-08-20
Consider the scenario mentioned in the thread's title, i.e:
1. The computer has a Linux OS already installed in a fully encrypted partition/drive;
2. There's free space available in the same drive or in a secondary drive - it shouldn't matter I guess - therefore no need to change the partitions already used by the fully encrypted OS;
3. GRUB or any other must "see" the OS already installed in order to add it to its boot options.

The problem is that unless there's a way to "open" the encrypted drive during the second OS installation the grub can't be updated to reflect those changes. As such, here's my question: **How is it possible to dual-boot in such scenario (the secondary OS would be also a Linux)? Is there a way to avoid a bootloader installation in the second installation and if so how? Should the GRUB be updated from within the first OS and if so the second one mustn't be encrypted? Ideas, please...**

---

### Post by Megaptera on 2013-08-20
You can have a 'hidden' o/s using Truecrypt and Windows [http://www.truecrypt.org/docs/hidden-operating-system](http://www.truecrypt.org/docs/hidden-operating-system) but not Linux with Truecrypt as far as I know -  so I'll be following this thread to see if others know the answer.
I've no state secrets to hide (in case anyone's bothered) ... just interested in the concept.

I suppose hiding a netbook under the floorboards isn't the answer?!

---

### Post by Vladlenin5000 on 2013-08-20
Actually the proof-of-concept of the proposed scenario considers an Ubuntu 13.04 installed first with the option of full drive encryption therefore nothing to do with Truecrypt. Again, the intended dual-boot is for two Linux system, being the first installed using the aforementioned option.

---

### Post by sioxs on 2013-08-20
Some food for thought....
I've recently setup such a scenario and discovered a few do's and don'ts along the way.
Once an encrypted drive is setup you cannot modify the MBR or partitions outside the OS that installed the encryption.
Changes to update-grub on secondary OS's should reside on the root partition not the MBR
Which implies updating grub on the main OS which is in the MBR initiated AFTER kernel updating a secondary system to reflect the changes to the boot loader.
In other words, partition & MBR changes should ONLY be done from the OS that encrypts it. 
Optionally It is possible to make a hard-link to the main OS's /boot directory (insecure as it needs to be mounted & decrypted) or by creating a mount point for your secondary OS's in fstab (still insecure) or by first creating a separate boot partition say between 250 - 500 Mb which can be unmounted once the selected system is up and running (better solution)

As your post states your first Linux box is on a "separately" encrypted drive, therefore anything that happens outside of that partition is totally discretionary. 
If you intend on installing another Linux OS on a partition outside of the encryption whether you encrypt it or not, without mounting your primary encrypted box (which you could do BTW, but defeats the purpose of securing that data) it will not be seen by grub by the new OS(s).  

In a nutshell here's what could be possible:
Upon booting your prompted for the password to decrypt the entire drive (all partitions)
successfully mounting advances to the grub menu (of the main OS) which includes all detected OS's and kernels
As noted above this situation works best if the boot loader is on a separate small partition at the beginning of the drive (eg: sda1)
With this setup implementation of LVM is a good idea to better manage partition space.

Convenience comes at a price, but a little extra work can go a long way in avoiding catastrophes. 
If there are other solutions or workarounds I'm all ears.
Peace
sioxs

---

### Post by Vladlenin5000 on 2013-08-21
Thanks a lot ;)

Most of the do's and don'ts and limitations I could figure out theoretically and that's why I asked for ideas and just in time the proof-of-concept suddenly becomes too real. Now I have to have - boss says so - RHEL 6 (desktop) fully encrypted and no messing around da internet :rolleyes: therefore I'll have to had personal Ubuntu later.

---

