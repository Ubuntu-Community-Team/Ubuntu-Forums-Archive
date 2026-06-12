---
title: "Reverse wubi?"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by frash23 on 2013-02-21
Alright, so i have my laptop wich i only have ubuntu on.
I want to install windows on it, but still keeping my ubuntu system, like a dual boot with the wubi installer.

I don't know much about partitioning, and all the articles i found on the internet was doing it form windows, not ubuntu.

How can i create a windows dual-boot from inside of ubuntu?

---

### Post by fdrake on 2013-02-21
> **frash23 said:**
> 
How can i create a windows dual-boot from inside of ubuntu?
I do not think that there is a way to do that.
The reason being is that windows does not support installation in formats outside FAT and NTFS. (You can install an ubuntu partition on a FAT/NTFS by you will have serius security issues, since this systems do not unix- like systems.) 

 I also think that that would be dangerous for your system too, since ubuntu will have to give windows access to its filesystem. 
You can install vmware, or virtualbox and install windows in it.

---

### Post by frash23 on 2013-02-21
> **fdrake said:**
> I do not think that there is a way to do that. I also think that that would be dangerous for your system too, since ubuntu will have to give windows access to its filesystem. 
You can install vmware, or virtualbox and install windows in it.

I didn't directly mean hosting it inside of the system, just how to do the partitioning and how i would choose the different OS's on startup.

---

### Post by JiuJitsu500 on 2013-02-21
Like fdrake said, that would be more dangerous than it would do any good.

A vitrual machine would be the way to go and you can share files like that as well but ti doesn't give windows full access (which if you caught a virus that erased the entire filesystem would also screw up ubuntu... you get the idea).

Or, partition your drive, install windows on it, and re-install GRUB because the win bootloader is stingy and self-centered.

---

### Post by frash23 on 2013-02-21
> **JiuJitsu500 said:**
> 
Or, partition your drive, install windows on it, and re-install GRUB because the win bootloader is stingy and self-centered.

This is what i wanted.

I amhaving issues with my internet, while it works perfectly on my 5 other windows computers.

---

### Post by JiuJitsu500 on 2013-02-21
I posted like 5 seconds after you did I guess...

Well, boot from a live USB or DVD, partition the drive so Windows has as much room as you want it to, then install windows to that drive by your pefferred means, then boot back into a live environment and install GRUB (which is actually very easy to do).

Alternately you can follow some guides to make the windows bootloader 'see' ubuntu, but I don't like that too much. GRUB chainloads, which to some is "worse" but no one I have ever know has had a legit problem with that.

---

### Post by fdrake on 2013-02-21
some links that may help you.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

before doing the ubuntu installation I'd unistall Wubi. So that you clear the grub menu for the new installation.

---

### Post by frash23 on 2013-02-21
> **JiuJitsu500 said:**
> I posted like 5 seconds after you did I guess...

Well, boot from a live USB or DVD, partition the drive so Windows has as much room as you want it to, then install windows to that drive by your pefferred means, then boot back into a live environment and install GRUB (which is actually very easy to do).

Alternately you can follow some guides to make the windows bootloader 'see' ubuntu, but I don't like that too much. GRUB chainloads, which to some is "worse" but no one I have ever know has had a legit problem with that.

Alright, i know a bit about grub.

Thanks a lot!

---

