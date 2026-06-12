---
title: "Dual Boot Install over Linspire"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by palmtree on 2007-04-18
I currently operate Linspire 5 and Win XP Pro in a dual boot setup on two hard drives one for Linux and the other for Win XP. The default is to boot into Linspire.

I want to replace/overwrite Linspire with Ubuto 6.10.

Any suggestions on the steps to take to accomplish this without damaging Windows XP hard drive and still have dual boot up option?

Thanks

---

### Post by ceciliaFX on 2007-04-18
I have the same question except my laptop is a multiboot with red hat (8, i think) and windows2000.

I have about 4 gigs for my linux - i sure hope that's enough because I don't want to mess around with the windows partitions.

And I like my Red Hat - I would just like to have a newer kernal. and i DON'T do things like "recomplile" the kernal.

i just want to install and work.

My main interests are GIMP and Quanta and using Opera. It would be cool to view DVD's and burn CD/DVD's but I ain't picky.

---

### Post by bwhite82 on 2007-04-18
Palmtree, if you can work your way around a partition manager, this is no sweat at all. Insert your Edgy disk (Depending on whether you're  using the LiveCD or alternate), eventually you'll get to a partition manager (one is graphical, the other textual) and make sure you mark your current Linspire parition to "format" and that it is mounted at "/" and is set to "bootable".

ceciliaFX, I wish I could help you out, but alas, I have never tried a triple-boot scenario, I am totally not sure how grub handles triple-booting. Although, I haven't heard many folks complaining about it so it shouldn't be too difficult.

---

### Post by ceciliaFX on 2007-04-19
I don't want to triple-boot - i want to replace the red hat with something else more upto date.

That is why i am checking out ubuntu.

I just hope i can use ubuntu in the 4 gigs currently set aside for red hat.

---

### Post by palmtree on 2007-05-10
Thanks for suggestions. I had success and now have Ubuntu 7.04 running on its own hard drive. I ran the Live CD and from that ran the install program. I selected the drive where Linspire resided and allowed Ubuntu to use the entire disk. It also made the dual boot menu and I am able to select Windows XP which is on the other harddrive if I need it, otherwise it boots to Ubuntu. All seems to be fine.

---

