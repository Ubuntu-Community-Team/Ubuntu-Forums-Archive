---
title: "Kernel alive, but no Ubuntu?"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by Junkuhn on 2007-09-17
Hello, 

First I'm completely new to the Linux system. I have NO experience at all, so treat me like a five-year old when explaining stuff... :) 

Now to my problem:

I installed Ubuntu 7.04 on a fresh disk. I used the alternate CD because when I tried to use the regular one I just got a "I/O error" messege when I pressed "start or install..."

Using the alternate CD the installation and partitioning went fine, but when I boot up my computer stops after telling me:

"kernel alive
Kernel direct mapping table up to 13000000 @ 8000e000" 

After this the screen goes black (not shutting off, but showing black pixels) but I can hear my HDD is working. 
I was told it problerly was a hardware problem, and was instructed to got othe GRUB menu during start-up and type in:

"noapic nolapic"

This didn't seem to work either but after some re-boots it loaded the login screen. I logged in and Ubuntu seemed to be working. I continiued to install my grafics card (nVidia 8800GTX) and re-booted.
This was the only time Ubuntu loaded.


It was a a whole new computer with completely new parts in it, so to see if I had some hardware issues I intalled XP on it(sorry) and it wiorked fine?


Is this a problem any of you have heard of before ? Hope someone can enlighten me abit.. :)


/Junkuhn

---

### Post by Junkuhn on 2007-09-18
I just downloaded the Live CD again and tried to boot from it; same resut... Even when I tried to run the "check disc" on it it told me.

"kernel alive
Kernel direct mapping table up to 13000000 @ 8000e000" 

and shows me black pixels.. 

/Junkuhn

---

### Post by RJARRRPCGP on 2007-09-18
Sounds like a hardware problem, especially if it works after rebooting more than once and then it's back to a black screen.

It acting unpredictable sounds like bad hardware.

What to point at?: 

The motherboard, processor, RAM and/or power supply.

---

### Post by Junkuhn on 2007-09-19
Well.. 

Hardware worked fine with XP 64 and I WAS in Ubuntu once, that is what confuses me. But now I tried getting the 32 bit edition of Ubuntu and it works like a charm. :) 

I'm running on a Intel Core2Duo "Conroe" 2,86 GhZ ( I think, nor sure about the clock though)
Is this processor too new for the 64 bit edition ? what do I miis out on by using the 32 bit? I heard that it only supports 3.8 GB of RAM?

Anything else ? 


/junkuhn

---

### Post by dabl on 2007-09-19
In the console if you enter ```
cat /proc/cpuinfo
``` you can see exactly what your CPU model is. Or you can look at it in the Admin>hardware information utility.

No, your CPU is not too new - I've been running (K)Ubuntu on a Core 2 Extreme for a year now.

I wonder if it's a video-related problem.  When you get that black screen, can you do Alt-F1 and get a text prompt? Or possibly Ctrl-Alt-F1.

---

### Post by Junkuhn on 2007-09-19
> **dabl said:**
> 
I wonder if it's a video-related problem.  When you get that black screen, can you do Alt-F1 and get a text prompt? Or possibly Ctrl-Alt-F1.

I was not able to get any response from the computer, but it sounded like it was loading Ubuntu (had no sound, but HDD was noisy)

As I said I got it working on the 32-bit system wich leads me to another problem:

I installed my nVidia 8800 gtx by using Envy and it went smoothly. It asked if it should update my xorg.config thingy and I told it to do so. I rebooted and everything was working fine. I had the nVidia menu and everything. Then a popup came telling me that I had 114 updates for my system so I downloaded them, and installed them. 

Now my problem starts:

After showing the Ubuntu loading screen (the one with the orange loading bar) it jumps to the terminal, the screen flashes 2 times and then it jumps to a blue/gray/red menu (like the text-based installer) telling me:

--------------------------------------------------------------
Failed to start the X server (your grafical interface).
It is likely that it is not set up correctly. Would you like to
view the x server output to diagnose the problem?


<Yes> <No> 
---------------------------------------------------------------

I press "yes" and a list with a lot of rubbish (in my eyes :) ) apears. 
At the bottom it says:

---------------------------------------------------------------
(EE) NVIDIA(0) Failed to load NVIDIA kernel module
(EE) NVIDIA(0)            ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal x server error
no screens found
---------------------------------------------------------------

I press "ok" to this and I'm set back inti the terminal and my screen says this:

----------------------------------------------------------------
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/79cb38b3-4422-4f11-9473-b6342bf647e5 = s
da5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/79cb37b3-4422-4f11-9473-b6342bf64
7e5
kinit: No resume image, doing normal boot...

Ubuntu 7.04 *computer navn* tty1

*computer navn* login:_ 
-----------------------------------------------------------------

Any ideas ? :)

---

### Post by kaamos on 2007-09-19
You installed a kernel module without using the package manager. When you then updated the kernel, the nvidia module was not updated and so is not available for the new kernel.

Login to the terminal (the command line thingy that you have after X has failed) and use the command
```

sudo dpkg-reconfigure xserver-xorg

```
to change the display driver from "nvidia" to "nv". The other way to do this is to edit the file /etc/X11/xorg.conf with a text editor (sudo nano <filename>). After the change is done, type
```

sudo reboot

```
You should then get a gui using the original driver shipped with Ubuntu.

---

### Post by Junkuhn on 2007-09-19
> **kaamos said:**
> Y
to change the display driver from "nvidia" to "nv". The other way to do this is to edit the file /etc/X11/xorg.conf with a text editor (sudo nano <filename>). After the change is done, type
```

sudo reboot

```
You should then get a gui using the original driver shipped with Ubuntu.


I made the changes, but how do I "save" then and exit the file?

---

### Post by kaamos on 2007-09-19
If you used the text editor - ctrl+o and then ctrl+x saves the file and exits the program
If you used dpkg-reconfigure - just complete the wizard, it saves all the data when it is finished

---

### Post by mschmoelzer on 2007-09-19
> **Junkuhn said:**
> I made the changes, but how do I "save" then and exit the file?
In the nano editor, press [CTRL + O], then [Return] to save the changes to the file, then [CTRL + X] to exit the editor

---

### Post by Junkuhn on 2007-09-19
ok thanks guys... Gonna give it a try. :)

---

### Post by Junkuhn on 2007-09-19
yay! it works! 

Thanks guys!

---

### Post by zerooooooooooooooo1 on 2007-09-24
> **Junkuhn said:**
> Hello, 

First I'm completely new to the Linux system. I have NO experience at all, so treat me like a five-year old when explaining stuff... :) 

Now to my problem:

I installed Ubuntu 7.04 on a fresh disk. I used the alternate CD because when I tried to use the regular one I just got a "I/O error" messege when I pressed "start or install..."

Using the alternate CD the installation and partitioning went fine, but when I boot up my computer stops after telling me:

"kernel alive
Kernel direct mapping table up to 13000000 @ 8000e000" 

After this the screen goes black (not shutting off, but showing black pixels) but I can hear my HDD is working. 
I was told it problerly was a hardware problem, and was instructed to got othe GRUB menu during start-up and type in:

"noapic nolapic"

This didn't seem to work either but after some re-boots it loaded the login screen. I logged in and Ubuntu seemed to be working. I continiued to install my grafics card (nVidia 8800GTX) and re-booted.
This was the only time Ubuntu loaded.


It was a a whole new computer with completely new parts in it, so to see if I had some hardware issues I intalled XP on it(sorry) and it wiorked fine?


Is this a problem any of you have heard of before ? Hope someone can enlighten me abit.. :)


/Junkuhn



[COLOR="DarkRed"]Hello, I had the same problem, I couldn't boot UBuntu, fedora and it didn't matter if it was 32 or 64x version. I tried to do nolapic, noapic noapci, all the stuff and it didn't help at all, today I get angry and went to bios...  AND IT FINALY WORKS!!!!!

so, go to BIOS

than:

advanced -> integrated devices 

and make USB LEGECY SUPPORT (if you have got it in bios)    @@@@@@@DISABLE@@@@@@@@

when I did it, all versions of linux were going without any problem... 

So, try this, hope it helps... :KS

[/COLOR]

---

