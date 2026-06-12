---
title: "Ubuntu 10.04 and external HDD issue !"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Hot_Sauce on 2010-05-01
I have burnt the 10.04 image on my CD. I want to install it on my external HDD now. So I can boot 10.04 from my external HDD on any laptop/PC that supports USB booting.

Is this possible ? Is this the procedure to be followed ?

[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

---

### Post by Herman on 2010-05-01
:) Sure it's possible!
It's not only possible, it's easy too!
Just remember to install the GRUB boot loader to MBR inside the USB drive, and don't let it get installed to MBR in your first hard disk drive inside your computer. 
This link shows you how,  [COLOR=#000000][Ubuntu /  Windows Dual Boot]("http://members.iinet.net.au/%7Eherman546/p24.html").[/COLOR]

---

### Post by Hot_Sauce on 2010-05-01
> **Herman said:**
> :) Sure it's possible!
It's not only possible, it's easy too!
Just remember to install the GRUB boot loader to MBR inside the USB drive, and don't let it get installed to MBR in your first hard disk drive inside your computer. 
This link shows you how,  [COLOR=#000000][Ubuntu /  Windows Dual Boot]("http://members.iinet.net.au/%7Eherman546/p24.html").[/COLOR]

So if I follow the steps that is provided in the link I POSTED, that same procedure ensures that the GRUB boot loader is installed in the MBR in the external Hard Drive ?

---

### Post by Herman on 2010-05-01
I'm not sure if that link you posted will work or not. I would need to try that out to find out. 
How about you try it and let me know what happens? :)

Oh, I see, they're talking about unplugging all of the internal ahrd drives in the computer.

Well, that will work okay, I suppose, but since you're going to the effort of opening your computer case and messing around with IDE and SATA cables, why not plug your external drive in to your motherboard through an IDE or SATA cable? It will work ten times as as fast. USB2 is slow compared with IDE or SATA.

---

### Post by Hot_Sauce on 2010-05-01
> **Herman said:**
> I'm not sure if that link you posted will work or not. I would need to try that out to find out. 
How about you try it and let me know what happens? :)

Oh, I see, they're talking about unplugging all of the internal ahrd drives in the computer.

Well, that will work okay, I suppose, but since you're going to the effort of opening your computer case and messing around with IDE and SATA cables, why not plug your external drive in to your motherboard through an IDE or SATA cable? It will work ten times as as fast. USB2 is slow compared with IDE or SATA.

Oh my sincerest apologies. I was not aware that I was supposed to remove the internal HDD for that process.

I am on a laptop so I cannot do this ! The link you have posted I cannot really understand. Can you please help me understand how to install 10.04 on an EXTERNAL HDD so that it could be booted through any other computer that supports USB booting ? :)

---

### Post by Hot_Sauce on 2010-05-01
The link you have posted as I understand shows to to do a Dual boot ? I  am very amateur to this so I am sorry of my question is a bit ignorant

---

### Post by Herman on 2010-05-01
Yes, the link I posted shows you how to set up a dual boot, -on two hard drives - , it also shows you how to install the boot loader to whichever drive you think best. 

Maybe the link is misnamed. 
The information in that link is designed to be applicable to any situation where there are more than one hard disk, including external USB drives. 

Please let me know what it is you don't understand and I'll be happy to clarify. :)

---

### Post by Hot_Sauce on 2010-05-01
> **Herman said:**
> Yes, the link I posted shows you how to set up a dual boot, -on two hard drives - , it also shows you how to install the boot loader to whichever drive you think best. 

Maybe the link is misnamed. 
The information in that link is designed to be applicable to any situation where there are more than one hard disk, including external USB drives. 

Please let me know what it is you don't understand and I'll be happy to clarify. :)

SO when I enter the CD i just burn and click on nstall ubuntu I basically I use the ERASE AND USE THE ENTIRE DISK option and from that option I select my external HDD from the menu and progress as the link states ? Would that not format my windows XP ?

---

### Post by Herman on 2010-05-01
No, there are three illustrations there, the first one shows how you need to select 'erase and use the entire disk', but if you scroll sideways a little and read the information that goes with the illustration you'll understand that that's not what we're actually going to do.
This is one of the reasons why you would want to be following a how-to, because the best procedure is not immediately obvious to the inexperienced person. 

The next illustration shows you how to select the hard disk you want to erase, in which case, you need to choose your USB external hard disk drive. (I assume you have backed up any data in it to a different media).

The illustration after that, (if you look closely), shows /dev/sdb as the device to be used, which in your case will be your USB drive. 

SO, it's perfectly safe, as long as you are careful and aware of what you are doing. :)

EDIT: Or at least *relatively* safe, since nothing is ever perfect.

---

