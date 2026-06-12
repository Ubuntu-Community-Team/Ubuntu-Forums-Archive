---
title: "Making Ubuntu a default"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2007-11-17
Currently I'm using XP. How do I make Ubuntu load by default? Or if there a way to have a transition scren where I can choose OS before loading? My Windows sem to kick in right away...

Thanks

---

### Post by taurus on 2007-11-17
Did you install windows after you installed Ubuntu?  If that's the case, you need to reinstall GRUB to MBR so you can boot either Ubuntu or windows.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by dodgingspam on 2007-11-17
No, I had XP and just installed Gutsy. In fact as soo as I'm able to figure out how to enable my Netgear card I'll reforemat my HD and reinstall Ubuntu only.

---

### Post by taurus on 2007-11-17
If you installed Gutsy last, did you install GRUB to MBR?

---

### Post by dodgingspam on 2007-11-17
apparently not. I t to boot using terminal and can't even find grub.
I received CD with Gutsy today and used only that to instal. How do I get grub?

---

### Post by taurus on 2007-11-17
When you install it to your harddrive, you will get to a section about bootloader.  You have options to either install GRUB and where you want to install it or skip that section.  I guess you probably skipped it.  You need to install GRUB to MBR if you want to get a menu to boot either Ubuntu or windows.  

Again, you don't have to reinstall Ubuntu.  Just look at the link in post #2 to install GRUB to MBR.

---

### Post by dodgingspam on 2007-11-17
I see. I read though that section on GRUb but it appears it all has to do with how to use it rather with how to install it. I can't seem to be able to locate GRUB anywhere and everytime I boot and try to get to Ubuntu I have to use the CD which seem to be installing Ubuntu everytime instead of just loading it... I guess I need to start over in the morning...

---

### Post by uxe1 on 2007-11-17
its easy to get confused, when you run the cd it appears to install, but its what called a "live disk" you have to double click the install icon on the desktop after the live session starts. it'll ask you some questions on how to install and will install grub for you. chose the "resize" option and you will have a duel boot system ware you can chose ubuntu or windows on start each time. -no cd. and it will be faster!!!

---

### Post by dodgingspam on 2007-11-17
You're absolutely correct. I went ahead and installed whatever was loaded on my HD and now see OS selection screen. However, when I select Win XP I get an error saying: 

A disk error occured.
Press Ctrl+Alt+Del to restart. 

How do I get to XP now?

---

### Post by uxe1 on 2007-11-18
there has to be an easer way than this, id search the forums or start a new thread... But, 
when that hapend to my g/friends comp, i put the windows disk in ,  the first time it asks if you want to be repair your old install say no, then the second time it asks say yes, it will go through he whole install thing but you wont loose any of your stuff. then you may have to install grub again.. if you do burn yourself a super grub disk, [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) it will walk you through it... 
like i said there has to be an easer way, im new too, so id search around

---

