---
title: "Need help installing"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by pwolschen on 2008-07-11
I have an HP 8765c. I have been trying to install ubuntu on it but whenever i select the install option a message comes up saying kernal panic not synching attempting to kill the idle process. at this point it wont do anything else. I tried running a memory test and everything failed not a single thing passed. XP is running fine on the computer why cant I get ubuntu to work?

---

### Post by wpshooter on 2008-07-11
Where did you get the CD that you are trying to boot/install from ?

Did you burn this CD yourself and if so, did you burn it at 4X or less and did you do a sumcheck on the CD burn ?

Also, if possible did you attempt to perform an integrity check of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by Pumalite on 2008-07-11
Maybe you need the Alternate CD depending on your pecs. Do md5sum on iso, burn the CD at 4x or less. Do not use CD-RW.

---

### Post by snowpine on 2008-07-11
How much RAM does your computer have? You need 384mb or more for the normal Live CD installation. If you have 256-383mb, try the Alternate CD (as Pumalite recommended), which you can download here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (check the box that asks if you want the Alternate CD)

If you have less than 256mb ram (which I suspect to be the case, given the vintage of your computer) I would not recommend installing Ubuntu. Either upgrade your RAM or try Xubuntu instead. 

Good luck!

---

### Post by pwolschen on 2008-07-11
The computer has enough ram. It has 384 mb. When i run the disk integrity check on a different computer its ok but when i run the disk integrity check on the computer i want to install on it says that it can't read the disk. I think I'm going to try reburning the disk and also try the alternate CD

---

### Post by ajgreeny on 2008-07-11
Before you reburn the iso check it has the correct md5sum.  I'm afraid I don't have a clue how to do that on windows if that is your only option, but it can be done, of that I am certain.  You can find the correct md5sum figure [here]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by VMC on 2008-07-11
> **wpshooter said:**
> Where did you get the CD that you are trying to boot/install from ?

Did you burn this CD yourself and if so, did you burn it at 4X or less and did you do a sumcheck on the CD burn ?

Also, if possible did you attempt to perform an integrity check of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

If you burn it using Nero or ImgBurn they have a verify option . Then do as wpshooter suggested. On the initial bootup screen there's a Media check. Do that.

Using the Alternate cd, I'm unsure of the media check, but md5sum should tell you of a good burn.

---

### Post by pwolschen on 2008-07-11
I burned the CD again and before i burned i did the check sum. I also verified the burn. However it still did not work. Any other suggestions?

---

### Post by Pumalite on 2008-07-11
Clean the lens in your burner or change it. If that doesn't work; install with the Alternate CD.

---

### Post by wpshooter on 2008-07-11
> **Pumalite said:**
> Maybe you need the Alternate CD depending on your pecs. Do md5sum on iso, burn the CD at 4x or less. Do not use CD-RW.

May I ask why you (and other postings I have seen on here) say not to use CD-RW.  That is the media that I do all my ISOs on and I do not have any problems with them ?

Thanks.

---

### Post by wpshooter on 2008-07-11
> **Pumalite said:**
> Clean the lens in your burner or change it. If that doesn't work; install with the Alternate CD.

Also, check to make sure that the firmware on your CD-drive is on the latest version.

Also, try a different brand of CD.  Drives sometimes have preferences as to what brand they seem to like.

---

### Post by avtolle on 2008-07-11
> **wpshooter said:**
> May I ask why you (and other postings I have seen on here) say not to use CD-RW.  That is the media that I do all my ISOs on and I do not have any problems with them ?

Thanks.
For my situation only, I've older hardware which only seems to be able to read CD-Rs; thus, why I recommend the use of the same. I've a new laptop that does well either way, but even on it I've had a problem (once) with a CD-RW used to try to install, the problem went away with a CD-R.

---

