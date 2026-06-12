---
title: "install ubuntu 9.10 without grub??? windows 7"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by MiMiK on 2009-11-16
hello there

well today i tried installing the new ubuntu. i installed it inside windows 7, but i didnt noticed an option to install it without grub. is there any way to install ubuntu without grub?? if i remember correctly in version 9.04 there was an option but cant seen to find it in 9.10..

since i wen ahead and installed it i have to go thru windows boot menu then grub and it's annoying..

any help or info.. i looked in google and only found one article that said that it not possible to do that but am a noob, am not sure

i would like to use windows boot menu since i got used to it wen i had 9.04..:)

---

### Post by wilee-nilee on 2009-11-16
9.10 does not play nice in wubi from what I have seen on the forums, that is why your seeing grub after the windows bootloader. You would be better with a dual boot.

---

### Post by MiMiK on 2009-11-16
> **wilee-nilee said:**
> 9.10 does not play nice in wubi from what I have seen on the forums, that is why your seeing grub after the windows bootloader. You would be better with a dual boot.
wilee thanks for the fast reply..

have another question is there a way to edit the grub menu to that in enter ubuntu quick so i dont have to wait the 10 secounds are up.. like put 1 second? or 0?

---

### Post by garvinrick4 on 2009-11-16
I have found no problem with using WUBI with Windows. 

You can edit Ubuntu boot time in Start-Up Manager ubuntu. Default at 2 nice to have 5.

In Windows msconfig  boot tab  there is a 10 second delay. Make it want you want.

Wubi can be a fine dual boot if you use it correctly and maintain your machine.
The same as any other system.  It is fantastic to learn on because it is easy to
uninstall in Windows and reinstall with disc you keep handy. Takes 12 minutes to
reinstall. If you want to have fun with it and not worry about destroyer your other distro.
it is nice. Only way I could learn is to experiment and figure out what is going on. If you
want to repartion later and have a quad boot go ahead nice to know what you are doing first.

---

### Post by wilee-nilee on 2009-11-16
> **MiMiK said:**
> wilee thanks for the fast reply..

have another question is there a way to edit the grub menu to that in enter ubuntu quick so i dont have to wait the 10 secounds are up.. like put 1 second? or 0? 

The post above me may be correct but it is a personal opinion not what most people on the forum would say, other then trying out a distro. Ubuntu does run slower in wubi, and if the W7 fails you are out 2 operating systems. 

I use startup manager in a dual boot you can change the time out in it, it is in synaptic, I have never used it in a wubi setup though. Also with having your Ubuntu inside of windows you could possibly pick up a infection that wont affect Ubuntu but could migrate to W7. There are so many reasons why dual booting is better, another is you can access the W7 partition from Ubuntu if needed. So if you like Ubuntu and are going to use it the best use is dual booting and it is an easy process.

The dual boot will fix the slower start up, and the time out and the default boot can be set with startup manager.

---

### Post by darkod on 2009-11-16
Something to add to the above. You asked about not installing grub. That is possible but I'm not sure it will work.
When you are installing ubuntu, on the last screen before clicking Install there is button Advanced. In advanced options you can select on which drive grub to be installed if you have more than one, and there is a tick box not to install grub at all.

BUT... I am talking about proper install, not wubi. Wubi is something like virtual ubuntu, installed like windows app, you have it in add/remove programs after. It is like a test environment to get familiar with ubuntu and see what you like and what you don't. In the proper install, the way ubuntu is meant to work, I am not sure windows bootloader can even boot any type of linux. So if you don't install grub what will boot it?

Wubi puts an option for ubuntu in your windows bootloader, like a virtual one, that's why you see grub afterwards too, otherwise it would be either windows bootloader or grub.

When you do the proper install and don't install grub I don't see what would boot ubuntu. Maybe coz I never tried. :) I am not saying it impossible, I just never heard about it.

---

### Post by Mark Phelps on 2009-11-16
> **darkod said:**
> ...In the proper install, the way ubuntu is meant to work, I am not sure windows bootloader can even boot any type of linux. So if you don't install grub what will boot it?
Correct -- MS Windows can not directly boot Ubuntu.  You can install GRUB4DOS in MS Windows -- but that is a derivative of GRUB.
> When you do the proper install and don't install grub I don't see what would boot ubuntu. Maybe coz I never tried. :) I am not saying it impossible, I just never heard about it.
You have to use GRUB or LILO, or some other Linux-compatible boot loader.

---

### Post by dandnsmith on 2009-11-16
However, its worth noting that you can get the Windows boot to cooperate in booting ubuntu, by saving the code for the bootloader as a file which the Windows boot invokes - I have a couple of PCs set this way (to avoid problems when installing Windows or repairing it)

---

### Post by garvinrick4 on 2009-11-16
To get Sam, Joe, Ma and Pa to give Ubuntu a whirl and enjoy Ubuntu WUBI is the least
intimidating of the installs. It is fantastic to learn Linux with without Ma and Pa having to
worry about partitions and grub. Use WUBI if you are getting into Linux and enjoy it and
learn. Read Forums to learn, use Google and make Post's here when you need to know
something. Ubuntu users are a very helpful lot they remember hence where they come and pass it down.


WUBI is a personal opinion and one that I believe is correct. After one learns the ropes to
Linux then create a seperate partition and move forward in your skills.

---

### Post by riverwall on 2010-03-17
> **MiMiK said:**
> wilee thanks for the fast reply..

have another question is there a way to edit the grub menu to that in enter ubuntu quick so i dont have to wait the 10 secounds are up.. like put 1 second? or 0?

A good way is installing a rack (as Kingwin) with a key to enable or disable the hard drive inside the rack, and qhen I installed Ubuntu I disconnected my hard drive of windows 7 and I did it as standalone, the I changed the order to boot in setup bios, when I want to run windows 7 I disable my Ubuntu Hard drive but when I want Ubuntu its start first by bios. 
P.D.
Excuse my language I don't speak English.
Manuel Muro :P

---

### Post by uRock on 2010-03-17
I recently did work on my mother-in-law's system where I wish it had the capability to adjust the BIOS to do that.

---

