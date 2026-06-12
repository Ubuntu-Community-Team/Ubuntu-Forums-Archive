---
title: "New user, Installing 64 bit to HP Pavillion dv6105us"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by plantluvver on 2006-10-23
Hi,
This is my first Linux install, though I have a Linux desktop that was given to me, preinstalled.  (I don't know a lot about Linux, or computing in general, since DOS.  So I am a little rusty.:rolleyes: )

I have a CD that I burnt that I used Bittorrent to download.  My PC is an HP Pavillion dv6105us (bought at Office Depot).  I have Windows on the Harddrive, as from the factory, almost.

I tried running the safe graphics option from the CD.

Here is where I seem to start having trouble:

*Loading hardware drivers...  [ ok ]
*Starting PCMCIA services...
*PCMCIA not present
*Loading manual drivers... [ ok ]
mount: Function not implemented
*Starting raid devices... [ ok ]

  yadda yadda yadda, all lines ending [ ok ]

*Configuring network interfaces [ ok ]
*INIT: Entering runlevel: 2
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory

This is the last thing that happens.

When I try the normal install, it hung earlier, but I don't remember where.

At one website, I read a whole procedure for checking the hash codes, but I didn't understand it, and it didn't sound like it was for Windows. non-Windows sort of thing.

Before trying to boot, I did run the CD test from the menu.

I saw a work around for the PCMCIA bug, is this what I am experiencing?
If so, the work around is for "permanent" installations, isn't it?:-k 

Thanks,
Mary

---

### Post by tubasoldier on 2006-10-23
Mary,

 I dont really have an answer to your question but I do have to say good luck with HP. I had quite a bad experience with them when I bought a laptop from them. And I could not get linux to install correctly on it either. It was a duo=core and their bios implemented the acpi thermal configuration incorrectly for the second processor thus making it impossible to install linux. Windows just throws out the 0 degree Celcius issue while linux really does care what temperature your processor is.

---

### Post by plantluvver on 2006-10-23
So far, I am happy with HP's support of the product(as far as it goes.)

One REALLY good thing is that I bought the HP at Office Depot, and I can get a cash refund for it, if I can't get Linux to install properly.  So, I have a steep, but short learning curve.](*,)   The problem is, that I am getting used to grabbing the laptop and taking it out for a latte or a beer.  She's my first laptop, and like all first loves, she is becoming very special to me.;) 

Mary

---

### Post by gn2 on 2006-10-23
Your problem is most likely to be the 64-bit OS.

Have you tried 32-bit?

Much more likely to work....

---

### Post by plantluvver on 2006-10-24
I don't know one processor from another.  However, the PC and the box say AMD Turion 64 mobile technology.  This is why I used the 64 bit OS.  Can I use the 32 bit version on my machine? 

I am confused about the names of the different distributions of v6.06.  I have seen reference to the Live CD,  does tis mean the standard distribution? (Is it called Live because it is supposed to be able from booting the CD.)

Anyway, I downloaded the alternate 64 bit Kubuntu image yesterday.  I will burn it and see if the install goes any better.  (I switched to Kbuntu because I currently have a KDE desktop, and don't feel I need to switch.)

If I can't figure that one out, I am going to look in the public library for a Linux book, or buy a magazine ot book at a large bookstore.  I looked at my bookstore's website, and they don't seem to have anything on Ubuntu, so I will probably go to a different distribution.

Mary

---

### Post by gn2 on 2006-10-24
> **plantluvver said:**
> I don't know one processor from another.  However, the PC and the box say AMD Turion 64 mobile technology.  This is why I used the 64 bit OS.  Can I use the 32 bit version on my machine? 

I am confused about the names of the different distributions of v6.06.  I have seen reference to the Live CD,  does tis mean the standard distribution? (Is it called Live because it is supposed to be able from booting the CD.)

Anyway, I downloaded the alternate 64 bit Kubuntu image yesterday.  I will burn it and see if the install goes any better.  (I switched to Kbuntu because I currently have a KDE desktop, and don't feel I need to switch.)

If I can't figure that one out, I am going to look in the public library for a Linux book, or buy a magazine ot book at a large bookstore.  I looked at my bookstore's website, and they don't seem to have anything on Ubuntu, so I will probably go to a different distribution.

Mary

You can use 32-bit, 64-bit can cause difficulties.

Also for laptops, I have found that with Ubuntu mine will go into and resume from standby, I couldn't get it to work in Kubuntu, could just have been my machine though. (or incompetence on my part)

The Live CD is the standard download, called "Live CD" because it will boot and run live from the CD without being installed on the hard drive.

There is an official Ubuntu book available through Amazon.

Ubuntu is very well supported and can be a good choice if you're willing to learn.

Hope that helps.

---

