---
title: "Installation Help!"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by max_noob on 2009-12-08
Downloaded the disk image and opened it with Nero Express Essentials and I gave me an error about the block size not corrosponding to the image length. It asked me if I wanted to correct this (and thinking it would do it by it's self) I clicked yes but it asked me to fill out information on it so I canceled and reopened the file. This time it burn. I rebooted and it ran I selected my language but when I it came up with a menu I pressed install. It said : I/O Error
---------------------- 
Read disk Error
 
The only option was "reboot" so I did this and selected another menu item but they all did the SAME thing. THe message. Can someone help?

---

### Post by lisati on 2009-12-08
It almost sounds like the ISO file didn't download properly. Short of downloading a fresh copy, you might want to check out the md5sum of the file.
If you're not sure how to do this, have a look here: [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

---

### Post by tommcd on 2009-12-08
If the iso image you downloaded does not pass the md5sum check, then download Ubuntu again. Also, download it from a different mirror site if you can.
I assume you are burning the CD from Windows. Instead of using Nero, I would recommend using the free programs Iso Recorder of Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD at the slowest possible speed to minimize the chances of a bad burn. Then when you boot the CD, first run the option that says: "check disc for defects". This will check the md5sums of all the files on the CD to make sure the CD is good.
If the CD passes the check, then proceed with installing Ubuntu.

And welcome to the Ubuntu forums!

---

