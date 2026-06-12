---
title: "Grub Rescue&gt;"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by manickaselvam on 2011-05-30
Yep... I have researched many thing about this GRUB RESCUE> prompt. Even though I had similar problems earlier i could able to solve with UBUNTU 9.04. 

Recently i have upgraded from UBUNTU 9.04 to UBUNTU 11.04 by Bootable USB. It was not booting, then found an answer from a forum that i need to change the word "ui" in bootable file. :(

Then everything went fine with the installation. But later never changed the idle screen. So restarted, now getting "grub rescue>", now not able to boot my Win7 also. 

Tried with CD with different speeds, USB bootable... No success. Can any expert help me?

---

### Post by manickaselvam on 2011-05-30
Oops... again i tried with different CD with 10x speed.... I got the different error.!!!

ata_id[266] : HDIO_GET_IDENTITY failed for '/dev/sro'

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system!!!

but i have downloaded the Live image from [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
 :(

---

### Post by coffeecat on 2011-05-30
> **manickaselvam said:**
> 
Then everything went fine with the installation.

Maybe, maybe not. A jump from 9.04 to 11.04 is not supported and unlikely to work. You should have gone 9.04 > 9.10 > 10.04 > 10.10 > 11.04, which would have been difficult because both 9.04 and 9.10 are unsupported now and you would have had to use the old-releases repository.

I rather fear that you may have to make a fresh install, but before you think of doing that, boot up with your bootable 11.04 USB and choose "try Ubuntu" to get to the live desktop. Now go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there to download and run the boot info script and then post the contents of the RESULTS.txt file. Please remember to enclose it between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the # icon on the message toolbar for this.

---

### Post by coffeecat on 2011-05-30
> **manickaselvam said:**
> Oops... again i tried with different CD with 10x speed.... I got the different error.!!!

ata_id[266] : HDIO_GET_IDENTITY failed for '/dev/sro'

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system!!!

but i have downloaded the Live image from [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
 :(

OK, you posted just before I posted my last post. What exactly are you trying to do? I read your last post that you had upgraded your 9.04 installation with a live 11.04 USB. Now this sounds as though you are trying and failing to boot a live CD. Were you able to boot the live USB?

---

### Post by manickaselvam on 2011-05-30
Thanks [coffeecat]("http://ubuntuforums.org/member.php?u=129087"). I thought USB boot would be problem so tried with 11.04 (24x speed) it was telling the above error. After going through the forum i decided to write the disc with lower speed. But still getting the same kind of error.

I used Win7 & Ubuntu9.04. Due to lazzzy i haven't updated the ubuntu. Only yesterday had time to download and update 9.04 to 11.04. Eventhough i read about "9.04 > 9.10 > 10.04 > 10.10 > 11.04" but to have a try i have done this. !!! :( now i stuck here.

---

### Post by manickaselvam on 2011-05-30
I could run this "[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)" Boot info script if the UBUNTU USB is running atleast... My Dell Inspiron Laptop doing like this....

1) USB Bootable
2) powered ON
3) Boot Menu
4) I hv selected "USB Storage Device"
5) Ubuntu pink Screen is running with those 5 dots...!!!
6) Then "black screen"!!!! - I have to restart it again then

So tried with CD, i got the above error...!!!

---

### Post by manickaselvam on 2011-05-30
I hope i mess up a lot. I use UBUNTU for last 3 yrs. But never had such situation. Even able to recover the grub loader previously. Don't know why not now...? 

I tried with UBUNTU 9.04 CD itself now... Everything was fine until be booting option... 

I gave "try Ubuntu"... But no action... again it is in the same page... not moving further...

---

### Post by coffeecat on 2011-05-30
Let's clarify some things. You've had Ubuntu 9.04 running OK on that machine before? But now neither the 9.04 live CD nor the live 11.04 USB boot to the desktop? Have I understood you correctly?

It could be that your machine will not run 11.04. Even though many people can run 11.04 without problems (myself included), there are reports of it not being compatible with some hardware. As far as the 9.04 disc is concerned - I don't know.

Which model Dell Inspiron is it? In particular, what graphics card?

---

### Post by manickaselvam on 2011-05-30
Yes Coffeecat, I use the Ubuntu 9.04 for the last one year without any issue along with Windows 7 as dual boot. 

I was trying to upgrade 9.04 to 11.04. Even though i have to do 9 to 10 then 10 to 11, but i run USB Bootable ubuntu 11.04 without installation from the existing ubuntu9.04. I was much happy Ubuntu11.04 looks good. Then tried permanent installation. It was keep running, i set up username password, timezone, partition location etc., after that it was never turned to restart or finish. So i reset the power. 

Now stuck with grub rescue>. Again i tried with the same 9.04, no success. Then tried 10.10, no success. Again tried 11.04... No. tried with both USB as well as live CD. Even tried to format with GPARTED, the same stuck.

It is Inspiron 1525 Dell laptop. Heatsink,Central Processor    Unit,Notebook,Unified Memory  Architecture,1525. Processor,T5750,2.0,2MB,Core  Merom,M0. 2 GB RAM.

---

### Post by coffeecat on 2011-05-30
> **manickaselvam said:**
> but i run USB Bootable ubuntu 11.04 without installation from the existing ubuntu9.04. I was much happy Ubuntu11.04 looks good.

I don't understand that. You can't "run" a bootable USB from an existing Ubuntu installation. You have to boot the USB.

Anyway, it seems that you were once able to run the permanent installation and you were able to boot up live CDs or USBs. But now each live USB/CD you try won't boot. It sounds as though something has happened with the hardware. I really hope not, but I can think of no other explanation at the moment.

One thing you can do. All of those 10.10 and 11.04 USBs and CDs you've prepared. Try booting them on different machines. I presume you have access to at least one other machine because you are able to post to the forum. If they work OK on other machines then at least you can concentrate on what might have happened with the Dell Inspiron. If they don't work on other machines, then you need to check the md5sums of the downloaded ISOs.

---

### Post by manickaselvam on 2011-05-31
Weaha...!!! Its full of my mistakes...!!! Earlier when i download the  ubuntu image there were 2 times power interruption / internet  disconnected but when the power resumes automatically it has continued  to download... I checked only the size of the image!!! It was fine. But  there were some file missing after checking the md5sums.

Also my laptop DVD drive was not working properly. Now i have downloaded  fresh copy of UBUNTU 11.04, verified the md5sums and done my installation. Thank god my Win7 also still available. Everything is fine now. Thank you very much  Coffeecat, for enlightening me.

Wonderful ubuntu...!!! Thanks to the forum.

---

### Post by coffeecat on 2011-05-31
Yes, it's a good idea always to check the md5sum of a downloaded ISO. It can save a lot of time in the long run. :)

I'm glad you've solved it. Good luck with your Ubuntu-ing!

---

### Post by pritam_par on 2011-08-10
This issue solved here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

