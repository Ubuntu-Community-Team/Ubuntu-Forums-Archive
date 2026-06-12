---
title: "remote install"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by dioz on 2005-05-26
hi all,
 i want remove windows to install ubuntu into an old notebook (Sony Vaio pcg.sr5k)
but it has not floppy or cd.. than.. can i install it by remote?

my primary desktop have ubuntu hoary and xp pro..

help!!!

tnx for yr time and sorry for my bad english


dioz

---

### Post by netrattler on 2005-05-26
Here are a few links to help you out

[http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2)

[http://www.ubuntulinux.org/wiki/NetbootInstallHowto](http://www.ubuntulinux.org/wiki/NetbootInstallHowto)

Joe

---

### Post by rtz654 on 2005-05-27
I also had to perform a remote installation because of the same reason like you. But it is a little bit tricky as you have to set up BOOTP/DHCP, TFTPD and so one...

Before we start, is your notebook able to perform network boot (most built-in netwoprk controller)?? And what network controller do you have?

---

### Post by dioz on 2005-05-27
tnx netrattler for the link, but i have not an optical/floppy device.. :(

> 
Before we start, is your notebook able to perform network boot (most built-in netwoprk controller)?? And what network controller do you have?


i'll check if the network boot is possible on my laptop,
ii have  a tricom pcimcia ethernet card

but is possible copy the files of installation directly into the hard drive and launch it on the boot without cdrom or floppy?

tnx!!!

---

### Post by netrattler on 2005-05-27
Yeah it should be no problem copying the files to the hard drive and installing it from there, you just have to tell it where to look for it. Another thing you might want to try if your laptop has USB ports, some laptops allow you to boot off USB devices.

Joe

---

### Post by dioz on 2005-05-27
[QUOTE=netrattler]Yeah it should be no problem copying the files to the hard drive and installing it from there, you just have to tell it where to look for it. Another thing you might want to try if your laptop has USB ports, some laptops allow you to boot off USB devices.

Joe[/QUOTE]


my laptop cant boot from usb.. :(

i lose?

---

### Post by netrattler on 2005-05-27
I'm going to try some things and get back to you, Im going to see if I can make the boot floppy image for ubuntu boot off hard drive I would think it would be able to work but I've never tried. If it works then all we would have to do is make a small partition on your hard drive on the laptop for the ISO image, which you could always transfer with ssh if you have it installed on your desktop and just download putty for windows to transfre the files. So I'll see what I can come up with.

Joe

---

### Post by netrattler on 2005-05-28
Well I found another link of someone that has done it try giving this a try.

[http://ubuntuforums.org/archive/index.php/t-28948.html](http://ubuntuforums.org/archive/index.php/t-28948.html)

But I'll still try and see if I can't come up with another solution that might be a little easier incase you have trouble with this.

Joe

---

### Post by dioz on 2005-05-28
tnx a lot netrattler!
now i'll try the solution of yr link, if i'll have problem i come back, tnx again!! :)

---

### Post by dioz on 2005-05-28
work fine!!!  \\:D/ 
tnx a again!!!  


 ;-)

---

### Post by netrattler on 2005-05-28
Glad to here it worked for you.

Joe

---

