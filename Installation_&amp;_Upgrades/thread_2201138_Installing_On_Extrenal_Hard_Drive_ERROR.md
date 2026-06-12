---
title: "Installing On Extrenal Hard Drive ERROR"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by Antonio_Patterson on 2014-01-22
I have installed ubuntu and i have installed the files and used Universal-USB-Installer-1.9.5.2 to do that. I have a WD Passport (999GB). I have a Dell Latitude D610 running windows xp and this computer has 1.99GB of ram. I started the computer and did F12 and went down to usb storage device. It just showed a line appearing and dis-appering.:lol:](*,) I am a 15 yr Old boy ! :) Im proud that im so tech savy !! :) Sooo please help me if you can.

---

### Post by Bashing-om on 2014-01-22
Antonio_Patterson; Hi ! A Warm welcome to the forum.

In essence what you are saying is that you have installed ubuntu onto your system and now it will not boot ? 

Like maybe grub ( GRand Unified Bootloader ) did not install where bios expects it to be ?

Let's look at the drive to see what partitioning exist:
Boot up from the liveUSB -> try ubuntu mode-> activate a terminal and;
Post the output of terminal code:
```

sudo fdisk -lu

```
Just to make sure the install is there, then we can know better what is going on
And we will direct you to (re-)install grub - if that is deemed the corrective action.

[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Antonio_Patterson on 2014-01-22
Wait what. I have no way of getting into the linux command prompt. I know alot of commands because i use a vps. Sooo please tell me step by step what to do. I just went to My Computer and went to the drive and nothing is there !! (BTW i have a ubuntu theme on my xp ) [IMG]http://imgur.com/cPFBC5M[/IMG] ( If that picture doest work --> [http://imgur.com/cPFBC5M](http://imgur.com/cPFBC5M) ) I didnt name it locla **** "i" It was called "alot of space" lol domt judge me. After i rebooted the pc the first time after trying to boot ubuntu it was called Ubuntu Installer i think or something ! Now when i go inside of it i see --> [http://imgur.com/05YXFMG](http://imgur.com/05YXFMG) [IMG]http://imgur.com/05YXFMG[/IMG]. Now i dont know what to do.

---

### Post by Bashing-om on 2014-01-22
Antonio_Patterson; OK .....

Keep in mind that I am Windows' illiterate and I am happy that way. We are going to work with ubuntu tools, you need to learn anyway so.

How did you install ubuntu ?
What installation medium do you have,

just so I can direct you to a terminal. If this turns out to be a WUBI install, again I am illiterate, and going to keep it that way.
But I will
[INDENT][INDENT]help as much as I can
[/INDENT][/INDENT]

---

