---
title: "Use Ubuntu on CD to boot crashed computer?"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by BeepDHHS on 2011-06-06
Call me a pre-nubie or something as I do not yet have Ubuntu installed on a system.  I have a crashed Dell E310 running Windows XP.  I'm not yet sure what the nature of the crash is.  The computer won't boot into Windows unless it is in Safe mode, and then it only stays up for about 3 minutes.  While it is up, the file system is accessible - I was able to open an Excel file briefly to write down a few of the most important records.  We have purchased a Dell laptop running Windows 7 and would like to transfer files from the E310 to the laptop.  I've considered pulling the drive from the E310 and installing it into an external case (which I will have to purchase) which can then be connected via USB directly to the laptop.  But something on Ubuntu's website suggests that there might be another way.

On the web page, [http://www.ubuntu.com/download](http://www.ubuntu.com/download), there is a selection titled, try it from a CD or USB stick.  The way it reads, suggests to me that the Ubuntu OS can reside on a CD or USB stick and computers would be able to boot from the CD or stick.

1. If this is the case and I elected to boot the E310 to Ubuntu via CD, would I then be able to access the E310's hardrive via a direct USB connection to the laptop?
2. If so, would the operation work better if both systems are booted to Ubuntu and would the transferred files be readable by Windows 7 on the laptop?
3. Assuming the E310 can be booted up under Ubuntu, are there any analytical tools I might be able to use to try and trace a hardware problem (like a defective memory chip), a utility to fix  errors on the hardrive, or security software to run against the drive (in case the problem is a virus that my McAfee failed to intercept)?

Or is my best bet to do the external drive case bit?

If the E310 can be salvaged, I'm considering turning it into a PVR, but I will have to add a tuner card to do that.  Would switching to Ubuntu (or running it side by side with XP) be recommended for that purpose?

---

### Post by Joe of loath on 2011-06-06
1. Yes, but a direct USb connection isn't perfect. Network sharing or sneakernet (using USB drives or a USB hard drive) will be easier to set up on both systems.

2. Yup, no problem, as long as the disk you use is Windows formatted (Which it will be by default, even if you format it in Ubuntu).

3. There is memtest86 on the boot menu of the CD, and you can install antivirus while in live mode (if you have internet connectivity). Installing it when using a USB version will mean it's there next time you need it, too. I don't know if there are any hard drive utilities though, I've not used Windows for months :p

Ubuntu (Or more accurately, mythbuntu) would be perfect for your purposes there. Mythbuntu is set up as a media centre, and is IMHO better than Windows, since the level of maintenance needed after installation is near zero. So no squinting at the screen trying to scan for viruses, or defrag the disk, or rebuild the registry ;)

---

### Post by BeepDHHS on 2011-06-06
So, provided there isn't a hardware fault standing in the way, installing Ubuntu to two CDs and using a USB stick to transfer files should do the trick.  Or do I even need the second CD (for the laptop) since in this scenario there would be no direct connection between the two computers?

You mentioned formatting.  Are you referring to formatting the stick, or to the CD to which Ubunto is installed?

Speaking of the CD.  Should I use CD/R or CD/RW and do they need to be finalized?  I have on hand some CD/R and DVD/RW.

Is installation on the CD as simple as placing a CD in the drive and clicking on the "Try it from a CD or USB stick" selection on the web page?

---

### Post by Joe of loath on 2011-06-06
You'd only need Ubuntu on the PC that needs rescuing. Sticking the files on a USB stick will then suffice.

The USB stick. Unless you need to do it (IE it's corrupted), there's no reason to need to format it.

Personally I'd use a CD-R, CD-RW's are tricky between different burning programs on the same PC, let alone different operating systems.

Yup, it is indeed :D

---

### Post by sanderj on 2011-06-06
Easy and little cost: build your E310's harddisk into a external hard disk enclosure with USB (about 25 Euro / 35 USD), and connect it to the Windwos 7 machine. Easy. No Linux/Ubuntu needed.

Or: 
The Ubuntu way (not easy for a newbie): boot a Ubuntu CD in the E310. You don't need to install it! 
See if it works and it keeps running. If so, you could:
- copy the files you want to keep to a USB stick / USB hard disk, which you then put into your laptop, OR
- try to make a Windows network. That's not easy for a newbie; it's needed on both the Win7 and the Ubuntu machine.

---

### Post by BeepDHHS on 2011-06-06
Thanks a bunch Joe.  You've been a big help.:-)  I'm guessing I will need to finalize the CD.

---

### Post by Joe of loath on 2011-06-06
> **sanderj said:**
> Easy and little cost: build your E310's harddisk into a external hard disk enclosure with USB (about 25 Euro / 35 USD), and connect it to the Windwos 7 machine. Easy. No Linux/Ubuntu needed.

Or: 
The Ubuntu way (not easy for a newbie): boot a Ubuntu CD in the E310. You don't need to install it! 
See if it works and it keeps running. If so, you could:
- copy the files you want to keep to a USB stick / USB hard disk, which you then put into your laptop, OR
- try to make a Windows network. That's not easy for a newbie; it's needed on both the Win7 and the Ubuntu machine.

I'd say that booting from the CD IS easy for a newbie, but creating a network is not. Samba (Windows network filesharing protocol) is also slow as hell.

EDIT: Yeah, it will need to be finalised. However, if you create a data project in Brasero (disk burner) all that will be done automatically.

---

