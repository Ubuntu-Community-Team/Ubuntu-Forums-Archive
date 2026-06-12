---
title: "Uninstall Ubuntu"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by ade_1 on 2007-01-19
Hi, after some problems getting my wireless installed I have decided to uninstall Ubuntu for the moment. However I do plan to try again within the future. 

What I was wondering was, how do I go about uninstalling Ubuntu rather than just deleting the partition as last time I did that I had problem with the Boot Loader (I forgot the name of it now).

I am currently dual booting with Win XP. The dual boot screen I get is the one associated with Ubuntu, not a dual boot of Win XP or whatever. I hope I make sense!

Sorry if this is in the wrong area.

Thanks in advance

Aidan L

---

### Post by tribeone on 2007-01-19
I am in the same boat as you, can anyone help us out? There is all sorts of info on installing but nothing on uninstalling.

---

### Post by hal10000 on 2007-01-19
Delete the ubuntu partitions and restore your mbr with your windows cd (fixboot and fixmbr commands)

---

### Post by javaJake on 2007-02-14
...or you could reinstall Windows, and Windows'll just wipe out Ubuntu. Ka-bam.

---

### Post by Dylnuge on 2007-02-14
> **javaJake said:**
> ...or you could reinstall Windows, and Windows'll just wipe out Ubuntu. Ka-bam.

I somehow doubt that that is the best solution for this scenario.

The way I see it, there are two solutions that would permanently fix the problem:

1. If your Windows XP disk is non-OEM (if you did not receive it with your computer), you can boot with it and use the /fixmbr command to restore everything to the way Windows likes it. Once you are done with this, delete your Linux partitions and make your Windows partition big again. (I recommend this order, since deleting your Linux partitions deletes GRUB, which is very bad if you can't run /fixmbr).

2. If your Windows XP disk was shipped with your computer, there is a very high chance it will not help you fix the MBR. For reasons I am unable to explain, I have never been able to use the /fixmbr command with an OEM disk. You should try anyway, then continue with the first option if it works. If it does not, download another boot manager like GAG, install it, don't give it instructions on where Linux is (so no errors occur if it can't find it), and reboot. If it works, then you should proceed by deleting your Linux partitions and making Windows big again.

---

