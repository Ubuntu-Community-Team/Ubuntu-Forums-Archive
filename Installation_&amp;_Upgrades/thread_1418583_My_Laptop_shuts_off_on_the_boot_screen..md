---
title: "My Laptop shuts off on the boot screen."
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by NT2015 on 2010-02-28
OK I have tried several ways of doing this and all have the same result. I have tried booting Ubuntu off of a USB flash drive, nothing. Tried installing from a flash drive, nothing. Tried booting from the CD, nothing. Tried installing from the CD, nothing. What happens is i get the boot menu, not Grub the one where it asks "try ubuntu with no changes to your computer" or to "install" weather i pick try or install i get to the white flashing ubuntu logo and it sits there for about 30seconds and then my laptop shuts off. This happens every time. And i know the disk is good, its the same disk i used to install it on my desktop. 

Trying to install Version 9.10 Karmic x64

Please help. I wouldn't call my self a complete noob, but I am still fairly new to using Linux.

Specs:
Acer Aspire 5920 (not the one with the nVidia card) :(
CPU: Intel Core 2 Duo 1.8GHz
RAM: 3GB 
GFX: Mobile Intel 965 Express

---

### Post by darkod on 2010-02-28
At the main menu, hit F4 and select Safe Graphics. Then select Try Ubuntu.
Can it load the live desktop like that?

---

### Post by NT2015 on 2010-02-28
Sorry, actually i forgot to mention, I did try that as well. And it didnt work. ](*,)

---

### Post by NT2015 on 2010-02-28
UPDATE

I just tried the 32-bit version, just to see if it would work. I still have the same problem. I am currently running Memtest to see if maybe there is a problem with my ram, even though i currently run Windows 7 fantas.....well about as good as Windows can run.;)

---

### Post by RJARRRPCGP on 2010-02-28
> **NT2015 said:**
> it sits there for about 30seconds and then my laptop shuts off. 

That reminds me of some code that Windows 95 and Windows 98 have (but not Windows 2000 and XP) that when it can't find registry files or can't find VMM32.VXD, it then displays an error message and shuts off the PC, literally sends a power off command. Or it displays an error message and when you press enter, the PC shuts down. LOL.

(Note that it's during the real early init stage of Windows)  

(A blue screen does not trigger a power down) (It's when the Windows loader encounters a missing or corrupted VMM32.VXD or one of the other boot files)

---

### Post by NT2015 on 2010-02-28
OK Ive made some progress. I was in a bit of a hurry because I promised my girl she could use the laptop tonight (it currently still has Windows 7 on it). But I did some barbaric trial and error, at the menu i hit F6 and enabled everything in the list, (like i said, in a hurry, normally i would have done it one at a time). I then proceeded to boot ubuntu live from the CD, and with pleasing results. Ubuntu booted right up :D, the only problem i had, and its not really a problem, was that I'm not sure if my WiFi works. It found the propriatary driver for it, but because i had to restart the computer to activate it there was really no way to test it until i do a full install.  So tomorrow after work, i will narrow it down to what option allowed me to boot and will post the results. I do have one question though, when i select a option from the F6 menu and then proceed to do a full install, will it install ubuntu with the selected options? or will it just boot the installation with those options?

---

### Post by NT2015 on 2010-03-03
OK so problem solved. I figured i would post how to fix this even though nobody seems to be reading this anymore anyway. Maybe it will help somebody. 

I had to boot with "nolapic" 

To do this:
-At GRUB menu select your ubuntu installation and press "e"
-Go down to the line that lists your kernel and add nolapic to the end of that line
-press Ctrl-X to boot in to ubuntu. 

(Now thats only a temporary fix, as soon as you reboot that option will be erased and youl have to do it again. Keep reading to set it permanately in ubuntu 9.10. This process will be different if your running a version older than 9.10.

Make it stick:
Open a terminal and type this
gksudo gedit /etc/default/grubok now look for this line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"change the text in that line to this
GRUB_CMDLINE_LINUX_DEFAULT="noapic=off quiet splash"Click save and close gedit
now go back to your terminal window and type
sudo update-grubnow all should be right :)

Now i didnt make the tut on how to make it permanent. Many thanks to Wojox for his post in this topic [here]("http://ubuntuforums.org/showthread.php?t=1324401"). I just simply took his tut and made a minor change so it would suit my problem. I hope this will help somebody because it took me two frustrating days to get this sorted out.

---

### Post by sam.reader on 2010-03-03
Your boot.ini file is most probably missing.
Try to go through the C drive from another hard disk and for the boot.ini file
If its missing try to get it rectified by a professional.
Using the boot.ini file from another hard disk won't help your cause.
Report back.

---

### Post by GeoffreyBernardo on 2010-03-03
> **NT2015 said:**
> OK so problem solved. I figured i would post how to fix this even though nobody seems to be reading this anymore anyway. Maybe it will help somebody. 

I had to boot with "nolapic" 

To do this:
-At GRUB menu select your ubuntu installation and press "e"
-Go down to the line that lists your kernel and add nolapic to the end of that line
-press Ctrl-X to boot in to ubuntu. 

(Now thats only a temporary fix, as soon as you reboot that option will be erased and youl have to do it again. Keep reading to set it permanately in ubuntu 9.10. This process will be different if your running a version older than 9.10.

Make it stick:
Open a terminal and type this
gksudo gedit /etc/default/grubok now look for this line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"change the text in that line to this
GRUB_CMDLINE_LINUX_DEFAULT="noapic=off quiet splash"Click save and close gedit
now go back to your terminal window and type
sudo update-grubnow all should be right :)

Now i didnt make the tut on how to make it permanent. Many thanks to Wojox for his post in this topic [here]("http://ubuntuforums.org/showthread.php?t=1324401"). I just simply took his tut and made a minor change so it would suit my problem. I hope this will help somebody because it took me two frustrating days to get this sorted out.

Thanks alot for posting this! I fixed a similar problem that I had with 9.10 not booting.

There are so many people it seems with this problem that this post should be made a sticky in this forum as well as in the Beginner's Talk Forums.

---

