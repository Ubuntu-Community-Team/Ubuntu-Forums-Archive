---
title: "Can't get to install any version of Ubuntu - please help"
date: 2018-03-18
forum: Installation &amp; Upgrades
---

### Post by safinator on 2018-03-18
Hello everyone! 
I am a bit of a newbie in these issues, but would like to learn. My first step was to get Ubuntu installed, but I have encountered some problems for which I did not manage to find a solution so far. So this is how everything went in chronological order. 

WHAT IS THE PROBLEM
1. I have downloaded the Ubuntu 17.10 installer and Rufus software. --> OK
2. I have created a partition on the hard drive (100 GB) --> OK
3. I have mounted the ISO image on a USB flash drive with Rufus --> OK
4. In the BIOS settings I have set the USB as the primary source for booting. --> 
5. The Ubuntu menu has appeared as expected when booting the computer, and I first opted for the option of Checking the Disk. Before the screen of disk check appeared, a screen with a code blinked for a second. The test said there is no problem with the disk and I could press any key to proceed. But when I press any key, the same code that blinked before appears, and nothing can be done other than restart the computer. --> BAD
6. When the same boot menu appeared, I tried to directly install the Ubuntu without checking the disk. The same code blinked for a second before the Ubuntu's loading screen. There, the dots that show progress make one or two rounds, and get frozen, after which nothing happens at all. --> 

WHAT I HAVE DONE TO SOLVE IT
1. I have updated the BIOS for a newer version. The same thing happens again, but this time the code is like three times as short. 
2. I have tried installing the 16.04 version, but all the same happens again. 
3. I have tried using Linux Live to mount the ISO image. Yet again, all the same. 
4. I have tried to run the Ubuntu with Virtual Box, but it does not work. 

So, what can be done in this situation? Sorry if this is a noob question, but I really need some advice as where to move from now on. 

Thank you so much beforehand. 

P.S. Attached is the latest code after updating the BIOS[ATTACH=CONFIG]278986[/ATTACH]

---

### Post by safinator on 2018-03-18
Sorry, forgot to mention about the hardware: 

It is an MSI GE72 6QD Apache Pro laptop. i7, 16 GB Ram, GTX960M, 120 GB SSD and 1 TB HD.

---

### Post by Bashing-om on 2018-03-18
safinator; Hello; Welcome to the forum

Try this:
> 
<ubottu> A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a 
               black screen or show corrupted splash screen. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use 
               this parameter


[INDENT][INDENT]could be Yes[/INDENT][/INDENT]

---

### Post by safinator on 2018-03-19
Hello Bashing-om! 

Thank you for your advice - I will definitely give it a try! 

Should I try out the [B]acpi_osi=? 

[/B]Will it will it work even if the black screen with that code blinks for a second before the Ubuntu loading screen appears while installing or trying to run it without installation? 

Thanks

---

### Post by safinator on 2018-03-19
Could it be related to the fact that my Win10 is 64bit, and I have downloaded the 64bit version of Ubuntu? What I mean, is that on the website it says that the 64 is meant for those processors based on AMD, and mine is Intel. --> [http://releases.ubuntu.com/16.04.4/](http://releases.ubuntu.com/16.04.4/)

---

### Post by kc1di on 2018-03-19
The 64 bit should work in fact it's the only one that will likely work if your using UEFI boot. 
The problem with the black screen is the Nvidia video card you have.  You need the nomodeset option and once you get it up and running you'll need to install the correct nvidia driver for your card by going to the driver manager and installing the recommended driver. good luck. 
This [Ask ubuntu]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") post will be of help.

---

### Post by safinator on 2018-03-20
Thanks a lot for the information! Unfortunately, yesterday I did not have the chance to try out the solution of nomodeset. I did update the Nvidia drivers though - hope it will help somehow.

---

### Post by safinator on 2018-03-20
Hi guys! 

Sorry to be a pain in the tender part of the body, but I tried both things, and still get the same problem. I have updated my video card drivers, and nothing changed. Then I have tried to set the nomodeset at acpi_osi= , and still nothing has changed. The interesting part, is that the black screen with the code does not stay there all along, it just blinks for a second, but the installation process just freezes (the purple screen). The only time the black screen remains there to be seen, is after carrying out a disk check (which does not encounter any problems) and pressing any key. 

What else can be done? Feel so bad that my experience into the Ubuntu world is starting with so much difficulty (

---

### Post by kansasnoob on 2018-03-21
You may want to try and stop nouveau altogether using this boot parameter:

nouveau.blacklist=1 nomodeset

---

### Post by safinator on 2018-03-21
Sorry for the noob question - so in the Ubuntu's menu screen, I press E to enter a command line (the F6 does not respond there) and just type in the [COLOR=#000000][INDENT]nouveau.blacklist=1 nomodeset[/INDENT]


[/COLOR]
[COLOR=#000000][B] and then press ESC? 
Many thanks in advance![RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by Bashing-om on 2018-03-21
safinator; Hey -

Still hang'n with you.

Differentiate between the liveDVD/USB and the actual install.

F6 applies to the live environment .

In the install at the grub menu,  press 'e' for edit .
That brings up the boot parameter screen.
arrow down to the line similar to this "linux /boot/vmlinuz-4.4.0-116-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the desired boot term " -without the quotes-;
Might be a good thing to replace quiet splash such that the boot messages are then displayed . See if you can now spot error messages  as the system boots
ctl+x to continue the boot process.

[INDENT][INDENT]look'n for that reason why
[/INDENT][/INDENT]

---

### Post by safinator on 2018-03-24
Thank you guys for your continuous support - I really appreciate it and it is a real pleasure to deal with such people. 

However, the Ubuntu was still resisting to me, so I decided that I am losing too much time and energy with just the installation, and opted to go for Linux Suse for now - it got installed without any problems. Yet again, thank you for your support, and sorry for causing any inconveniences while helping me solve my issues. 

Best regards

---

### Post by kc1di on 2018-03-24
No problem, Hope you'll enjoy SuSE - But if you ever come back we will be here to help :)

---

