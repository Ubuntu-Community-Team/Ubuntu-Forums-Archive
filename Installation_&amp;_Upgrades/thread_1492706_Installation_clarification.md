---
title: "Installation clarification"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by jlangholzj on 2010-05-25
hey all, 

I'm not new to C/unix...but it has been a while. Just been playing around with installing 10.04. LOVE IT!!! but I've been having issues with grub (imagine that). anyway. I got around it by unplugging my internal HD and installing ubuntu to a flashdrive. After going through it a second time, I noticed under the "advanced" tab there's an option to load or not to load grub and where to install it too. if i leave my internal plugged in, and select the flashdrive to have grub installed to it, i shouldn't have to worry about it interfering with stuff on my main partition should i??

thanks

-J

---

### Post by rob-ward on 2010-05-25
My concern would be that if you install GRUB on the penstick and make the Master Boot Record point to that then if you remove the penstick your computer won't boot.

So the question is are you wanting to be able to remove your penstick and when it's not plugged in for Windows(or whatever OS you have) to boot?

If you are trying to do this then I think what you need to do is make Ubuntu install Grub on the penstick and the MBR on the penstick while leaving your MBR on your internal drive intact. This way you then just have to configure your boot order so that if your penstick is in your computer will boot off of that, if it is removed then it will boot off of your internal HDD and boot whatever OS you have there.

Is that what your trying to do? 
did any of that make sense or help at all?

---

### Post by jlangholzj on 2010-05-25
> **rob-ward said:**
> My concern would be that if you install GRUB on the penstick and make the Master Boot Record point to that then if you remove the penstick your computer won't boot.

So the question is are you wanting to be able to remove your penstick and when it's not plugged in for Windows(or whatever OS you have) to boot?

If you are trying to do this then I think what you need to do is make Ubuntu install Grub on the penstick and the MBR on the penstick while leaving your MBR on your internal drive intact. This way you then just have to configure your boot order so that if your penstick is in your computer will boot off of that, if it is removed then it will boot off of your internal HDD and boot whatever OS you have there.

Is that what your trying to do? 
did any of that make sense or help at all?


exactly what i was trying to do! and yes, it made perfect sense. I was just curious if that MBR setting in the advanced tab right at the end of setup would like you said, install the MBR and Grub to the flashdrive while leaving the MBR on my internal HDD intact, its a pain to have to keep plugging and unplugging the darn thing! (I'm making multiple flashdrive/ubuntu setups)

---

### Post by darkod on 2010-05-25
> **jlangholzj said:**
> exactly what i was trying to do! and yes, it made perfect sense. I was just curious if that MBR setting in the advanced tab right at the end of setup would like you said, install the MBR and Grub to the flashdrive while leaving the MBR on my internal HDD intact, its a pain to have to keep plugging and unplugging the darn thing! (I'm making multiple flashdrive/ubuntu setups)

Yes, the advanced settings window will ask you where to install grub2. If you select the usb stick (for example if it's called /dev/sdb), then grub2 will be installed there and there will be no changes done to the internal hdd MBR.

Just make sure you select the stick, not a partition on it (if it has a number, then it's a partition on that disk).

---

