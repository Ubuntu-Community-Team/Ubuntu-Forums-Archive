---
title: "clean install but wont boot just blank screen, tried other fixes no result"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by SticeXD on 2012-04-16
ok so i used to have ubuntu 10.04 installed on this computer (desktop) and then for reasons unknown to me i put windows 7 on it. now iv tried 11.10 12.?? and even tried 10.04 again. none will boot i can boot from cd no problem iv tried updating grub. iv tried the instructions in a similar solved case but it didnt solve the problem so iv settle on 11.10 and would love some help getting it going.

---

### Post by 2F4U on 2012-04-16
So just to be clear about your situation:
- you installed 11.10 to your computer?
- it boots up fine and works?
- you tried 10.04 and 12.04 and neither boot?
- you intend to install 12.04?

---

### Post by SticeXD on 2012-04-16
yes i installed 11.10 and thats what my computer says is currently on there iv tried reinstalling to the same result numerous times.

---

### Post by SticeXD on 2012-04-16
oops misread, i mean no none of them boot 11.10 inclueded i get the blank screen everytime i try too boot

---

### Post by Quackers on 2012-04-16
What graphics card are you using?

---

### Post by 2F4U on 2012-04-16
I would first attempt to set nomodeset in the grub kernel parameters and see if that avoids the blank screen:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by More or Less on 2012-04-16
11.10 gave me problems too.  I suggest installing 12.04 over your previous installations of Ubuntu, but don't install it over Windows 7.  I was able to do this with the USB installation. 

It managed to install within 10 minutes or so, and I previously had the same kind of problem you did.  I was using a version of 10, and it just wouldn't upgrade to 11.10 properly.

---

### Post by shad686 on 2012-04-16
I had the same problem when I first installed 11.10. It is a graphics issue. Hold down shift to get to the grub. I found the info needed in this thread [http://ubuntuforums.org/showthread.php?t=1741887](http://ubuntuforums.org/showthread.php?t=1741887) . Hopefullly it will be the same for you. If not do a search for your graphics card, and you should be able to find some help

---

### Post by SticeXD on 2012-04-16
ok so 10.04 always crashes at 64% 11.10 clean installs then black screen no amount of holding or pressing shift will pull up the grub, iv tried using the cd to get to terminal and update the grub, says it was done with no errors but still black screen trying 12.04 in a few after i get the disk burnt, if this fixes it awesome if not ill be back of course, thank all of you who have replied so far.

---

### Post by SticeXD on 2012-04-16
ok 12.04 officially up and running, it was a hard drive error some crap from windows 7 was infected and wouldnt delete until i formatted it by hand then everything went great, thank to everyone who posted

---

