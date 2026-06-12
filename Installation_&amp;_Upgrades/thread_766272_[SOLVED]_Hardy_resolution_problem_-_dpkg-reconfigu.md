---
title: "[SOLVED] Hardy resolution problem - dpkg-reconfigure xserver-xorg does not display re"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2008-04-25
Hi,
I have installed Ubuntu 8.04 Hardy Heron Desktop and having monitor resolution problem. It displays only 800x600 and 640x480 in menu System | Preferences | Screen Resolution.

[Exactly the same problem I have had in Ubuntu 7.10 Desktop](http://ubuntuforums.org/showthread.php?t=579784&p=3567236) and I have solved it using command:
sudo dpkg-reconfigure xserver-xorg

But in Hardy there is no video option in my xserver-xorg window. There are only setting about keyboard.

How to set resolution monitor to 1024x768?
Thanks,
Abcuser

---

### Post by wandalalakers on 2008-04-25
I noticed this too.  Do you think this is some sort of bug?

---

### Post by abcuser on 2008-04-25
Hi,
actually I have found out that command sudo dpkg-reconfigure xserver-xorg
returns warning and exits when all of default is seleted and after keyboard is selected.

Warning:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080425125856

Any idea how to solve this problem?

---

### Post by Killer Cop on 2008-04-25
I think I have a problem like this.

Normally I run 1152x864, but after I installed restricted nVidia drivers I can only set the resolution to max 1024x768.

Any ideas? And where's the good old Screens and Graphics?

---

### Post by bilbobagins on 2008-04-25
Hi folks, Itz not just you. I have the same problem, this was also apparent in the rc candidate that I tried a few days ago, hold tight and this bug will be resolved. go back to using the previous release, I for my part will continue to use  7.04.

---

### Post by rupierto on 2008-04-25
Take a look:

[http://ubuntuforums.org/showpost.php?p=4789536&postcount=110](http://ubuntuforums.org/showpost.php?p=4789536&postcount=110)

---

### Post by abcuser on 2008-04-25
Hi,
I have solved the problem!!!

1. I opened Terminal and enter command: sudo displayconfig-gtk
2. Screen and Graphics Preferences window opens on Screen tab I have selected "LCD Panel 1024x768" from Model drop down window
3. On the same window I have selected "1024x768" from Resolution drop down menu  and clicked on OK button.
4. Log off from Ubuntu and Log-in again.
5. New resolution has been started in 1024x768 mode and it is working fine.

Hope this helps to anyone out there.

Regards,
Abcuser

---

### Post by jrlrocks on 2008-05-28
THANK YOU!

That just bugs the CRAP out of me. I spent 2 days hunting around the web to find this incredibly simple solution. I know UBUNTU 8 is new and there are bugs... I'm not playing PC games just wanting to see my desktop! lol

Cheers!:guitar:

---

### Post by El_Perro_Perduto on 2008-09-09
I installed 8.04 on my Toshiba Sattelite AMD 64 laptop about two weeks ago and the OS was able to recognize my on board video card. I've been able to get around 1152x864 resolution @ 60Hz. The system has also recognized the non-open source ATI graphix accelerator. 

Problem is that video and graphics still don't come out as crisp as they used to when I was a Windows drone (not that I miss it!!).  Could anyone suggest a fix?:confused:  
Does reconfig'g xserver-xorg work for this?

---

### Post by kips80 on 2008-09-13
I had the exact same problem.  At first I thought it was a problem with the NVIDIA graphics card driver provided by Ubuntu Hardy Heron.  After a lot of "googling" I found this thread in the Ubuntu forums.  I used the exact steps 1-5 which abcuser outlined, except that I used 1280 x 1024 resolution (the max resolution of my LCD screen).  It worked perfectly (after logging out instead of restarting...oops) and now I can actually see my desktop!

Thank you abcuser! How do I add to your "thanked" count?  I'm new to this forum, so I don't know all the little tricks yet.

One general question I have for the Ubuntu developers: why is the dialogue box revealed by "sudo displayconfig-gtk" hidden in the first place?  Why isn't it under the "system" menu??  It was a lot of frustration to simply adjust my screen resolution.

---

### Post by zvacet on 2008-09-13
**System>preferences>main menu>other>screen & graphics**>check it and you will find it under app>other.

---

### Post by Alexander Grundner on 2008-09-20
> **abcuser said:**
> Hi,
I have solved the problem!!!

1. I opened Terminal and enter command: sudo displayconfig-gtk
2. Screen and Graphics Preferences window opens on Screen tab I have selected "LCD Panel 1024x768" from Model drop down window
3. On the same window I have selected "1024x768" from Resolution drop down menu  and clicked on OK button.
4. Log off from Ubuntu and Log-in again.
5. New resolution has been started in 1024x768 mode and it is working fine.

Hope this helps to anyone out there.

Regards,
Abcuser
I tried this suggestion (it's a good one), but it didn't work for me on my old HP Omnibook XE2 notebook (1024x768 16-bit depth). The way I got my screen working again, after installing Hardy over my Dapper install, was to use my old xorg.conf file (well sort of). What I did is I popped in my old Dapper Live CD and modified my xorg.conf file to have a DefaultDepth of 16 (it defaulted to 24 and only would display 800x600) restarted X to see if the change took -- it did. I then copied the contents of the modified xorg.conf file to a USB flash drive and pasted it all into the xorg.conf file in Hardy. Worked like a charm.... Hope this helps someone else.

---

### Post by boussetta on 2008-10-05
Hi guys;

I tried the solution by abcuser it worked fine but once i Log off it return back to lower resolution so I need to set it again through the <screen and graphic> option

---

### Post by Doncr on 2008-11-27
> **abcuser said:**
> Hi,
actually I have found out that command sudo dpkg-reconfigure xserver-xorg
returns warning and exits when all of default is seleted and after keyboard is selected.

Warning:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080425125856

Any idea how to solve this problem?

This is normal behavour. It is overwriting the xorg.config, and making a backup copy. 

If your xserver does not restart, you can

rm xorg.conf
mv xorg.conf.20080425125856 xorg.conf

don

---

