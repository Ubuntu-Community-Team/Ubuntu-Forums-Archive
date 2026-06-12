---
title: "Live USB of Ubuntu 12.04 not crashing"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Quazze on 2012-08-09
(i'm not sure if i'm posting this in the right section)

Hello everyone

I was trying to work on Ubuntu 12.04 from a live USB-stick (in order to change my file system partition size). But it doesn't work. First off it loads very slow, which is maybe to be expected, but it is really very slow. But everything is still ok, until I have to choose between installing Ubuntu or just trying it out. When I click this it starts to load the dekstop (again very slow), but then it hangs. And after a while the screen starts to act strange and it flashes to this black and white rectangle grid and I have to reset...

I don't know what I'm doing wrong, I just use the Ubuntu 12.04 iso downloaded from the official website and make the live USB-stick with usb-creator-gtk.

Maybe a little extra information, I am using Ubuntu 11.04 on my laptop (because I first want to make my partition larger before I upgrade).

I am now trying with another distribution 11.11, so I'll see if that works, but I wanted to use the USB-stick also to install Ubuntu on another laptop...

thanks
Lukas

---

### Post by C.S.Cameron on 2012-08-09
If your machine is powerful enough for 12.04, check the MD5SUM of the iso.

---

### Post by gordintoronto on 2012-08-09
What video adapter is in your computer? You might need to use "nomodeset."
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

My preference is a program called Multisystem for creating a LiveUSB.

Very slow is normal, the other stuff is not. I assume "When I click this" means you clicked on "try Ubuntu."

---

### Post by johnathansmith on 2012-08-09
Hi, as guys above me mentioned, maybe your machine is not enough powerful. Also there is a possibility your USB stick is corrupted. Try different version of live ubuntu, for example 10.4.4 should be fine. Then post here your results.

---

