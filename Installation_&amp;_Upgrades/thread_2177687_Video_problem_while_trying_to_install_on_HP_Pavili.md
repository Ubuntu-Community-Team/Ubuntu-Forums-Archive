---
title: "Video problem while trying to install on HP Pavilion laptop"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by Andrew_Murphy on 2013-09-29
Hello.

I'm trying to install ubuntu-12.04.3-desktop-amd64.iso onto an HP Pavilion dv6700 laptop.  I've installed Ubuntu a few times in the past without a problem - on different hardware - but on this laptop I am having problems with the video during the live CD's boot up.

If I leave it alone during boot I see the 'press any key for options' screen, then the next screen shows the word "ubuntu" spread across the screen in three chunks.. kind of broken up and repeated.  The next screen is also very broken up and scrambled, I've been able to open up some of the option menus from the top right icons, but can't make any changes.

I've read the help page here: [https://help.ubuntu.com/12.04/installation-guide/amd64/boot-troubleshooting.html](https://help.ubuntu.com/12.04/installation-guide/amd64/boot-troubleshooting.html) and then tried pressing the space bar during the options screen, then "F6" to get the boot configuration parameters string.. then adding vga=788 and also fb=false.  Neither of these parameters has made any difference.

I've tried using a thumb drive and a DVD.  I've also tried using ubuntu-12.04.3-desktop-i386 instead.  Made no difference.

I'm sure that the video card must be working ok, as I currently have Vista installed and it runs without a problem.

---

### Post by mastablasta on 2013-09-30
what about nomodeset boot parameter?

also is this an UEFI laptop?

---

### Post by su:bhatta on 2013-09-30
See if following the instructions on this page helps: 

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

Also, you can give it a try with  13.04 which has a newer kernel

  And, it would help us if you provide us with complete specifications of the laptop, like CPU, GPU/APU etc along with mastablasta's request of providing information about UEFI boot .

---

### Post by Andrew_Murphy on 2013-09-30
> **mastablasta said:**
> what about nomodeset boot parameter?

> **bhattabhishek said:**
> See if following the instructions on this page helps: 

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

The **nomodeset **boot parameter did the trick!  Ubuntu is installing now.  Thank you! :D

I don't know if this laptop uses UEFI or not.. I can't find anything on the HP website about it.  Though since it's installing now, perhaps it's a non-issue either way.

Thanks again!

---

### Post by su:bhatta on 2013-10-01
Glad you got it working. Hopefully there is no problem in subsequent boots.

Welcome to the world of 'Linux for Human Beings'
Please mark this thread as 'Solved' using the 'Thread Tools' at the top right of this page.

---

### Post by mastablasta on 2013-10-01
here is how you make it permanent if you continue to have same issues after install: [http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)

---

