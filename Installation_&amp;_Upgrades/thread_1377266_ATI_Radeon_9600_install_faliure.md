---
title: "ATI Radeon 9600 install faliure"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by szabokarcsi on 2010-01-10
Hi!

I've got an ATI 9600 video card,  but I can't install it's driver. I have downloaded the **[COLOR=Black]ati-driver-installer-9.4-x86.x86_64.run[/COLOR]** file. But after installing (./ati-driver...) and restarting the screen stays blank, doesn't appear anything.

Because of this I have to reinstall the system for 3 times (Ubuntu 9.10). Okay, I'm not a Linux expert, I wish I could start Ubuntu in console mode, and uninstall the driver, but I can't.
I have been searching on the internet about the solution of this problem, but I didn't find anything useful.

The video card has a video output - I'd like to watch films on my TV (that's why I really need the catalyst).

(Nothing appears at *System -> Preferences -> Hardware drivers*. Is it normal?)

The card works correctly under Windows.

Please help me!

**[COLOR=SeaGreen]*It would be also very useful, if I somebody could tell me how to boot Ubuntu to console mode - in case of an other unsuccessful driver installation. I don't want to reinstall the system again...*[/COLOR]**

 &#9787;/
                       /&#9612;  | k 4 r 3 s z |
                       / \

---

### Post by szabokarcsi on 2010-01-10
Huh! No one knows?

 &#9787;/
                       /&#9612;  | k 4 r 3 s z |
                       / \

---

### Post by szabokarcsi on 2010-01-11
More information needed?

Or: if the driver doesn't work how can be uninstalled properly?

---

### Post by Mark Phelps on 2010-01-11
What you're doing simply will not work because there is no current ATI driver for your card that will work with Ubuntu versions newer than 8.10.  Doesn't matter where you get it from, or how you try to install it -- it simply won't work!

You need to remove the ATI driver and replace it with the only driver that will work -- the open source driver.

Instructions for doing this are in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by szabokarcsi on 2010-01-11
Yes... I noticed that! I had been trying to install that +#&@+"' Catalyst for about four hours, with no success.
I'm a little bit upset.

I have three questions:
[COLOR=DarkRed]
[/COLOR][COLOR=Red][COLOR=DarkRed] - With that open source driver will the video output works?
 - How can I completely and properly remove the previous driver?
 - Are there any chance that ATI will develop a proper Catalyst driver?[/COLOR]
[/COLOR]
And of course, thanks for the answer! I thought that noone can tell a word about my problem.

---

### Post by Mark Phelps on 2010-01-11
> **szabokarcsi said:**
> I have three questions:
 - With that open source driver will the video output works?
The open-source drivers tend to support only basic features/jacks.  So, special jacks like S-video, HDMI, and the newer Display Port tend NOT to be supported.  But the older standard video terminal cable jacks should be fine.
>   - How can I completely and properly remove the previous driver? 
Read the material at the link.  It tells you how to do that.
>  - Are there any chance that ATI will develop a proper Catalyst driver?
No -- they've said in every release since the one in May that they are not going to provide Linux driver updates for the "legacy" cards.

---

### Post by szabokarcsi on 2010-01-12
Hm... So if I want to watch films on my TV, I would have to install an older Ubuntu? Thanks ATI!

I tried to install the driver as written on the link above, but when I wanted to edit [COLOR=Red]/etc/X11/xorg.conf[/COLOR] file, it cannot be found!

So I couldn't continue installing.

WHY??? :(

And isn't there any driver for an older Ubuntu version what is suitable for mine?

(Ubuntu 9.10)

---

