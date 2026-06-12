---
title: "Dual Boot Ubuntu and DSL"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by mjlambie on 2006-07-28
I am looking to install Ububtu and Damn Small Linux on a limited resources laptop.  How should I go about doing so.  I have installed a dual boot windows/ubuntu machine before w/ no problems by following online documentation, i just can't find anything on to do Ubuntu and DSL.  Any other small linux package would be cool too.  any help is very much appreciated.

thanks.

michael lambie
michael.lambie [@] gmail

---

### Post by tuxcantfly on 2006-07-28
install ubuntu first, and make sure DSL doesn't install a bootloader. instead, add it to the grub boot list in ubuntu (/boot/grub/menu.lst); just find where the DSL kernel is (somewhere in /boot), which disk partition it's in, and add it to the boot list (by the way, why do you need DSL? xubuntu works fine if you're on limited resources)

---

### Post by crayak27 on 2006-07-28
I did this awhile ago. Make three partitions, using some kind of live-cd (gparted live cd is good), one swap (hda1) and the others ext2 (hda2 + hda3). Run the ubuntu installer and make hda2 "/"  hda3 mounted under "/media/DSL". Then check it boots. If it does, use the damn small linux installer and install to hda3. Configure grub so all both ubuntu and DSL are available and you're done! :D 

*partition names like hda2 are just examples, yours could be different.

---

### Post by mjlambie on 2006-07-29
Thank you so much for both recommendations ubuntu community members.  #1 thanks for the hint of xubuntu, i had no idea what that was, i had heard of edubuntu, but didn't know about 'x'.  #2, thanks for the word of dual-boot linux. sounds pretty easy, just wasn't sure how to do it. 

I think i will try a comparison of DSL-n vs. xubuntu dual-boot style. 

I heart ubuntu!

---

### Post by mjlambie on 2006-07-29
So, my only new question is...  What are the major differences between xubuntu and ubuntulite?

[http://www.ubuntulite.org/]("http://www.ubuntulite.org/")
[http://www.xubuntu.org/]("http://www.xubuntu.org/")

???

why isn't ubuntulite listed on ubuntu.com ?

---

### Post by Jagot on 2006-07-29
Xubuntu uses XFCE:

[http://www.xfce.org/](http://www.xfce.org/)

UbuntuLite uses IceWM:

[http://www.icewm.org/](http://www.icewm.org/)

UbuntuLite is not an official variant of Ubuntu - Canonical do not have anything to do with it as far as I know, which is why it is not listed at Ubuntu.com.

---

