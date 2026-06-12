---
title: "Kernel Compilation and booting woes"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by santosh_koshy on 2010-04-21
I tried compiling and installing Linux 2.6.24 into Ubuntu 9.10. The compilation completed successfully but during boot time, I get the follwing error. 

Warning: Unable to find a suitable fs in /proc/mounts, is it mounted? 
Use --subdomainfs to overide. 
General error mounting filesystems.
A maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
Give root password for maintenance
(or type Control-D to continue):

If I enter the root password, it opens an read only filesystem which does not accept any operations. 

Any ideas???

---

### Post by jpaugh64 on 2010-04-21
Okay, this is a complete guess, based on hazy memory of what I've read and little that I have done, but:

I'm guessing that the kernel is not able to find your root hard drive to mount it.
I am also guessing that the read-only filesystem is an initrd.img, which the kernel always mounts as the root fs before mounting the "real" root filesystem.

To confirm the latter, check for your favorite game program in /usr/games/. (If the games folder even exists, then I am *pretty* sure that I am wrong.) 
~
If I am right about all of the above, then it would seem that there is an error in your grub configuration. And, since grub has been updated since I've messed with it, that is as far as I can help you, or rather, *hint* to you.

I hope that is enough to get you pointed in the right direction, but do not trust anything that I have said thus far.
~~
One thing that I can say, under only my usual disclaimer, below, is this:
Try to boot using the old kernel entry from Grub's boot-time list of operating systems.
(You may have to press 'ESC' to access it, as Grub would warn you.) If that does work, that would be useful information for those helping you here. Also try the "recovery-mode" option, for the kernel that isn't working. It may give you extra clues.

---

### Post by santosh_koshy on 2010-04-21
The kernel is not in the initrd. There are games present in /usr/games. lsmod does not load all modules. Moreover, If i change the grub entry to rw at boot time, it creates a read write filesystem. The issue though is that proc is not able to properly mount the root filesystem and the required drivers dont get loaded. 

Clueless as of now...Any ideas???

---

### Post by ibuclaw on 2010-04-21
> **santosh_koshy said:**
> The kernel is not in the initrd. There are games present in /usr/games. lsmod does not load all modules. Moreover, If i change the grub entry to rw at boot time, it creates a read write filesystem. The issue though is that proc is not able to properly mount the root filesystem and the required drivers dont get loaded. 

Clueless as of now...Any ideas???

What filesystem is / ?

Is the module for it built into the kernel?

---

### Post by santosh_koshy on 2010-04-21
The fs is ext3 though, I have compiled support for all file systems within the kernel. ext2,ext3 and ext4 (ext4 is experimental in older versions of the kernel)

IS this problem something related to the proc fs?

---

### Post by ibuclaw on 2010-04-21
> **santosh_koshy said:**
> The fs is ext3 though, I have compiled support for all file systems within the kernel. ext2,ext3 and ext4 (ext4 is experimental in older versions of the kernel)

IS this problem something related to the proc fs?

Actually, having a think about it, might be an initrd problem - or the lack of one there.
Or perhaps the AppArmor patches are not compiled into the kernel.

How did you compile/install the kernel?

---

### Post by santosh_koshy on 2010-04-22
I have the initrd done and executing, Infact, i was able to crate a break during boot into the initramfs and perform the mounting of the filesystem. 

Now, regarding Apparmor, I am a bit confused. I read in forums that apparmor requires to be patched. But does Apparmor have anything to do with mounting the filesystem?? Apparmor is not compiled in my version since I took a vanila version 2.6.23 from kernel.org which does not contain the apparmor patch. 

Is Apparmor the problem?

Regds

---

### Post by ibuclaw on 2010-04-22
> **santosh_koshy said:**
> I have the initrd done and executing, Infact, i was able to crate a break during boot into the initramfs and perform the mounting of the filesystem. 

Now, regarding Apparmor, I am a bit confused. I read in forums that apparmor requires to be patched. But does Apparmor have anything to do with mounting the filesystem?? Apparmor is not compiled in my version since I took a vanila version 2.6.23 from kernel.org which does not contain the apparmor patch. 

Is Apparmor the problem?

Regds

Due to close ties between kernel/userspace, Apparmor can be a bit of a fickle if it tries to run without patches in place.  I've seen it happen in the past. But can't account it for happening to me.

I assume you can chroot into the filesystem OK from a LiveCD/Other?
Try that and remove apparmor / re-create the ramdisk.

(If you need specific steps, just ask).

---

### Post by santosh_koshy on 2010-04-22
Are you suggesting that I disable apparmor from my root filesystem?? WIll this sort the problem??

---

