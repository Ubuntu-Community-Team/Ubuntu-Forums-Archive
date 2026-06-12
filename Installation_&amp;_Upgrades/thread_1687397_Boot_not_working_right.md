---
title: "Boot not working right"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by PiZZA S4UC3 on 2011-02-13
I've tryed ubuntu 10.10 desktop, and netbook. with cd, usb, and wubi and install in windows. So far none have worked with the cd and the wubi I've gotten the same result. It seems to work and has the loading screen with the 5 dots... then it stops that and simply shows pieces of my windows background and taskbar randomly disperced on the screen. then if i turn my laptop off and back on it loads again but then it'll show black and white squares in a wierd patern. It does that every time i turn it on after. with the usb, as soon as I boot off of it it says boot error and when i hit ENTER it boots windows and if i press Esc it restarts my computer and boots windows.

---

### Post by oldfred on 2011-02-13
Welcome to the forums.

That sound most likely to be a video problem. What video card/chip do you have?


[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by PiZZA S4UC3 on 2011-02-13
It's a Geforce GTS 360M CUDA 1 GB

---

### Post by Rubi1200 on 2011-02-14
You can take a look here:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by albatross_ibais on 2011-02-14
hello friends,can any 1 help me....?when i want to installlll Ubuntu,it show an error msg dat's "error_code+0*73/0*78" .
Plz help me ..............

---

### Post by oldfred on 2011-02-14
I think Rubi1200's link is similar, but mostly for wubi installs.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

### Post by oldfred on 2011-02-14
[albatross_ibais]("http://ubuntuforums.org/member.php?u=1243853") welcome to the forum. but is is not considered good form to hijack another thread with a new problem. Please start a new thread and tell us what you have done with some more detail on when the error occurs.

---

