---
title: "Can I Triple Boot XP/Vista/Gutsy Gibbon?"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by epblash on 2007-10-24
Right now I'm dual booting XP and Vista using the EasyBSD program. I had to jump through a couple hoops to get it to work since the bootloader kept corrupting, but I eventually got it to work.

I want to try Linux, fool around with it a bit, and the like. Can I triple boot with XP, Vista, and Gutsy Gibbon? Is it as simple as running the live installer off the CD and then the GRUB booter takes care of the rest, or are there a couple other things to get GRUB to recognize the triple boot? Do I have to do something special in the live installer, other than taking a little room off of one of the Windows installations to make the swap partition and the like?

I'd try it out myself and experiment, but I really don't have the time to jump through all the Windows Genuine "Advantage" crap for Vista and install all of my programs again. Thanks very much! :)

Edit: oh, and that reminds me: should I get the 64-bit edition, or the 32-bit version? I've got a 64-bit processor, an Intel Core 2 Quad Q6600, and the Vista install is 64-bit. Point is, is the performance benefit worth it, or should I just get the 32-bit version for compatibility? Or is there a way to quad-boot and get the best of both worlds? :D

---

### Post by pieisgood4589 on 2007-10-24
OK, first of all, you need to edit the partition table in the Ubuntu LiveCD. Go to GParted, or whatever, and create a partition for Ubuntu Linux. If you don't know how, PM me. Next, select that partition when installing by selecting "manual partition" and choose that pre-made emtpy Ubuntu Partition. Then, just follow the simple install crap and Ubuntu will install!

[EDIT] You HAVE to get the 32 bit. The 64-bit is incompatible with intel machines, Good luck! :popcorn::KS:popcorn:

---

### Post by WiFi Ed on 2007-10-24
64 bit Ubuntu runs just fine on my Q6600, all the Core2Duo and Core2Quad cpu's are 64 bit processors...

---

### Post by nolis615 on 2007-10-24
i dont think you can boot more than two operating systems at the same because most partition editors only let you make 4 partitions at the most and most os's require two part's
(a main partition and a swap)

but then again im a noob so... i might not know what im talking about

---

### Post by rsambuca on 2007-10-24
> **pieisgood4589 said:**
> 

[EDIT] You HAVE to get the 32 bit. The 64-bit is incompatible with intel machines, Good luck! :popcorn::KS:popcorn:

INCORRECT.  The AMD64 version works perfectly with the Core 2 Duo.

---

### Post by rsambuca on 2007-10-24
> **nolis615 said:**
> i dont think you can boot more than two operating systems at the same because most partition editors only let you make 4 partitions at the most and most os's require two part's
(a main partition and a swap)

but then again im a noob so... i might not know what im talking about

Holy smokes guys, what is with all of the dis-information today?  You can have as many OS's on your system as you want.  I currently have seven.

---

### Post by nolis615 on 2007-10-24
i thought that i didnt know what i was talking about :)

---

### Post by epblash on 2007-10-24
So how do I install them? :P

Anyways, I found this blog post:

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

which looks rather ideal, else it would go to the GRUB loader, which would say ubuntu and XP, and if I select XP then it goes to the windows boot loader which gives me the option of XP or Vista. That's a bit inconvenient considering XP would still be my primary OS considering I play quite a bit of computer games (halo, battlefield, steam games (and no, I'm not interested in wine or crossover or the like)) and I don't want to have to go through 2 bootloaders at startup. Is there a way to get them all in the single bootloader without reformatting, even if I have to do some terminal commands to edit GRUB etc?

---

### Post by rsambuca on 2007-10-24
I go through the two bootloaders, but I have set the defaults to XP (for my wife) on both bootloaders.  I also set the timeout options to 2 seconds so there is no real waiting.  Two seconds is plenty of time to hit an arrow key on the keyboard, which will stop the timer and you can select another OS.

---

### Post by epblash on 2007-10-25
how do I set the bootloader time for each bootloader (GRUB and the windows one) please? :)

---

### Post by mrfelker on 2007-10-25
For GRUB (Ubuntu) find the section near the top of the file menu.lst 

# timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

you can edit the timeout by sudo gedit menu.lst and save the new menu.lst.

For Windows you can edit the boot.ini file (you'll have to use the command attrib -r -w -s boot.ini to even see the file).  Use a text editor - notepad will do.  However the timeout only makes sense if you have a second Windows OS or the Recovery Console - otherwise Windows will boot directly with no timeout

---

### Post by rsambuca on 2007-10-25
> **mrfelker said:**
> For GRUB (Ubuntu) find the section near the top of the file menu.lst 

# timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

you can edit the timeout by sudo gedit menu.lst and save the new menu.lst.

For Windows you can edit the boot.ini file (you'll have to use the command attrib -r -w -s boot.ini to even see the file).  Use a text editor - notepad will do.  However the timeout only makes sense if you have a second Windows OS or the Recovery Console - otherwise Windows will boot directly with no timeout

The correct method of opening the text editor is```
gksudo gedit /boot/grub/menu.lst
```

For Vista, can't you just use the control panel?  I am pretty sure I did something like:

Control Panel->System->Advanced System Settings
Then on the Advanced tab->Startup & Recovery-Settings

---

### Post by Smirre on 2007-10-27
My situation is a bit different, I have XP and Gutsy installed, and since the Crysis demo was released just now, I want to install Vista (for the DX10 support since my gfx card can handle it).  Meaning I still want to keep XP and Gutsy and make it a triple boot affair. (I only want Vista for DX10 games you see, I don't really like that OS :/ ). Afaik Vista has its own bootloader, will I be able to install Vista without any or too much hassle?

---

### Post by rsambuca on 2007-10-27
> **Smirre said:**
> My situation is a bit different, I have XP and Gutsy installed, and since the Crysis demo was released just now, I want to install Vista (for the DX10 support since my gfx card can handle it).  Meaning I still want to keep XP and Gutsy and make it a triple boot affair. (I only want Vista for DX10 games you see, I don't really like that OS :/ ). Afaik Vista has its own bootloader, will I be able to install Vista without any or too much hassle?

It should work fine.  Just direct Vista to install to a new partition, and it will detect XP and add it to its bootloader and overwrite grub.  Then you can re-install grub with any Ubuntu liveCD.

---

