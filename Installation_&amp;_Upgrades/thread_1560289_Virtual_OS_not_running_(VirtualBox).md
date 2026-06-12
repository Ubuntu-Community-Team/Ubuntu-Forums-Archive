---
title: "Virtual OS not running (VirtualBox)"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by kalebka55 on 2010-08-24
Hi all,

I have installed 'VirtualBox' on my lucid lynx and want to load the Microsoft XP OS.  When I start the virtualization I get this message in the VirtualBox terminal---

"Fatal: Could not read from the boot medium! System Halted."

--- What could be the problem??

Assistance will be thoroughly appreciated!

---

### Post by blur xc on 2010-08-24
Do you have the windows xp disk in the computer?  And you have to tell VBox to use the disk to boot up.  I'm assuming you already created a blank .vdi file?  I don't recall exactly how it goes step by step.  I've only installed off of a disk once, every other vm I've made was from an iso file.

BM

---

### Post by gordintoronto on 2010-08-24
For this one program, it's better to get the program from its web site ([http://www.virtualbox.org/](http://www.virtualbox.org/)) rather than synaptic or Software Center. There are important feature differences.

---

### Post by kalebka55 on 2010-08-25
I am trying to boot from an .iso file I got from Microsoft website.  Also checked out the user manual, but my problem is not visible there.  

I keep on deleting the VM's and trying to install again- will my partitioning continuously be taken up/ or does the partition created for the VM return to normal?

???

---

### Post by wilee-nilee on 2010-08-25
The partitions are virtual when deleted they are gone.

So first the version of virtualbox your using doesn't have usb support the puel does it is on the web.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

To add the ISO to vbox, open it, click on file-virtual media manager and you will see this screen add XP to it.
[ATTACH]167462[/ATTACH]

If you have already done this you have to make sure that when you have started vbox at the top of the screen click on devices-cd/dvd and make sure the ISO is checked on.

---

### Post by kalebka55 on 2010-08-25
To add the ISO to vbox, open it, click on file-virtual media manager and you will see this screen add XP to it.

If you have already done this you have to make sure that when you have started vbox at the top of the screen click on devices-cd/dvd and make sure the ISO is checked on.


Thanks for your reply. So I downloaded the VirtualBox (VB) from the VB website.  I have done all that you said and still have the same problem.  I obtained the latest Microsoft XP service pack 3.ISO = (xpsp3_5512.080413-2113_usa_x86fre_spcd.iso) downloaded from the MS website.

Same 'FATAL'  message obtained.  Any other ideas?  What other 'bootable medium' could it be refering to?  would i need the actual XP CD and boot from there?

---

### Post by hudsonl on 2010-08-25
> **kalebka55 said:**
> 
Thanks for your reply. So I downloaded the VirtualBox (VB) from the VB website.  I have done all that you said and still have the same problem.  I obtained the latest Microsoft XP service pack 3.ISO = (xpsp3_5512.080413-2113_usa_x86fre_spcd.iso) downloaded from the MS website.

Same 'FATAL'  message obtained.  Any other ideas?  What other 'bootable medium' could it be refering to?  would i need the actual XP CD and boot from there?


Check **Machine** ... **Settings** ... **Storage** ... 
  
Make sure that the CD / DVD device is defined / pointing to your iso file ... 

See Example:
[IMG]http://www.larryhudson.net/tmp/VboxCD.jpeg[/IMG]

---

### Post by wilee-nilee on 2010-08-25
You say fatal mistake but when is this. Is this what your seeing.
[ATTACH]167513[/ATTACH]

If this is it then you have to mount the ISO by clicking on the devices tab in that window then click on the ISO in cd/dvd shutdown the window and restart.

---

### Post by gordintoronto on 2010-08-25
> **kalebka55 said:**
> So I downloaded the VirtualBox (VB) from the VB website.  I have done all that you said and still have the same problem.  I obtained the latest Microsoft XP service pack 3.ISO = (xpsp3_5512.080413-2113_usa_x86fre_spcd.iso) downloaded from the MS website.

Same 'FATAL'  message obtained.  Any other ideas?  What other 'bootable medium' could it be refering to?  would i need the actual XP CD and boot from there?

The XP Service Pack is not Windows, it is some updates to Windows. First you need Windows.

---

### Post by wilee-nilee on 2010-08-25
> **gordintoronto said:**
> The XP Service Pack is not Windows, it is some updates to Windows. First you need Windows.

You are correct. 

Thread starter do you have a actual XP install ISO, this sort of thing is your responsibility to know.

---

### Post by kalebka55 on 2010-08-26
> **gordintoronto said:**
> The XP Service Pack is not Windows, it is some updates to Windows. First you need Windows.


Thanks Gordintoronto- this makes A LOT more sense!!  apologies for my ignorance.

---

### Post by kalebka55 on 2010-08-26
> **wilee-nilee said:**
> You are correct. 

Thread starter do you have a actual XP install ISO, this sort of thing is your responsibility to know.


Apologies for my ignorance

---

### Post by wilee-nilee on 2010-08-26
Hey don't worry about it we all start somewhere in understanding. Try this version if you have a legit key.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by kalebka55 on 2010-08-26
[

---

### Post by kalebka55 on 2010-08-26
> **wilee-nilee said:**
> Hey don't worry about it we all start somewhere in understanding. Try this version if you have a legit key.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)


Thanks wilee-nilee!! Im not sure if i mentioned in my original posts, but my reason to load the VM is to load itunes so as to sync my devices.  I finally got wine to function and got to install itunes (halleluya)!!!  problem is that i cant sync the devices.  have you ot any solution to sync via the terminal?  or anything else?

Ive realised i will have difficulty using my usb with the VM so i am going to have to opt out of my previous mission! im pretty sure getting the legit key would be a mission in itself....probably having me to post more blogs for help.

But i appreciate your help nevertheless.  Thanks for your time!

---

