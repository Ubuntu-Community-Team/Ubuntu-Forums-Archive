---
title: "new and needs help"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by android272 on 2011-04-08
Im new to ubuntu and im having trouble installing it.  I do all the steps on the ubuntu home page for making a USB install drive but its just not working on ether my nor my mom's PCs.

I have had it running on both PCs once before but my tablet got messed up and hers I just tried Ubuntu. now when I put in the USB it looks like I its trying to do something but I dont know what its doing.


here is what the screen seas on both PCs when I put the USB in.
[IMG]http://i42.photobucket.com/albums/e347/Android27/IMAG0116.jpg?t=1302272031[/IMG]

---

### Post by Rubi1200 on 2011-04-08
Hi and welcome to the forums :-)

The picture is a very nice shot of you taking a photo of a blank screen ;)

But seriously, did you follow these steps?

post the specifications for the computer, especially the graphics card

check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I assume you set BIOS to boot from the USB/Removable drive?

How did you put the image on the USB?

I recommend UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ronparent on 2011-04-08
Hi Rubi

You will notice he is getting the boot loader more common for the live cd image than for an installed system? It seems to me that he has to boot a live cd and verify the install. Then he will be able to id it to reinstall grub to it and place the boot loader on the external drive. Got to run.

---

### Post by android272 on 2011-04-08
sorry guys I forgot that you would need my info. 

PC: HP TouchSmart tm2 Notebook PC
OS Name:	Microsoft Windows 7 Home PRemium
OS Manufacturer:	Microsoft Corporation
Processor:	Intel(R) Core(TM) i5 CPU     U470 @ 1.33GHz
BIOS Version F.14 - 08/32/2010 (058A210000242A10000120100)
Windows Directory	C:\Windows
System Directory	C:\Windows\system64
RAM 4.00 GB

I don't know if you would need any more info

---

### Post by Rubi1200 on 2011-04-09
Did you set BIOS to boot from the USB drive?

At what point does the screen go blank?

A Google search seems to indicate you have an ATI Radeon graphics card. Did you use the nomodeset option when booting?

---

### Post by Favux on 2011-04-09
Hi android272,

Likely the problem is the dual video chipsets.  You should be able to install if you block the ATI videocard and go with the Intel MB video only.

Depends on what release of Ubuntu you are using.  I'll guess Maverick.
[https://wiki.edubuntu.org/HP%20TouchSmart%20tm2](https://wiki.edubuntu.org/HP%20TouchSmart%20tm2)
[http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)
I'd ignore the advice to put touch on the Synaptics driver as you should be able to get the Wacom X driver to work fine for touch.  Also for rotation you can use the Magick Rotation applet.

There are a couple of other bigger TM2 how to threads for Lucid.

I think Natty may offer drivers for both videos.  We'll have to see.  Especially what the proprietary ATI fglrx driver offers.

---

### Post by android272 on 2011-04-09
Thank you [Favux]("http://ubuntuforums.org/member.php?u=699990")  for the links.  I wish I could have seen these likes when I had ubuntu  on my tablet.  it seems that they solution to my my screen going  blank(the reason I uninstalled ubuntu) it to just close my screen and  then open it again.

now the problem is reinstalling it. I did set the root mode to USB.  the screen flashes the picture that I posted above.  once I'm a this screen I can do nothing, and when I try to hit keys after a while it beeps at me every time I hit another key.  Since that last time I successfully got ubuntu on my tablet I have tried to make multiple bootable USB drives but they all say what is in the picture.

---

