---
title: "Slightly confused"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by marc61 on 2007-09-15
Hi, I'm new here and have been trying to figure out the next step to burning the ISO to a CD. I have downloaded the InfraRecorder and understand that I must also do an Md5Sum. What I'm not sure about is the WinRar archive. Should I extract the files to let's say my documents, then burn them? What is the procedure for doing it properly? I've read all the help and forums and do not see any reference about extracting files from WinRaR.

---

### Post by Pumalite on 2007-09-15
Go here and download an iso: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Then here is a guide to burn them: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by marc61 on 2007-09-15
Obviously if I have the WinRaR archive I've already downloaded the ISO. I've read all that stuff. My question was: Should I extract the files to let's say my documents, then burn them? What is the procedure for doing it properly?

---

### Post by Pumalite on 2007-09-15
Read Burningisohow-to

---

### Post by Gremlinzzz on 2007-09-15
Just burn the rar file.

---

### Post by marc61 on 2007-09-15
Thanks Gremlinzzz, worked fine. Now, another issue. I have tried this with 2 CD-RW's and I get the same results. I get the first screen that asks if I want to install, check cd for errors etc. I tried to check the cd for errors (on both cd's actually) and keep getting I/O error- error reading boot cd. The same with choosing the installation option too. If I have issues with my cd's, can this be done from my external hard drive?

---

### Post by t3hi3x on 2007-09-15
with bootable isos there are other things than just files on the image. you must use a program that will take an ISO file and then burn the iso based on that. an example would be Nero.

ignore the md5 checksum. this is to verify the validity of the download.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/) is a link to a program that ill burn the iso files


DO NOT EXTRACT THEN BURN THE FILES. this will not work because of the way bootable isos work.

---

### Post by marc61 on 2007-09-15
Ummmm, all that's been done, with infrarecorder and the files where not extracted. The issue is when I boot the cd I try to check the cd for errors or try to install, it freezes and gives me this message: I/O error- error reading boot cd. That's why I'm wondering if I could do this from my external harddrive.

---

### Post by t3hi3x on 2007-09-15
[http://ubuntuforums.org/showthread.php?t=192689](http://ubuntuforums.org/showthread.php?t=192689)

---

### Post by Pumalite on 2007-09-15
Update your firmware.

---

### Post by marc61 on 2007-09-15
Well, I guess there's no resolve to this because there is no update for my firmware. Guess it's Windows for me.

---

### Post by Pumalite on 2007-09-15
Not so fast. Sometimes this is resolved in BIOS. Go to BIOS>IDE Configuration>Set to 'Enhanced Support for PATA+SATA'
If your BIOS doesn't offer the option, then you could still solve it by setting your CD-DVD drive to 2nd Master in your computer and 'Auto in your BIOS.

---

### Post by marc61 on 2007-09-15
Looked through my bios, not a thing about IDE configuration.  Regarding your second option, I have no idea on how to make those changes (setting 2nd master etc.) I'm using ME, can you follow me through? I really want Ubuntu. I've spent all day with this, I hope if I eventually do get the cd to work that the rest goes smoothly. My patience is running thin.

---

### Post by marc61 on 2007-09-15
Still can't find anything relating to IDE configuration and pata and sata. Did find that my cd is set to the 2nd master and on auto. So far, there is no firmware update, I've verified that my protected mode drivers are 32 bit, I disabled UDF support, disabled DMA, reduced drive caching, and disabled auto insert. All suggestions made by Microsoft help. Nothing worked. So, I'll try using a cd-r instead of a cd-rw and see if that does anything, because so far I can't get this thing to work. I'm able to use any other cd in the player, it works fine for anything else except getting ubuntu to either install or check disk for errors. I was able to do a mem test. I was surprised it actually did that. It's booting, just freezes after booting.

---

### Post by t3hi3x on 2007-09-15
Do you have another cd rom to test it with?

---

### Post by Pumalite on 2007-09-15
Do md5sum on iso, Burn at 4x, check CD for corruption after burn and before install. Try CD in different computer. Definitely use good quality CD-R.

---

### Post by gali98 on 2007-09-15
yeah... It may be the cd-rw.. because they can go bad. Mine have before and I got the same error you are. You should really get a fresh cd-r and make sure that the iso didn't get corrupted on download. You might download again and burn that. and burn slow.... Pretty much what pumalite said. Just clarifying. Hope this helps,
Kory

---

### Post by marc61 on 2007-09-15
I do not have another cd rom to test it on. On both occasions I burned it at 4x. I read everything I had to before installing to make sure I knew what I was doing, I never thought I was going to have this problem as I said, I use my cd burner for all kinds of things and never have problems. I'll bring it to work and test it there.
Yeah, I think I'll try the cd-r. I have downloaded ubuntu twice, on two different cd-rw's. Both didn't work, md5sums were done each time. Actually they do work to a point, that is I can do a mem test after booting and I can do anything and the bottom as in help (F1) etc. It just won't install or check to see for disk errors.

Anyways, thanks folks. I'll see what happens with a cd-r.

---

