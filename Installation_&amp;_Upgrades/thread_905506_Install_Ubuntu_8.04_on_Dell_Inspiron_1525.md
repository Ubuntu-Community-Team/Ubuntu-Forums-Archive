---
title: "Install Ubuntu 8.04 on Dell Inspiron 1525"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by henry_d on 2008-08-30
Hi i have bought a dell inspiron 1525 with vista on it and have been reading all about the media direct button and how it destroys the partitions. 

I read how to fix it by zero formatting the drive from a live c.d. but dont know how to do this

I want to completely wipe vista and the media direct button so it wont destroy my partitions when i press it, and install ubuntu 8.04.

I didnt want to format the hard drive and then find out i couldnt install ubuntu and be left without an operating system or do something wrong and mess up the laptop. :)

Please could someone tell me how to zero the hard drive and get rid of the media direct button and how to install ubuntu 8.04 and tell me which order i have to do it in. Also if you could give me any links to tell me what drivers/software i might need to install to get everything working properly i.e. wi-fi, graphics tablets etc, it would be much appreciated.

The specs of my laptop are
**Ram:** 1GB
**Hard drive:** 100GB
**Processor:** Intel core 2 duo T2390 or something similar
**Wi-fi:** Dell wireless card 1395
**Webcam:** Built in creative 2mp webcam

Thanks very much

---

### Post by mikewhatever on 2008-08-30
Here is the installation guide [https://help.ubuntu.com/community/Installation#Standard%20installation](https://help.ubuntu.com/community/Installation#Standard%20installation)
You'll may have issues with Broadcom wireless also known as dell 1395.

---

### Post by henry_d on 2008-08-30
Thanks for the info. 

Does anyone know how to erase the media direct button and can i install ubuntu once i have zero formatted the drive.
Im dont know much about computers and i thought if i zero formatted the drive it might not start up again properly to give me the option to install ubuntu.

Thanks

---

### Post by mikewhatever on 2008-08-30
Ubuntu does not need a hard drive at all to run from the Live CD, so, no matter if you format or not, it should start. I don't know anything about erasing buttons, and don't quite understand what you're talking about. It's strongly suggested to download and run a Live cd for hardware testing.

---

### Post by henry_d on 2008-08-30
Ok and if it's all working on the live cd and i want to install it can i do so from the cd. Will it wipe the hard drive as well?

Oh and as for the button deleting. There is a famous button on the inspiron 1525 (not sure if it's on other models) called the home button. If that is accidentally pressed it boots up the system and re-partitions the hard drive and you can start up ubuntu. 

There are quite a lot of people who have complained about this. I have also seen a few posts which say how to fix it but i didnt want to do it, as they said stuff like run the following code, but as im completely new to linux i didnt know where to run that code and when to do it, so i didnt do it in case your meant to type it in at a certain point. 
If someone could help me with erasing the button i would be very grateful.

---

### Post by SkonesMickLoud on 2008-08-30
As the 1525 is also available as the 1525n, you should be able to install Dell's Ubuntu image with no hardware problems.  You can get the CD image here:

[http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-cd-0.2-2.iso](http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-cd-0.2-2.iso)

And the DVD image here:

[http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-dvd-0.3-3.iso](http://linux.dell.com/dru/images/ubuntu-7.04-desktop-i386-dell-dvd-0.3-3.iso)

Note that both images are 7.04, so you'll need to update to 8.04 manually.

---

### Post by mikewhatever on 2008-08-30
> **henry_d said:**
> Ok and if it's all working on the live cd and i want to install it can i do so from the cd. Will it wipe the hard drive as well?

Yes, when ready to install, just hit the 'Install' button on the desktop.
There is also an option to use the entire HDD for Ubuntu installation.

> Oh and as for the button deleting. There is a famous button on the inspiron 1525 (not sure if it's on other models) called the home button. If that is accidentally pressed it boots up the system and re-partitions the hard drive and you can start up ubuntu. 

There are quite a lot of people who have complained about this. I have also seen a few posts which say how to fix it but i didnt want to do it, as they said stuff like run the following code, but as im completely new to linux i didnt know where to run that code and when to do it, so i didnt do it in case your meant to type it in at a certain point. 
If someone could help me with erasing the button i would be very grateful.

What you might be referring to is the recovery procedure that gets initiated by that button. If so, you'll probably want to delete the recovery partition, but then, you'll have no way of reinstalling Vista. Perhaps someone who owns a Dell and is more familiar with the issue can comment, meanwhile, have a look in [Dell Support Section]("http://ubuntuforums.org/forumdisplay.php?f=342").

> **SkonesMickLoud said:**
> As the 1525 is also available as the 1525n, you should be able to install Dell's Ubuntu image with no hardware problems.

That would be wonderful, but I suspect that Dells preloaded with Ubuntu ship with intel 3945 and not broadcom, besides, 7.04 is relatively old, I'd try the link below:
[http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso)

---

### Post by henry_d on 2008-08-30
Sorry it's not the home button it's the media direct button that re-partitions the hard drive. Also i think i will keep vista on there now. If i install ubuntu from the live cd does it give me the option to keep it vista and install ubuntu on a different partition? If it doesnt how do i keep vista on there and install ubuntu?

Thanks

---

### Post by henry_d on 2008-08-30
Im downloading the Dell specific ISO which is 2.1GB so it will only fit on a DVD. Will the following install information work the same for DVD [https://help.ubuntu.com/community/Installation#Standard%20installation](https://help.ubuntu.com/community/Installation#Standard%20installation)

Or do i have to burn it differently?

Thanks

---

### Post by mikewhatever on 2008-08-30
> **henry_d said:**
> Im downloading the Dell specific ISO which is 2.1GB so it will only fit on a DVD. Will the following install information work the same for DVD [https://help.ubuntu.com/community/Installation#Standard%20installation](https://help.ubuntu.com/community/Installation#Standard%20installation)

Thanks

I don't know about the 7.04 one, but don't use the iso I linked to if you want to keep Vista. That iso is only good to reformat the HDD and put Ubuntu on it. Use a regular desktop cd = live cd, test the hardware and make sure you understand the installation guide.

---

