---
title: "GRUB corruption"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by biohazardhm on 2010-11-06
someone used a livecd to format linux partition. that stupid guy i can't boot with any ubuntu CD. also my GRUB is corrupted and when i start my pc, i get a black screen with "grub rescue>"
i can't boot with Windows vista also. how can i repair it to get my pc work. i don't want to format all of my harddrive. 

i've noticed that i can boot with gparted livecd(with debian). is there a way to repair my system by booting with it ? if there is, how can i do that? if there isn't, how can fix it?

---

### Post by dino99 on 2010-11-06
to restore the deleted partition, use tools from cgsecurity

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

you got "grub rescue" because it cant find its path, you can edit the boot line to give the good path

---

### Post by biohazardhm on 2010-11-06
> **dino99 said:**
> to restore the deleted partition, use tools from cgsecurity

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

you got "grub rescue" because it cant find its path, you can edit the boot line to give the good path


could you give an instruction for "giving a good path"? thanks in advance. i don't want that partition. it was ubuntu 10.04 and if i can remove it, i can boot with ubuntu 10.10 and install it.

---

### Post by Rubi1200 on 2010-11-06
If you can boot the computer with a LiveCD, please post the results of the boot-script linked at the bottom of my post.

The information will help us determine the exact details of your setup and make offering solutions easier.

Right now, we are in the dark. The fix may be something relatively simple or may require some more work. The results will help us with that.

Thanks.

---

### Post by ryadav on 2010-11-06
boot into rescue mode with your install cd and reinstall grub again

[[COLOR=#000099][FONT=Arial]_https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202_[/FONT][/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by Rubi1200 on 2010-11-06
Under normal circumstances, I agree that reinstalling GRUB is usually the solution to such problems.

Here, however, I strongly advise waiting for the boot-script results.

We do not know the whole picture, what was messed around with, or if there are other issues that need to be dealt with.

---

### Post by kansasnoob on 2010-11-06
> **biohazardhm said:**
> someone used a livecd to format linux partition. that stupid guy i can't boot with any ubuntu CD. also my GRUB is corrupted and when i start my pc, i get a black screen with "grub rescue>"
i can't boot with Windows vista also. how can i repair it to get my pc work. i don't want to format all of my harddrive. 

i've noticed that i can boot with gparted livecd(with debian). is there a way to repair my system by booting with it ? if there is, how can i do that? if there isn't, how can fix it?

If your Linux partition was "formatted" I assume you have no Linux installed anymore but still have grub installed to the mbr.

If that's correct, and I'm only guessing, then restoring the Windows mbr should hopefully get Vista booting.

If you have a Vista recovery CD you could follow the appropriate steps here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It's also possible to do so with an Ubuntu Live CD but it sounds like you don't have one that will boot, eh?

I'm confused when you say, "i can boot with gparted livecd(with debian)". Exactly what CD are you talking about?

I've never tried usin a gparted cd for anything but partitioning :confused:

---

