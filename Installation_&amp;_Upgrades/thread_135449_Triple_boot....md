---
title: "Triple boot..."
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by chipyoung on 2006-02-23
I am currently running Windows XP and Knoppix linux on my hard drive.  Two partitions plus one partition for the linux swap.  My plan is to create another partition for a hard drive install of ubuntu5.10 for 64 bit.

I have not done a hard drive install of ubuntu before.  My question is will ubuntu handle my grub boot loader ( append the boot file). so that I have access to all 3 distros or will I need to stop ubuntu from modifying or writing over by MBR?  If I need to do that will ubuntu prompt me in the installation sequence.  Knoppix uses Grub and everything is woking now.

Thank you in advance,
Chip

---

### Post by mdsmith on 2006-02-23
It should work fine. I have 98 and Ubuntu on hda and Mdk 9.2 and Hdb. I didn't do anything special. I just let the Ubuntu installer take of it. Don

---

### Post by chipyoung on 2006-02-23
mdsmith,

I noticed you said you had these distributions on 2 hard drives.  I am trying to use just one hard drive.  Do you think I will have any problems using just the one?

Thanks

---

### Post by Schmic on 2006-02-24
> I have not done a hard drive install of ubuntu before. My question is will ubuntu handle my grub boot loader ( append the boot file). so that I have access to all 3 distros or will I need to stop ubuntu from modifying or writing over by MBR? If I need to do that will ubuntu prompt me in the installation sequence. Knoppix uses Grub and everything is woking now.


The ubuntu installation of grub will show you a list of other operating systems detected and prompt if you want to install grub to the MBR. The one's listed will be added to the grub loader along with ubuntu so as long as the other 2 are shown in the list you will not have a problem installing grub.

---

### Post by chipyoung on 2006-02-24
Thank you Schmick and mdsmith,

That's the answer I was hoping for.

I'm still serching for the best linux distro for me.  It's funny, I had no problems installing Knoppix on my 3 machines, but when I tried ubuntu  I was unable to install it on any machine.  With the help of the forum I was able to search down my problem.  it was an ATI problem.  I had to go to the expert mode and use the vesa driver.

You guys are great.  Keep up the good work, and have another cup of coffee and I hope they fix the ATI problem.

Thanks,
 Chip

---

