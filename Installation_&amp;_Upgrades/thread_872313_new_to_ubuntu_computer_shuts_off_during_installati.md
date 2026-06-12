---
title: "new to ubuntu computer shuts off during installation"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by hotrodsurfmomma on 2008-07-27
I am sorry if I seem like an idiot here, I have never used Ubuntu before:-( I hope someone can help me. 
I have been having too many issues with virus' on my laptop with xp and finally gave up and wiped clean the hard drive, I tried to reinstall xp but unfortunatly my copy is upgrade only. But I have been wanting to install ubuntu for awhile now, so this was a blessing in disguise. 
I have been trying to install the os all day and it seems to get to a different point every time and then shuts the computer down completly.  If i turn the computer back on it says no boot disc available then i have to restart the computer and go to the boot menu again. It will go to the menu where I can install it (from disc) however if I tri to run it it goes to a prompt that looks like DOS and i have no clue what I am supposed to type.

I have been able to enter the computer name and my full name several times just can never seem to get it to load the OS

If anyone has any ideas please help me.

---

### Post by salvador_luna on 2008-07-27
Try starting in safe mode form the live cd. I had that problem and wen i tried the option i could install it.

Edit: You may want to check [this site]("http://www.psychocats.net/ubuntu/index") and [this article]("http://linux.oneandoneis2.org/LNW.htm"). The first  one may help you solving some issues and the second one is to help you understand the way that linux works, so you don get mad :).

---

### Post by hotrodsurfmomma on 2008-07-27
Thank you for your resposne, How do I get to run it from safe mode? As I don not have any operating system on this laptop. I have a completly clean hard drive

---

### Post by salvador_luna on 2008-07-27
Well, insert your live cd and restart... select your language and y the botton of the screen there are some text. There you will see something like "other options" (sorry, i dont remember the text exactly). There you can select that option and try to start the live cd.

Sorry for my spelling... english is not my native language :)

---

### Post by hotrodsurfmomma on 2008-07-27
I get an error that says no root file system is defined... How do I fix this

---

### Post by salvador_luna on 2008-07-27
Well, i dont know what that error means... what are your specs?

---

### Post by salvador_luna on 2008-07-27
I found this in the forums, maybe it could help you:

[http://ubuntuforums.org/showthread.php?t=871719&highlight=root+file+system+defined](http://ubuntuforums.org/showthread.php?t=871719&highlight=root+file+system+defined)

For what i read, i assume that you could launch the installer in safe mod, right? if you deleted windows and there is nothing in your hard drive, i recommend you that, when you are in the partitioning screen, select the options that says something about "automatic: use entire disk", and do not try partitioning manually.

Hope it helps you

---

### Post by hotrodsurfmomma on 2008-07-27
argh I am sorry i do not know how to find the specs.. 
I keep playing around with it and i figured out how to change the root thing but  now I have a fatal error with the grub and I have no clue what this is
I am wondering if i should just borrow a copy a windows just to format the drive then install ubuntu from there. I have been working on this since about 8:30 this morning.
Thank you for all your help 

Well I am currently at a screen that

[! !] install the GRUB boot loader on a hard disk
Unable to install GRUB in (hd0)
Executing 'grub-install (hd0)' failed
This is a fatal error.

This is a Dell latitude laptop with 80gb hd and 512 mb RAM
I hope this information is enough to point me in the next direction if not please let me know how to get the information that you need to help me. I really am in over my head on this one
Thank you again
Valerie

---

### Post by salvador_luna on 2008-07-27
Im not an expert but have you check your cd? maybe is a bad image... try downloading it again and verify that your cd download is ok ([link]("https://help.ubuntu.com/community/HowToMD5SUM"))

Also, [this]("https://help.ubuntu.com/community/BurningIsoHowto") instructions on how to burn the cd may give you some useful tips (like burning it at a low speed).

Please tell me if it helps.


Edit: I found this searching your error in the forums: [http://ubuntuforums.org/showthread.php?t=838116&highlight=Executing+grub-install+(hd0)%27+failed](http://ubuntuforums.org/showthread.php?t=838116&highlight=Executing+grub-install+(hd0)%27+failed)
Posts #5 and #6 could help.

Also in this [thread]("http://ubuntuforums.org/showthread.php?t=785260&highlight=Executing+%27grub-install+(hd0)%27+failed"), post #9 could be a solution (yes, i know, this is something that must not happen)

---

### Post by hotrodsurfmomma on 2008-07-27
I followed all the steps on the ubuntu help section of the site like downloading the .iso writer and checking the md5sum (which honestly I have no clue what these even are) I am able to get to the main installiation menu and am re-partitioning the HD again under the automatic settings and every time I seem to get another step closer to this working!  It seemed to recognize that this is the only OS on the computer so I am crossing my fingers in hopes that by tomorrow my questions will be on how to navigate not install  :guitar:

Thank you so much for your patience and help
I hope I can get this working but I am burnt out at the moment, I have to get up for work in another 4 hours so I will call it quits for tonight.

I hope it will finish installing

---

### Post by salvador_luna on 2008-07-27
Im glad to help you! Hope it works now!

The md5sum verify that your download is ok. In this way, you reduce the posibilities of burning a bad file.

---

### Post by hotrodsurfmomma on 2008-07-27
So far so good It is installing software. ;)
Thank you again

---

### Post by salvador_luna on 2008-08-03
Please, if the installation was complete without errors, mark this thread as solved :)

---

### Post by ldgilman on 2008-08-03
You may have to change the boot order in the BIOS. Mine was originally set for Floppy then Hard Drive. I changed the order in my laptop (Dell) to CD then Floppy then Hard Drive.

---

