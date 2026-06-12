---
title: "Difficulties installing Ubuntu"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by Toby_Wyant on 2014-11-08
[COLOR=#000000][FONT=Segoe UI]I'll include specs at the end for the purpose of brevity, for both of my laptops and the hdd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]I'm using ubuntu on my chromebook via crouton. My desktop manager is xfce cuz it needed to be light. I've got two laptops, one of which is a tiny samsung chromebook for work, the other of which is an old lenovo g505 which I use for dota mostly. This is the one that I put the new hdd in. 
So, got my new hard drive since the old one went kaput. Opened up the laptop, put in the new hd (being sure to do it away from possible sources of static). Copied ubuntu iso to my flash drive, and used mkusb so I could boot via the usb. So far, so good right? Plugged the usb in, started up the laptop, and nothing happens. I just get the lenovo flash and then it restarts to show me the flash, black screen, et cetera both ad infinitum and nauseum.  
I've tried accessing the bio settings with the function keys (f1-f12, as well as fn f1-12. No juice), as well as fn-delete as well as delete. Still no juice. I can't seem to access any settings at all, which is unusual.[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]**Specs**[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]The chromebook is fairly tiny samsung netbook. The model number is 303c, but it shouldn't be too important as I'm not having troubles with this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]The hard drive is a Toshiba Solid State hybrid drive, 500 gb. There are a bunch of other specs on the side of the box but I'm not sure how relevant they are. I'll include them anyway. *Interface: Serial ATA 6Gb/s with Native Command Queuing 
*Height is 7mm [&#8776; common military ammunition size] 
*Rotational speed is 5400rpm 
*NAND Flash size: 8gb SLC 
*Buffer: 32mb There's also what I suspect is some kind of serial number on the back. It is PB00014E1.[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]The big laptop is a lenovo g505s. Fairly old, but only had problems with the hd once before. I replaced it, and have now replaced the replacement.[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Anyway, that's about it. I would enjoy a speedy response, as I want to play dota. :D

[/FONT][/COLOR]

---

### Post by nerdtron on 2014-11-08
> [COLOR=#000000][FONT=Segoe UI]Copied ubuntu iso to my flash drive, and used mkusb so I could boot via the usb. 

Have you tried other method of creating a bootable USB? [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
There are also utilities like unetbootin for windows.

And just to make sure that you have a working USB installer, try to boot it on other machine too.
[/FONT][/COLOR]

---

### Post by Toby_Wyant on 2014-11-08
I've had a look at that. I would see if I could boot it on another machine, but all I've got is my laptop and my chromebook (running ubuntu/chromium via crouton).  
I wasn't able to get any of the other methods working.

---

### Post by oldrocker99 on 2014-11-08
A very reliable way to create a bootable USB is **unetbootin**, which runs on Windows, Mac or Linux. The USB drive does need to be formatted as FAT, which a new stick probably already is. You can select a distribution from a list, in which case the program will download the .iso and write it to the USB. Or, you can download the .iso yourself, and point unetbootin to where the downloaded .iso is located. Either way, it will create a bootable USB.

---

### Post by Toby_Wyant on 2014-11-08
Trying to get unetbootin to work. Can't open it when the file doesn't have executable permissions, and when I do nothing happens if I try to run the file.

---

### Post by QIII on 2014-11-08
Hello!

I'm a little confused by your last post.

Do you mean you can't install UNetbootin?

Do you mean you can't open UNetbootin?  Can't you run it as an application?

Do you mean you can't open the ISO you are attempting to use?

What, exactly, are you doing when "nothing" happens?

Please paint us a word picture.  It is very difficult to help if we don't know exactly what is going on.

Cheers!

---

### Post by Toby_Wyant on 2014-11-08
Sorry for the less than timely reply, I was tinkering around. 

I can't install UNetbootin. I've given it execute permissions (allowed it to run as a program), but nothing happens when I click on it.

I've tried to run it via bash by navigating to the download directory with cd and using ./unetbootin-linux-608. I receive the following error: 

  bash: ./unetbootin-linux-608: cannot execute binary file

No idea what that means. All I want is to install ubuntu on my new HD, but there are a few problems. 

Firstly, while I can access the boot menu, I can't do so when the USB is plugged in. 
Secondly, if I don't try to access the boot menu and just plug in the USB and start up (which has worked in the past), all that happens is the lenovo splash showing up, black screen, and restart. 

I've tried using mkusb to create a bootable USB, but it doesn't appear to have worked. 
Trying to use UNetbootin, but have encountered the previously mentioned problem. 

Thanks for any help.

---

