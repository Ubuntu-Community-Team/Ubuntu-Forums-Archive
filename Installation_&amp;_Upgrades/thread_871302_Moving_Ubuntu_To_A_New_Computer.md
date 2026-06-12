---
title: "Moving Ubuntu To A New Computer"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by JeremyTheGeek on 2008-07-26
As the title suggests im trying to move Ubuntu to a new computer. Im looking at ways of backing up all my applications, configurations and other data. Now here is my question 

Is there anyway to move/copy all of my installed applications/libraries to my new Hardy PC.

Ive tried aptoncd & creating an install script in synaptic but there is a snag. Aptoncd cannot find all of my packages (stuff from tarballs and the like) and the install script made by synaptic only installs packages that are found in the repos. I need all of the packages/libaries that are installed on this computer to be copied over to the new computer without making it unusable. 

Ive already backed up all of my data in my /home directory and need to know if there is anything else that i need to backup.

Any help would be appreciated. 

      -Germ

---

### Post by Pumalite on 2008-07-26
If you have an external, use:
[http://www.clonezilla.org/download/sourceforge/](http://www.clonezilla.org/download/sourceforge/)

---

### Post by JeremyTheGeek on 2008-07-26
If i make a image of my current system and then restore it on the new computer won't there be issues with the different hardware??

---

### Post by solitaire on 2008-07-26
There is a package that makes a 'live cd' of your current install. I can't remember the name at the moment. Basicaly it takes everything except your /home/ dir and there is also an option to make a backup of your entire system and make it an install dvd. So you can stick it in any new pc and run the install and a few mins later you got everything preinstalled :):)

---

### Post by Pumalite on 2008-07-26
> **JeremyTheGeek said:**
> If i make a image of my current system and then restore it on the new computer won't there be issues with the different hardware??
How different is your new computer?

---

### Post by JeremyTheGeek on 2008-07-27
New computer:
PDF LINK  >>  [https://images-na.ssl-images-amazon.com/images/G/01/00/00/01/71/94/80/171948090.pdf]("https://images-na.ssl-images-amazon.com/images/G/01/00/00/01/71/94/80/171948090.pdf")
+1 extra GB RAM

Old Computer:
256mb RAM
40 GB ATA drive
2.0 Ghz Intel Pentium IV (512 kb L2 cache)
15 (apx) inch CRT screen
intel AC'97 sound card
usb keyboard + mouse
CD-RW drive
floppy drive


   -Germ

---

### Post by Pumalite on 2008-07-27
I cannot assure you it will work, but you can try. The kernel is supposed to load the modules according to the hardware it faces, but it doesn't always work.

---

### Post by JeremyTheGeek on 2008-07-28
Assuming I do restore an image onto the different hardware. How do i install the Grub bootloader?

---

### Post by vadarfone on 2008-07-28
> **solitaire said:**
> There is a package that makes a 'live cd' of your current install. I can't remember the name at the moment. Basicaly it takes everything except your /home/ dir and there is also an option to make a backup of your entire system and make it an install dvd. So you can stick it in any new pc and run the install and a few mins later you got everything preinstalled :):)

If that works, that is brilliant.

That is EXACTLY what I am looking for.

I have Ubuntu pretty nicely set up on a 5400rpm laptop drive, but I want to install it as a dual boot on my old 7200rpm laptop drive.

The 7200rpm drive already has XP on it, so I will want to make a live CD from my current install and reinstall it on my new drive.

If I do this, will it transfer everything "as-is"?  

Basically, I cant be bothered to spend days setting ubuntu up again,and just want to be able to take everything as it is, as transfer it, making a dual boot in the process...

Any help on this would be excellent!

---

### Post by JeremyTheGeek on 2008-07-28
Ive done some more research and found remastersys. Remastersys is a way to create a liveCD/DVD of your existing system. 

Instructions are at >>  [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

use the repos from this thread >> [http://ubuntuforums.org/showthread.php?t=685911](http://ubuntuforums.org/showthread.php?t=685911)

My problem is that I only have 3GB left free on my /home partition. Is there anyway to allow remastersys to make the iso on a portable HD/iPod (80GB classic in disk mode). 

Remastersys can also be used to create CD/DVD for distribution minus the user data.

   -Germ

---

### Post by JeremyTheGeek on 2008-07-28
Edit: Double-posted

---

### Post by JeremyTheGeek on 2008-07-28
Found out the answer.

System >> Administration >> Remastersys Backup >> Modify remastersys config >> working directory >> <place for iso>

Q: will there be any issues if using a 80GB Pod classic (fat32 formatted) ?

---

### Post by solitaire on 2008-07-28
> **JeremyTheGeek said:**
> Ive done some more research and found remastersys. Remastersys is a way to create a liveCD/DVD of your existing system. 

Instructions are at >>  [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

use the repos from this thread >> [http://ubuntuforums.org/showthread.php?t=685911](http://ubuntuforums.org/showthread.php?t=685911)

My problem is that I only have 3GB left free on my /home partition. Is there anyway to allow remastersys to make the iso on a portable HD/iPod (80GB classic in disk mode). 

Remastersys can also be used to create CD/DVD for distribution minus the user data.

   -Germ



Thanks!! :D:D 

That's the package I was thinking of! My mind went a total blank in this thread :D:D

---

