---
title: "Extremely unusual problem, please help"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Elite Override on 2011-06-01
Hi everyone, I'll start by giving you the machine specs:

Current OS: Windows 7 Pro x64
2.8 Ghz dual core pentium (E550 IIRC)
2 GB Ram
Around 50 GB free space on drive.

So I wanted to dual boot win 7 and ubuntu (10.10 originally, but also tried 11.04 due to this problem. Both 64 bit.)

I have done this previously, about 2 years ago without problems. However, when I live boot or install from the cd the following happens:

Usual boot sequence asking my language and then showing the two load screens. When it has finished loading I see what appears to be a very distorted/fragmented screenshot of what my Windows OS looked like before I shut it down to boot into linux. 

I took a picture with my phone (I decided not to use image tags since it's fairly big):
[http://hashcookie.net/uploads/ca347d45b6_01062011.jpg](http://hashcookie.net/uploads/ca347d45b6_01062011.jpg)

You can see bits of the windows taskbar and my wallpaper. The system is totally unresponsive when it reaches this point, it is just a static image. There is no indication on the screen that ubuntu ever loaded after its loading screen.

So here is what I thought:

1. The iso can't be faulty since I tried both 10.10 and 11.04 on various other computers as well.
2. I had originally booted from a flash disk and thought that it might have caused the problem. So I burned 10.10 to a cd and got the exact same results.
3. I tried live mode, persistent mode, install and they all give the same results.

Also, the image always seems to be up to date, if I change the wallpaper in windows, I get a distorted version of it when booting ubuntu. Also note that there are no screenshots like this saved on the drive. I always shut down windows (not using hibernation or sleep) so I cannot understand how ubuntu can retrieve such an image?

This means that I can't install ubuntu at the moment...so please help. I have no idea what to do now.

---

### Post by Quackers on 2011-06-01
What graphics card are you using?

---

### Post by mörgæs on 2011-06-01
Posting with an exact and descriptive title will give you more answers.

---

### Post by Elite Override on 2011-06-01
> **Quackers said:**
> What graphics card are you using?

Nvidia 240GT, 512mb.

Btw: Changed title, sorry about that.

EDIT: I changed the post title, but I see there is no way for me to change the thread title. Would someone with the correct permission please change it?

---

### Post by Quackers on 2011-06-01
You may need to use a boot prompt. Please see the link below for details.
It is likely that the "nomodeset" one will work for you. If it does, select "try ubuntu" to load the live desktop then you can install the system from the desktop icon.
If you need the nomodeset option to boot the live cd you will also need it the first time you boot the installed system. 
All necessary details are in this link
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Elite Override on 2011-06-01
> **Quackers said:**
> You may need to use a boot prompt. Please see the link below for details.
It is likely that the "nomodeset" one will work for you. If it does, select "try ubuntu" to load the live desktop then you can install the system from the desktop icon.
If you need the nomodeset option to boot the live cd you will also need it the first time you boot the installed system. 
All necessary details are in this link
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thank you so much, I'll take a look and report back :D

---

### Post by Elite Override on 2011-06-01
> **Quackers said:**
> You may need to use a boot prompt. Please see the link below for details.
It is likely that the "nomodeset" one will work for you. If it does, select "try ubuntu" to load the live desktop then you can install the system from the desktop icon.
If you need the nomodeset option to boot the live cd you will also need it the first time you boot the installed system. 
All necessary details are in this link
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I've just tested it and it works, thank you.

I am still wondering why I got a screen showing windows and where it came from though. Does the graphics card store it? It does seem unlikely though.

---

### Post by Quackers on 2011-06-01
I don't know why that may be.
Glad it worked. Happy Ubuntuing :-)

---

