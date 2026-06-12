---
title: "HD partition question"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by natgab on 2010-06-20
I had to reinstall my Ubuntu 10.04 system after some trouble trying to remove a FAT32 partition.  I reinstalled using the Live Ubuntu CD (not Ubuntu Studio CD) and seems to work fine.  I want to know if its normal to have an unallocated space before the boot partition? I installed GRUB2 in the sdb1, not in main sdb, it that helps.

Ubuntu boots fine, but I was wondering if the unallocated space affects it being detected properly by other systems?  When I boot OS X I get an error that the HD is not formatted. Previously I was not getting the error.

OS X & Ubuntu are each on a separate SATA HD and Windows XP is on a third IDE HD.

---

### Post by drdos2006 on 2010-06-20
My guess is that OS X is complaining about the unallocated space, not Ubuntu. Might have to do some more searching about OS X and Ubuntu, but if you have only recently re-installed Ubuntu, you might consider re-installing using the whole of the HDD.

regards

---

### Post by natgab on 2010-06-20
> **drdos2006 said:**
> My guess is that OS X is complaining about the unallocated space, not Ubuntu. Might have to do some more searching about OS X and Ubuntu, but if you have only recently re-installed Ubuntu, you might consider re-installing using the whole of the HDD.

regards

-Yeah, I still have it as a stock system. I already reinstalled once, I even formatted as FAT32 from the Mac OS X side to wipe it and then did this last install. But I still got an unallocated space. 

Any of the three systems work fine individually if I go to BIOS and set the particular HD as boot.

---

### Post by drdos2006 on 2010-06-21
What happens if you disconnect the other drives and install Ubuntu on its own ?
Do you still get an unallocated section ?

regards

---

### Post by garvinrick4 on 2010-06-21
The 1 meg of unallocated space does not bother or effect anything.
If you have problems booting or recognizing other drives look for other
reasons.

---

### Post by natgab on 2010-06-21
> **garvinrick4 said:**
> The 1 meg of unallocated space does not bother or effect anything.
If you have problems booting or recognizing other drives look for other
reasons.

-Well, the HD does show up on the Chameleon screen with a Linux icon, just like the Mac & Windows icons.  So I guess Chameleon can see it regardless of the blank space.  

Is there a difference to Linux of where I place the boot partition?  Whether I place it in sdb or sdb1 ?

BTW I used the 9.04 live disc for the screencap because the 10.04 version is confusing in the way it shows the GRUB2 & swap next to each other.

---

### Post by darkod on 2010-06-21
This is just a guess on my side, but I think they made 10.04 leave 1MB in front of the first partition preparing it for SSD use. After all, 10.04 is LTS and there are more and more SSDs used.

A SSD needs the first 1MB empty because it uses them for garbage collection (not sure if it's the same as TRIM).

As for whether grub2 is on /dev/sdb or /dev/sdb1. It really depends how you are booting. It seems you use another bootloader that just chainloads grub2, so it doesn't really matter where you installed it.

On the other hand, if grub2 was on /dev/sdb you will see grub2 if booting from it.

PS. And it's not a boot partition, grub2 is just a bootloader if that's what you meant. There is big difference because you can also have /boot partition.

> Is there a difference to Linux of where I place the boot partition?   Whether I place it in sdb or sdb1 ?

---

### Post by natgab on 2010-06-21
> **darkod said:**
> This is just a guess on my side, but I think they made 10.04 leave 1MB in front of the first partition preparing it for SSD use. After all, 10.04 is LTS and there are more and more SSDs used.

A SSD needs the first 1MB empty because it uses them for garbage collection (not sure if it's the same as TRIM).

As for whether grub2 is on /dev/sdb or /dev/sdb1. It really depends how you are booting. It seems you use another bootloader that just chainloads grub2, so it doesn't really matter where you installed it.

On the other hand, if grub2 was on /dev/sdb you will see grub2 if booting from it.

PS. And it's not a boot partition, grub2 is just a bootloader if that's what you meant. There is big difference because you can also have /boot partition.

---Hey, thanks for the info about the SSDs.  I did not know they needed things like that, but it makes sense.  

Yes when I boot OS X, it first gives me Chameleon bootloader and then I choose the Linux icon and then I get the GRUB2 text screen.  

And I did know the difference between boot partition & bootloader, just was kinda tired after a weekend of reinstalling Ubuntu several times and still getting the error warning in OS X. ](*,)

---

