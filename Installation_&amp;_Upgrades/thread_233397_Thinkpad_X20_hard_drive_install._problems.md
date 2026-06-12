---
title: "Thinkpad X20 hard drive install. problems"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by mazato on 2006-08-10
Having repaired my PC so many times in windowzz, I decided to try Linux(Ubuntu actually). so I'm learning lots of stuff. Well first thanks to every developer and person involved in such a cool OS  and those who give a hand to newbies like me.
Well I got me a Thinkpad x20 with a CPU of 500 MHZ, it only has 64 MB of RAM, but an upgrade( 256MB) it's on the way.Paid 100 bucks :D . It does not have floppy,cd-rom,neither an ethernet card (only a modem, so I can't install Ubuntu with a Live CD,Netboot,neither through floppies using old versions. I tried installling IN DOS mode when the laptop still had W98. but there were so many errors that I gave up. So I bought a 2.5" to 3.5" IDE adapter for the laptop hard drive and conect it to my desktop primary IDE interface, so I could run the live CD on Windowzz XP.I know how to set the BIOS so that it boots from the cd-rom and set the jumpers on it too(it does not need to be changed 'cause by default,it's already set as Master).The BIOS did not recognize the laptop hard drive (I also tried different settings with the jumpers, but nothing worked) but reading in other threads I found out that if I changed the laptop hard drive to the secondary IDE interface,it would work. And so, I changed it, ran the live cd, installed Ubuntu on the thinkpad hard drive and everything went without any glitch. When I tranferred the  2.5 HD to the laptop I knew it would not boot up of course, however, I think there might be some way to change some configuration file on the HD after installing Ubuntu in the desktop so it will boot in the laptop, or not? I was so pissed off that I decided to format the laptop HD, so I used one of the applications in System/Administration/Disks . After this I put it back in the laptop and now a Grub error pops up and frezes, it was # 22.

So my problem is, the only way to install Ubuntu is by using the ide adapter with the thinkpad HD connected in the secondary IDE interface (the one usually used to connect dvd-rom or cd-writers.

Please, anyone, what else can I do to be able  first: to boot up the laptop HD from the primary IDE interface as master? what makes the thinkpad HD being recognized in the secondary channel but not in the primary one?
and second: is there any way that I can change some config file in the thinkpad HD after using the working method explained before?

I do not want to give up on this 'cause I really like Ubuntu,besides I got this amazing Thinkpad(I know, I know only 500 MHZ) but it weights with battery only 3.5 pounds. That's the main reason. I could have saved money for a $500.00 new laptop now on sale, but I already have a wireless card hanging around and a new FREE OS.I do not want to pay anymore for buggy OS's like Miicro... WinHoles [-X

---

### Post by xozdude on 2006-08-16
I have the same laptop, and I booted to a live session with the CD-ROM in the Ultrabase X2 (Google it).  You might have luck with a USB CD-Rom, too.

---

### Post by mazato on 2006-08-16
Luckily I found an ultrabase on ebay, this is is going to be my last chance, if it doesn't work I'll be selling the laptop and the ultrabase, it it works I guess i'll sell only the ultrabase, he he!!
:)
tomorrow UPS will dropp it off!!
fingers crossed!!

---

### Post by michaeljking on 2006-08-21
I have just purchased the same laptop to run Ubuntu on, (It was shipped out to me today) I already have a Thinkpad T21 that I plan to use to load the OS by swapping hardrives then switch the hardrive back to finish, the T21 has a differnet graphics card so I think It will need configuration ftom the rescue mode!

I have not tried switching laptop hardrives before, 

When I used an hardrive adaptor to load xubuntu into an ancient toshiba ct300, (I switched it for the main hardrive on my Dell Pentium 3 desktop,) when I replaced the hardrive back in the laptop I was able to get the graphics running fine, though pcmcia support was missing,)

Before I tried installing Ubuntu I used The Gparted disk to blank my hardrive  of windows/old partitions, I seem to have better luck this way round, I still use the alternative install Cd to partitiion the drive though.

I am intersted to see hoe you go, hopefully i will try mine in a few days and report back!  
I am a big thinkpad fan, The build quality is great, it runs Ubuntu nicely(there is even a thinkpad option on the install disk)! and besides I dont like touchpads!

---

### Post by stani on 2006-08-21
You don not need the ultrabase, which might be a relative expensive option. I have installed Ubuntu on a thinkpad X24, so I guess it is similar. Just ask any friend with a laptop with a cd-rom to borrow it and put your harddisk in his computer. 
Install ubuntu and before it wants to reboot, put it back in your laptop. The xserver will not start, so login into the server and do:
```
$ sudo dpkg-reconfigure xserver-org
```
Good luck,
Stani

---

### Post by neverbeentospain on 2006-08-21
Have you tried booting from a USB pen drive?

---

### Post by michaeljking on 2006-08-22
Unfortunately this laptop doesnt boot from a USb, 
I managed to install ubuntu by switching its hardrive with a T21 thinkpad.

There are a few oddities that I need to look at, sound is a bit tempermental, the volume key buttons cause the laptop to slow down....might just be the laptop, it is 6 years old, 

I am using it now to write this.

---

### Post by michaeljking on 2006-08-23
With the X20 you need to add acpi=off to the grub boot list otherwise using the volume buttons cause the laptop to go and crash.

works fine now.

---

