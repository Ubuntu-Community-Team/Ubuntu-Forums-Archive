---
title: "Continuing install after initial boot"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by Chairboy on 2006-10-16
I've searched the forums, but can't seem to find a thread about my specific issue.  

I've installed Edgy Eft on a Dell GX620.  I set it up to dual boot using the Windows boot manager and installed Grub to /dev/SDA2 which is my ext3 partition.

I ran the install and completed the text-UI portion.  On reboot, I choose my ubuntu partition in the NT loader and then chose my kernel at the top of GRUB's load screen.  It begins the Ubuntu boot graphically (loads the filesystem, networking, etc) then drops me back to a text mode to login to my system.  I provide my username and password, then it drops me to a a prompt and...  nothing.

I use dpkg-reconfigure to fix my X settings and then startx, but I get the error that my .xsession file is missing.  Presumably, the install has not actually completed (based on my read of other people's install sessions).  

How do I manually launch the "Finish the dang install" procedure?  Or am I barking up the wrong tree and need to just fix the .xsession deal on its own and go from there?

Thanks!

---

### Post by TheWizzard on 2006-10-16
maybe try dapper. 
although a lot of people run edgy without problems, dapper is a more polished release.

---

### Post by Chairboy on 2006-10-16
Followup, I tried to guess what the next steps would be and seemed to have hit upon a winner.  I apt-got ubuntu-desktop and did a startx after that, and it pulled me into the UI.  Presumably that was what the install script would have done.  I'm sure there there are other elements that are not quite there, but I've got enough to continue on my own.

Thanks!

---

