---
title: "Boot Loader Menu not visible - Dual HDD"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by Johnmala on 2012-01-01
To start I am new to Linux.

My computer has three hard drives.  
SDA: 160GB with WinXP
SDB: 40GB Ubuntu 11.10
SDC: 160GB Data

I installed Ubuntu on the 40GB drive and told it to put the boot loader on the same drive.  When I boot I do not get a boot loader menu.  After the BIOS screens I get an error message from my monitor that reads:
 

 1: Analog Input
 Cannot Display This Video Mode
 

 After about 30 Seconds the computer will continue to boot to Ubuntu.
 

 I can change the boot disk in BIOS and boot to the WinXP drive with no problems, and change it back and boot to Ubuntu as well.
 

 How do I fix the boot loader so I do not have to go into BIOS every time I want to change operating systems?
 

 Thanks
 

 John

---

### Post by jerrrys on 2012-01-03
Open a terminal and enter:

sudo update-grub

It should be that simple.  This command will let grub boot loader take over.

Also, from what I remember of windows you will need your windows restore cd to restore windows boot if you ever decide to remove ubuntu. Be sure you have one.

"Cannot Display This Video Mode" sounds like a separate problem

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+grub&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+grub&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Cannot+Display+This+Video+Mode&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Cannot+Display+This+Video+Mode&sa=Search&cof=FORID:9)

---

### Post by Johnmala on 2012-01-09
Thank You, the second link led me to this post:

[http://ubuntuforums.org/archive/index.php/t-1728905.html](http://ubuntuforums.org/archive/index.php/t-1728905.html)

It referenced an application called Startup Manager which is now outdated but when I looked at Startup Manager it recommended grub-customizer at:

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

When I changed the video mode on the advanced tab, my startup menu was visible.

---

### Post by jerrrys on 2012-01-09
Good catch, Im not a windows user and had forgotten that startup manager will no longer work on windows.

---

### Post by itpro007ca on 2012-01-09
> **Johnmala said:**
> To start I am new to Linux.

My computer has three hard drives.  
SDA: 160GB with WinXP
SDB: 40GB Ubuntu 11.10
SDC: 160GB Data

I installed Ubuntu on the 40GB drive and told it to put the boot loader on the same drive.  When I boot I do not get a boot loader menu.  After the BIOS screens I get an error message from my monitor that reads:
 

 1: Analog Input
 Cannot Display This Video Mode

I have alomost the same problem,except when my PC boots up I see  a floating gray rectangular box saying "input not supported(the same on 'shutdown')....as with your pc,after 30 secs,it boots into Ubuntu...the only clue I have is "unknown display",which in my case is a Emachines E180HV widescreen lcd(native: 1380
 

 After about 30 Seconds the computer will continue to boot to Ubuntu.
 

 I can change the boot disk in BIOS and boot to the WinXP drive with no problems, and change it back and boot to Ubuntu as well.
 

 How do I fix the boot loader so I do not have to go into BIOS every time I want to change operating systems?
 

 Thanks
 

 John

I have the same problem,but I get "input not supported" on bootup and shutdown(I posted about it in "Installations and Upgrades"  ...Emamchines E180HV LCD monitor)...probably because under systems/display it says "unknown." I not new to Linux and PCs,just Ubuntu(did try 8.04 once though.).

---

### Post by Johnmala on 2012-01-14
I am new to lunix so keep that in mind,  what was happening with my system is the display settings in Grub needed to be adjusted.  Since I am new and still learning I used a program to help me do that.  The link to that program is in the third post.  Once I changed the resulution for Grub my issues when away.
 
Godd Luck

---

