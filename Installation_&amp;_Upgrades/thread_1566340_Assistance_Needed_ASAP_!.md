---
title: "Assistance Needed ASAP !"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by ilegal on 2010-09-02
Hello friends,

I have quite a problem here, so:

I just got a brand new laptop Dell vostro 1015, and the sales man asked what OS i wanted, i knew about ubuntu (free code OS) and becouse i have my own Win 7 i told him that i use ubuntu, and apearantly he installed ubuntu 8.10. Now i want to remove everything from my laptop and install win7, but as i first time use ubuntu OS i dont know how to do that. i was searching forums, read about gparted and stuff, but i even dont know what that is. so please, if there is a easy way to wipe it simply, leaving no data in hard disk? i also have ubuntu 8.10 desktop edition DVD. 

P.S. i tried to insert windows cd, but i wount load, and i dont know how to set the boot to win7 DVD. 

So, i would really appretiate any help, cuz i need to have win7 installed in two days.. :/

thanks in advance!

---

### Post by endotherm on 2010-09-02
well, the good news is, that all you have to do is install windows, and tell it to use the whole hard disk. that will get rid of ubuntu in and of itself,

the bad news is that since every bios is differant, you may have to search online or contact your manufacturers customer support to learn how to configure the bios to boot from the win7dvd. on my box, I can use delete to enter setup, and on the advanced configurations menu, I just change the first boot device to be the optical drive. or I could just hit F12 when the bios splash screen comes up, and select whatever boot device I want to use from the list it presents.

---

### Post by Ms_Angel_D on 2010-09-02
You more than likely need to go into the bios and change the boot order of your drives. You can normally do this by hitting one of your f keys f1 or f2 or something.

As far as formatting your drive goes. Download and burn a copy of the livecd

[How to Burn ISO]("https://help.ubuntu.com/community/BurningIsoHowto")

insert it in your drive and select to try ubuntu without making any changes. once the desktop loads look under system->administration->Gparted

Load it up and use that to turn swap off, delete the swap partition and the ext partition then format the space to ntfs. after that you should just have to put the windows disk in the drive and be able to go from there.

---

### Post by ilegal on 2010-09-02
the only option when my laptop when booting is hit F12 for boot options, i hit it, and there is:

Ubuntu 8.10, kernel 2.6.27-10-generic
Ubuntu 8.10, Kernel 2.6.27-10-generic (recovery mode)
Ubuntu 8.10, memtest86+
Reinstall Operating system (warning: all hard drive data will be LOST)

by pressing reinstall it installs ubuntu over again. 

Yes, my laptop has 250GB drive, as i understood from ubuntu ''My computer'' window, there is ''File System'' (hard disk as i understand) and ''OS'' (for reinstalling ubuntu i presume)

And i just want ti wipe it out.. i havent found anything useful on internet, touching this laptop's bios mode or smth...

---

### Post by Ms_Angel_D on 2010-09-02
Just because it doesn't tell you the option is there doesn't mean it does not exist try the F keys starting with F1 until one gets you into the bios.

---

### Post by ilegal on 2010-09-02
i found how to enter bios mode, rly big thanks! but i ran into another problem.

in bios mode, i go settings - general - boot sequence untick all settings, leave just CD/DVD/CD-RW Drive, and it wount boot the CD.. only thing i run into while booting is a message in black screen is ''press ESC for boot menu'' or smth like that, i press and i get choises same as i mentioned before. if i press nothing, it just loads ubuntu again. 

damn, im really confused..


EDITED: finaly from maybe a third time i succeeded booting up win 7 CD. i hope everything will go as i should. thanks for support guyz. 

BTW, as i used ubuntu a little, i found it quite interesting, i want to know what version of ubuntu i should choose (im thinking about installing ubuntu to my desktop PC, becouse i need to have win 7 on my work laptop)

as i said, i have Ubuntu 8.10 desktop edition DVD, it came in a box with my laptop, but is there a better version of it?

---

### Post by endotherm on 2010-09-02
the latest version of ubuntu is Lucid (10.04) and it is a long term support release, so it is a good choice for those trying to get work-stuff done in ubuntu. there will be a new release "Maverick Meerkat" coming in late october, but I would go with lucid for now.

---

