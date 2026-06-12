---
title: "yet another weird partitioning issue"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by elhoir_220582 on 2010-01-20
hi all,
i have 3 primary partitions in my PC,
The 1st one has only the Windows 7 boot manager
The 2nd one has the Windows 7 OS itself
and the 3rd one contains backup drivers and tools, so i can get rid of it if i want...

I want to create a 4th one which i will use to install Ubuntu

the thing is, the OS is not in the same partition as the boot manager, and i dont know if Ubuntu will detect it

btw, i have to use the alternate CD to install Ubuntu. I dont know the reason (SATA drives maybe?) but the normal CDs dont work....

And, when it goes into the Partitioning tool, it does not show "windows 7" or anything like that, just "ntfs partition" .. i dont know if ubuntu is detecting it or not....

Could you help me please?
Many thanks

---

### Post by mk1w86 on 2010-01-20
You will probably have to use Grub if you want to boot Ubuntu, not the Windows 7 boot manager (I didn't even know you could have Windows boot manager on a separate partition :o).

You might want to consider making the 4th partition an extended partition because for Ubuntu you will need a root partition and a swap partition. ;)

When you install Ubuntu it should automatically detect Windows 7 boot manager and create a Grub boot entry for it.  I am not 100% sure though what the installation program looks for when adding boot entries, maybe someone else does. :-k

---

### Post by darkod on 2010-01-20
How does the standard cd not work precisely? Any error message?

Try running the Try Ubuntu option first and see how it runs from the cd. As for win7 having the 100MB boot partition, don't worry. Yes, ubuntu can pick it up and knows what to do.

---

### Post by Grenage on 2010-01-20
Yup, it should be ok.  Grub 2 is ace at detecting installs (not that Grub wasn't).  It should overwrite your existing bootloader and reference Win7.

---

### Post by elhoir_220582 on 2010-01-20
> **darkod said:**
> How does the standard cd not work precisely? Any error message?

yes, i get I/O errors when reading from CD :-/

i have checked disc for errors and it seems to be ok. Also, i tried right after burning the CD so i dont think its wrong :)

---

### Post by darkod on 2010-01-20
> **elhoir_220582 said:**
> yes, i get I/O errors when reading from CD :-/

i have checked disc for errors and it seems to be ok. Also, i tried right after burning the CD so i dont think its wrong :)

I/O errors might be from the optical drive too. And I'm not sure the check disc for errors would always report them. :)

You could try usb stick, that way you save CDs. Or the alternate image as mentioned.

---

### Post by Kevbert on 2010-01-20
Make the fourth partition an extended partition. Then make a new logical partition which is big enough to store all your drivers etc (as you may need them at some stage in the future). Copy all the drivers in the third partition to the fourth and then delete the third partition. Now you can enlarge the extended partition to include the space left by partition three and move the new logical partition to the beginning of the newly enlarged extended partition.
The remaining empty space can be used for your new installation of Ubuntu (you can sort this when you install).

---

### Post by elhoir_220582 on 2010-01-20
> **darkod said:**
> that way you save CDs.
No need, i use CD-RW ^^^
 
i will install Ubuntu this evening.... wish me luck

---

### Post by elhoir_220582 on 2010-01-20
> **Kevbert said:**
> (as you may need them at some stage in the future
 I have already copied those data in a DVD

---

### Post by elhoir_220582 on 2010-01-21
hello guys,
this is to say that i installed ubuntu succesfully, and it did detect the Win 7 loader correctly :)

i had to play with apt sources due to the I/O errors when reading from CD-ROM, but its finally working

Thank you so much for your help

---

