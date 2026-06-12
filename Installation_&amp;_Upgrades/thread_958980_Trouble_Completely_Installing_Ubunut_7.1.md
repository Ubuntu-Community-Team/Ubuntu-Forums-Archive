---
title: "Trouble Completely Installing Ubunut 7.1"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by beardedbroccoli on 2008-10-26
I am (as I write) for the fifth time trying to reinstall ubuntu 7.1.
It gets to a certain point in which it's *copying files...* and then it stops and im left with this the install black desktop and the shortcuts for computer, examples, install, and trash. 
Am i doing something wrong? Is there something im not doing? am i truely retarded? 
thanks so much, you guys have big brains! :D

---

### Post by eddietours on 2008-10-26
have you try Different cd also burn them to low speed

---

### Post by tommcd on 2008-10-26
How are you burning the Ubuntu iso? Are you burning it from Windows? If so, you may want to try INfra Recorder od Iso Recorder. I used Iso Recorder when I first installed Ubuntu and it worked well.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burning)|(image)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burning)|(image)|(iso))
 Also, as Eddie said, be sure to burn the iso at a slow speed.
Also, be sure to check the md5sums of the downloaded iso file and the CD after you burn it, to make sure there is no data corruption:
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=(md5sum](https://help.ubuntu.com/community/HowToMD5SUM?highlight=(md5sum))

The current version of Ubuntu is 8.04. I don't think it will make any difference, unless you are installing on very new hardware, but you may as well go with the current version.

---

### Post by beardedbroccoli on 2008-10-26
im installing from ubuntu
thanks for that, it seems to Do need to burn it slower. 
this is the error i got.
how can i burn it slower exactly???
> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

---

### Post by tommcd on 2008-10-26
> **beardedbroccoli said:**
> 
how can i burn it slower exactly???

See this section of the first link I posted in my last post
> In Ubuntu

   1. Insert a blank CD into your burner. A "CD/DVD Creator" or "Choose Disc Type" window will pop up. Close this, as we will not be using it.
   2. Browse to the downloaded ISO image in the file browser.
   3. Right click on the ISO image file and choose Write to Disc.
   4. Select the write speed. If you are burning a Ubuntu Live CD, it is recommended that you write at the lowest possible speed.
   5. Start the burning process. 

I always burn iso CDs in Ubuntu this way and rarely have a problem. Also, use a CDR if you have one, not a CDRW. In my experience, after a rewritable CD has been written to many times the chances of a bad burn, where the md5sums don't check, is much greater than with a regular CDR. 
To check the md5sums in Ubuntu, first find out how your CDROM drive is listed in fstab. Run
 ```
cat /etc/fstab
``` 
to find out what the CDROM drive is. On my system Ubuntu calls my CDROM drive /dev/scd0. So to check the md5sums, first eject the CD after you burn it and reload it. Then run 
```
md5sum /dev/scd0 
```
The md5sum of the disc you burn should match the md5sum of the iso file you downloaded.

You can also check the md5sum this way, as per the 2nd link I posted:
> First mount the CD, if not already mounted:
 sudo mount /dev/hda /cdrom

Then use the supplied md5sum file on the CD
cd /cdrom
md5sum -c md5sum.txt | grep -v 'OK$'

 The md5sums are listed on the download page from where you downloaded Ubuntu.

---

### Post by beardedbroccoli on 2008-10-26
shizze. 
it would appear my cd burner isnt working??? what the f, indeed. 
heh, so is there no way i can simply reboot the whole shindig in my cdrom drive and just reinstall everything? this is a precarious situation.

---

### Post by tommcd on 2008-10-26
I'm not sure what you mean exactly. Do you mean restart the install process? Sure, you can do that, as long as you have a good install CD. If your CD is bad, and you were half way through an install, then it is likely that your system partition was formatted and you won't be able to boot from the hard drive. If that is the case you will need a good install CD to boot from to start over.

---

### Post by beardedbroccoli on 2008-10-26
ill try that, i think someone i know has an ubuntu 8.4. thanks

---

