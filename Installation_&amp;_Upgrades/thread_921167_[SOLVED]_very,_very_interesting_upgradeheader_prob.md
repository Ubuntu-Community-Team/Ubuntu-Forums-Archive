---
title: "[SOLVED] very, very interesting upgrade/header problem..."
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by novus721 on 2008-09-16
so this is different...

[due to a virtual machine problem I have]("http://ubuntuforums.org/showthread.php?p=5796731#post5796731"), I have tried to update my header set.

Now, even though I have the packages and everything required for the newest headers (confirmed by synaptic), my system will only boot to 2.6.22-14-generic, and will not boot into ANY of my 2.6.24-16/18/19 header sets. 

My grub claims that I am booting into 7.10 with the aforementioned .22 header set, which "uname -r" confirms as true.

However, "lsb_release -a" confirms that I am running on hardy (8.04.1)

I have tried to update my grub list to include the .24 header sets, but every time I go to load it I end up with this error
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) Enter 'help' for list of built in commands (initramfs)
``` and it waits for me to enter a command. I also used "update-grub" to be sure it recognized the other headers.

I can not describe at all how confused I am :-D:-D:-D
I have the packages, why won't it install the upgrade? Update Manager says all is updated as well...

I *really* could use some help, as otherwise I will have to dual-boot into xp for awhile and that is just a situation I 
would love to avoid entirely :)

UPDATED - Solved, check linked thread for solution.

---

