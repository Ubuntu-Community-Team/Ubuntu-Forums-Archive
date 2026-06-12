---
title: "grub altered"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by KRISHNASHK on 2012-01-27
I updated ubuntu using the ubuntu manager. after the update i am getting new grub entry for ubuntu? m confused how did that happen how should i delete it  and will deleting it hamper my system . I am using dual boot with windows 7?
thanks !

---

### Post by zvacet on 2012-01-27
Probably new kernel is installed with updates and that is why you have new line in grub.See if that kernel works and if it does you can delete old kernela from synaptic by typing in search box** linux-image** [FONT=Arial]and you will see all installed kernels.Delete one with lower number(maybe it is good practice to have two kernels in case newest doesn´t work as it should).Do the same with older kernel-headers.[/FONT]

---

### Post by raja.genupula on 2012-01-27
> **KRISHNASHK said:**
> I updated ubuntu using the ubuntu manager. after the update i am getting new grub entry for ubuntu? m confused how did that happen how should i delete it  and will deleting it hamper my system . I am using dual boot with windows 7?
thanks !
When new kernel updates ,you install . your grub will automatically update it after configuration of new kernel finished .you can see that Grub updating while new kernel installing .

You said you wanna delete Kernel , but old kernel or kernel . If you delete new kernel no use of updating i think . If you wanna delete old kernel then follow above post as our friend said.

 > after the update i am getting new grub entry for ubuntu? m confused how did that happen how should i delete it  

If you wanna delete the Grub entry kernels then the easiest way i can suggest you is moving with grub customizer . there you can select what grub entries you wanna see what you wanna hide in Grub Menu .
Dont delete New Kernels . 

Dont worry nothing will happen to your Windows 7 . 

All the best .

---

