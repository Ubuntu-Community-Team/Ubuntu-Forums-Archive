---
title: "Adding another OS when you don't have a partition for it. Also, Jaunty Alpha"
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BetterSense on 2009-02-15
I have 32bit Hardy on this system, which has an ext3 / and a ReiserFS /home. I suppose I can use the Gparted liveCD to shrink the ReiserFS by 10GB or so, then create another partition for the dual-boot OS. But then, at that point, is this system going to be bootable, because of grub? The only thing I don't understand about the process is what happens with grub. Perhaps I MUST then install another OS so that I can get a new grub configuration installed. 

Also, I can't decide whether to install Intrepid x64, or the Jaunty Alpha. What do you think, what's that status of the Jaunty Alpha 4, is it useable? I kinda wanted to try out ext4 and KDE 4.2.

---

### Post by Partyboi2 on 2009-02-15
Creating another partition will not effect grub, once you install another o/s then it will rewrite grub.
If you don't want to shrink your partition down you could also use something like virtualbox to install a second os.

---

### Post by BetterSense on 2009-02-15
I was really wanting to both take advantage of my ram with a 64bit OS, and also maybe make a fresh start since this system has various nagging issues, mostly with Pulse and X.

I have a Virtual XP but I'm pretty sure since it lives on my /home I will be able to use it with the new OS as well after installing VB.

---

