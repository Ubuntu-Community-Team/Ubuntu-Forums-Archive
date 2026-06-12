---
title: "Every time i install ubuntu..."
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by ethismos on 2017-01-21
I keep wondering why it is so damn hard.

I had a PC running ubuntu for 5 years at university. Then run it for 2 more years at home, now i get at a new place and have to install again. I do not get why it is so damn harder everytime.

What happened this time:

1) 2 Keyboards and 2 mice all not working. 10 reboots and 50 plug-ins at different usb ports later for no apparent reason a mouse works, i have to do the whole process with on screen keyboard.
2) One partition could not be formated, spend quite some time at another pc, found solution (formatting it from live cd before installation because for some reason that formatting is better...).
3) 80% of installation finished, grub error, find solutions at another pc, hours later with nothing working (including formats, new installation disk, different partitioning etc) i get lucky again with a combination of boot at one disk, root at another, home with swap at a third one and install finishes. SImply erasing any of the 3 disks and installing there got me errors.
4) I get into ubuntu the next day, one hard disk (my SSD ofc) is not recognised, cant find a working solution.
5) My mouse still works, my keyboard doesn't, try everything while typing with ON SCREEN keyboard, still not working.
6) Ethernet recognised, not working, giving me error messages every 30 seconds. Can't get drivers or anything, i try to fix it (disable ipv6, do many commands with terminal that i half understand to disable random stuff at network manager, reset network and pc 50 times, try every solution from 12.04 version and onward) nothing happens.
7) My SSD is now invisible at BIOS. No one knows why.
8) I use CD for an internet solution i find, i reboot with terminal, i get a "remove cd and press enter", stuck because i have no keyboard... 
9) Took me 30 minutes to install my old windows 7, everything works (with 15 minutes for drivers update).

First time i dont have ubuntu at my PC in 7+ years.

I have no idea how someone relatively new could go through that process (which included a second fully working pc) and even consider using ubuntu again. I am not an expert but i have used ubuntu a lot, i programmed with ubuntu, i played games with ubuntu, i had fun altering my UI at ubuntu, i did my university work with ubuntu but every time i have to go through installation i get frustrated and can't imagine how someone with no experience  or help can get through this error process.

Deeply dissapointed.

---

### Post by RobGoss on 2017-01-21
Hello and welcome, You don't mention anything about your hardware you're using it will help other to determine what might be the problem

If I'm reading your post correctly you are using Ubuntu **12.04 **version correct? or at least you give me that impression if this is the case that distribution is no longer supported and that maybe were your problem starts. Trying using a distribution that is current like **16.04 LTS **and I'm sure you're problems will go away 

You can see this chart that will show you the support length of Ubuntu's distributions [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Best of luck

---

### Post by Autodave on 2017-01-21
I do not have an answer for you and I feel your pain. I am wondering if you only tried one install disk/USB or only one download of the program: maybe you have a bad download?

When 16.04 was released, I downloaded both the 32 and 64 bit versions of Xubuntu and proceeded to do all 13 machines here. They ranged from an ASUS EEEPC900 (9" netbook, 900 mhz) all the way up to a 3.4 quad core with a 4 gig Nvidia card. *Every* install went w/o any problems at all. Mixture of conventional HDs and SSDs. Several machines w/multiple HDs.

---

### Post by RobGoss on 2017-01-21
Hello and welcome, You don't mention anything about the hardware you're using it will help others to determine what might be the problem

If I'm reading your post correctly you are using Ubuntu **12.04 **version? if this is the case that distribution is no longer supported and that maybe were your problem starts. Trying using a distribution that is current like **16.04 LTS **and I'm sure you're problems will go away 

You can see this chart that will show you the support length of Ubuntu's distributions [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Best of luck

---

### Post by ethismos on 2017-01-21
I m using 16.04 but that is not the issue.

The issue is that for years the installation process is full of errors, at least from 12.04 that i remember frustrating me from the first time.

I have installed ubuntu versions with intel and amd processors (right now i have it at a laptop running i5 6300U if i remeber correct and trying to get it on a fx 8320 atm) and motherboards, i have used many graphics cards and many internet providers. I have never EVER had an installation process go smoothly, put the cd in, get installation done, get drivers, finish. First of all i have NEVER had internet working during installation, i might be that unlucky but it is in the process of 7 years from crappy 4 Mpbs dsl, to 24Mbps ADSL to 50Mbps Vdsl  with at least 4 different providers at 2 different countries.

This is not a find a solution post, i will find something in the chaos like i always do, but its damn frustrating now that i dont have much time to waste 3 afternoons to get an installation done because of the amount of errors when i can do the same with windows in 30-45 minutes.

I just got no idea how simple things like that are not fixed yet, ubuntu is wonderful, but it is SO DAMN HARD to install it every single time, even with above average knowledge and previous experience...

(Edit: I did use 3 different dvds during the installation, all seem to have the same issues, no keyboard, grub error, hard to partition one of the drives)

---

### Post by RobGoss on 2017-01-21
Is this the only machine you have Ubuntu installed on? I've just did a clean installation of **16.04 LTS** and it went as smoothly as expected with out any problems what so ever. I suspect it might be a** hardware **or **graphic card** problem. How does the live desktop run when you try it?

Most of my machines are Dells and Ubuntu runs pretty good on them

---

### Post by Autodave on 2017-01-21
I have run Ubuntu/Xubuntu for over 10 years now. 10 years ago, it was a pain. But, with each 2 year LTS release, I find it easier and easier. This year, not a single problem on any machine. That's why I am wondering if you got a corrupted download. Maybe, Ubuntu is trickier than Xubuntu: Xubuntu was my choice this time.

---

### Post by RobGoss on 2017-01-21
If you need to check the **md5sum ** this guide migh be of help
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ajgreeny on 2017-01-21
> **ethismos said:**
> I m using 16.04 but that is not the issue.

The issue is that for years the installation process is full of errors, at least from 12.04 that i remember frustrating me from the first time.

I have installed ubuntu versions with intel and amd processors (right now i have it at a laptop running i5 6300U if i remeber correct and trying to get it on a fx 8320 atm) and motherboards, i have used many graphics cards and many internet providers. I have never EVER had an installation process go smoothly, put the cd in, get installation done, get drivers, finish. First of all i have NEVER had internet working during installation, i might be that unlucky but it is in the process of 7 years from crappy 4 Mpbs dsl, to 24Mbps ADSL to 50Mbps Vdsl  with at least 4 different providers at 2 different countries.

This is not a find a solution post, i will find something in the chaos like i always do, but its damn frustrating now that i dont have much time to waste 3 afternoons to get an installation done because of the amount of errors when i can do the same with windows in 30-45 minutes.

I just got no idea how simple things like that are not fixed yet, ubuntu is wonderful, but it is SO DAMN HARD to install it every single time, even with above average knowledge and previous experience...

(Edit: I did use 3 different dvds during the installation, all seem to have the same issues, no keyboard, grub error, hard to partition one of the drives)
You have been asked several times what hardware you are having these problems on and have not really given an answer.

I certainly think it it worth checking the .iso file you used for the install, as there is a real chance something is wrong with that. You may have been incredibly unlucky, of course, but that seems a bit unlikely.  Maybe you are now using new hardware which boots to a UEFI system and you have booted the install medium in BIOS mode.

Give us details of the problems on a specific set of hardware, however, and we may be able to tell you why you are having such difficulty.
Like others who have posted here I can manage to install any of the *ubuntu on all my computers, a mix of BIOS and UEFI, in about 15 - 20 minutes.

I am sure the problem will be solvable, but we do need details, not rants about your difficulty.

---

