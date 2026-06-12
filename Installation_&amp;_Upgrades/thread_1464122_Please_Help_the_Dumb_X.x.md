---
title: "Please Help the Dumb X.x"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by Iviesaur on 2010-04-27
Hi i'm new to everything really. My friend showed me Linux and i love it. I have the Ubuntu Remix on my netbook. Now i'm trying to download 9.10 for my pc. Its a compaq and i seriously don't know whats up. My friend burned the cd said it was made right. Then i went into my BIOS made CDR the top thing for the boot order and nothing. I can't get the install screen to even show up. Then my second attempt was to make a bootable flash drive. I made one using my netbook. It said it was made perfect. I placed it into my computer, went into the BIOS made removable thing the top prioriety in the BIOS and still no download screen. I have no idea what to do. Any help would be most greatly appreciated. Thank you. Sorry if some of that makes no sense. 

Also i used WUBI to install 9.10 i now realize that caused me to install Ubuntu along side Windows XP. Is there a way to get rid of windows while keeping my Ubuntu cause that'd be awesome. My friend said to try a partitioner. But since i installed using windows wouldn't that mean that my version of Ubuntu is installed on the same partitioner as windows.

---

### Post by Iviesaur on 2010-04-27
Now i wait and hopefully some super awesome people help me out :D:guitar:

---

### Post by Iviesaur on 2010-04-27
now time to bump i guess :D

---

### Post by inputpower on 2010-04-27
There is a lot going on here. I will do my best to guide you to a good place. First read about partitioning and what that means. GParted is a great tool and super easy. If you READ the help files for Wubi it is a software partition sort of like a virtual machine. It would be a great start into Linux using Wubi. If you are more adventures I would suggest partitioning your HDD so you can have Windows and Ubuntu installed. This is good for many reasons. The CD you used can be tested by putting it in your CD drive and attempting to browse it via Windows, you nay have a bad image. I suggest ImgBurn to brun an ISO. There are many other things that can be done, but these are some suggestions.
-good luck

---

### Post by Iviesaur on 2010-04-27
i'm confused to your post. are you sayingi could remove windows or not. To be honest i don't want windows i don't like it. It makes my computer run slow

---

### Post by v1ad on 2010-04-27
download unetbootin 
get the iso image of the linux. 
plug in a usb flash stick. 
start unetbootin
click the option to install from iso.
direct it to your usb. start it.
then plug it into a computer that you need to install wonderful ubuntu.
reboot. 
go bios. 
make sure usb is the first bootable device
f10 save yes.
it will restart.
boot off usb.
start the installer again.
make sure u select whole disk. 
it will rewrite everything with that version of ubuntu.

---

### Post by inputpower on 2010-04-27
Yes you can remove Windows. You can also have both installed. Please reference:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
 This is good information that will help you understand how you can have more that one OS installed. But if you just want to install Ubuntu a good copy should work. if you put the disk into another computer you should be able to view the contents of the disk to verify if it is a good burn. Most computers have a key that you hit to get to the boot menu. For Dell it is mostly f12. If it is not working burn another disk.

---

### Post by Iviesaur on 2010-04-27
the iso for linux. Would that be the Ubuntu Iso already saved on to my bootable flash drive?

---

### Post by v1ad on 2010-04-27
you probably copied it over. that will never work. you need to make sure it is extracted properly and made bootable. unetbootin does that. usb devices won't boot without the proper files on there that is provided by programs similar to unetbootin.

basically the file on the usb drive cannot be an iso image.

---

### Post by Iviesaur on 2010-04-27
so should i redownload Ubuntu 9.10? straight from the internet again?

---

### Post by v1ad on 2010-04-27
no use the iso image u have. put in onto desktop of computer you are using. then use netbootin to extract it properly onto the usb stick.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Iviesaur on 2010-04-27
> **v1ad said:**
> no use the iso image u have. put in onto desktop of computer you are using. then use netbootin to extract it properly onto the usb stick.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'll try it but like i said before i tried to boot from flash drive and i couldn't it wouldn't go to the install screen

---

### Post by v1ad on 2010-04-27
yes but how did you put it on the usb drive. thats what matters.

---

### Post by gadolinio on 2010-04-27
Having both OSs would be wise, I think. But in case you want to get rid of windows anyway, you can do it. I don't know how to "extract" the ubuntu installation you have inside windows to a new one; but you could still do a simple backup of your files and then copy them to the new install.
You should backup two things: your home folder, and your installed applications.
Go to /home, and make a copy of your user folder. Then paste its content into your new user's directory.
Regarding installed applications, go to System--> administration--> synaptic package manager
 (in your current system, the one you installed with Wubi). In synaptic go to File--> save selections as...  That lets you create a list of the applications you currently have. Give a name to that list, and check the box that says something like "save complete state, not only changes"; THEN click save. Backup that file you've just created. In the new installation, open synaptic, go to File--> read selections, and use the list (you should have copied it into the new install).

---

### Post by gadolinio on 2010-04-27
> **v1ad said:**
> yes but how did you put it on the usb drive. thats what matters.
  That's right. If, for example, you just copied the iso file to the thumb drive, it won't work even with a good iso. Using an app like unetbootin you can make a liveUSB from which you can boot and then install ubuntu.

---

