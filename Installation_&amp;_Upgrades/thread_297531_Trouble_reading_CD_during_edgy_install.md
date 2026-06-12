---
title: "Trouble reading CD during edgy install"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by scot524 on 2006-11-11
I am having difficulty installing edgy on a Sony Vaio VGN FS680. I have tried installation from the live CD (a few times). I have checked the md5sum as well as check the CD using the provided menu option and everything is fine. The boot process was very slow, given that this notebook is fairly new. When I begin the install process, things work as expected for a while. Eventually the installation process "hangs" with the CD sounding something like an old floppy drive.

I have had similar problems with the alternate install. Again, md5sum has been verified and contents of CD have checked fine. Similar problems ... installation eventually hangs or the installation tells me the CD is not mounted with the CD making alot of noise. I have tried acpi=off as boot parameter for the install to no avail. Also tried fb=false, also no luck.

Since, the point at which the installation stops is not predicatable, I think it is some sort of buffering problem. Does anyone have thoughts?

I am thinking about trying to install from USB drive and figuring out the problems with CD/DVD once installed?

---

### Post by wpshooter on 2006-11-11
Is the hard drive on this laptop blank or is there another O/S already on it ?

---

### Post by scot524 on 2006-11-11
It's blank now! Had XP

---

### Post by wpshooter on 2006-11-11
According to what I have seen in other post, there may be problems with installing Edgy on certain Laptops.

Why don't you try blanking the hard drive with this wiping program and give installation with the ALTERNATE CD another try.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by xcity on 2006-11-12
I saw this problem too, and my solution is burn another CD, using same image, and it's solved.

---

### Post by scot524 on 2006-11-12
It's not the CD -- I have verified the contents on another Ubuntu box. I think it is something weird with the Sony laptop. I wouldn't say for sure that is an Ubuntu problem. I don't know much about the history of this laptop, perhaps the optical drive itself has issues. 

I have played around with different boot options to disable PCMCIA bridge, etc. all to no avail. Since I have several working Ubuntu machines here, I am going to try a network install. It looks easier than the USB install. 

Wish me luck! I am not giving up until I get this running.

---

### Post by bulldog on 2006-11-12
> **scot524 said:**
> It's not the CD -- I have verified the contents on another Ubuntu box. I think it is something weird with the Sony laptop. I wouldn't say for sure that is an Ubuntu problem. I don't know much about the history of this laptop, perhaps the optical drive itself has issues. 

I have played around with different boot options to disable PCMCIA bridge, etc. all to no avail. Since I have several working Ubuntu machines here, I am going to try a network install. It looks easier than the USB install. 

Wish me luck! I am not giving up until I get this running.

**That's the spirit,go for it,you won't be disappointed!! **

---

### Post by scot524 on 2006-11-12
It's up ... network install did the trick. Actually, quite nice since there is not a massive update after a CD based install. Haven't stress tested the optical drive yet ... as I am going to see how well f-spot handles 18gb of photos.

---

### Post by PillowFightin on 2006-11-12
Can I ask how you did the network install?

---

### Post by scot524 on 2006-11-12
Instructions are here: [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

5 minutes to get going -- install took about 45 minutes or so.

---

