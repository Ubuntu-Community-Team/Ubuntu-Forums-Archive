---
title: "Unable to install ubuntu on PEAQ pnb c1011"
date: 2016-06-26
forum: Installation &amp; Upgrades
---

### Post by gilles9 on 2016-06-26
Hello everybody,
I m trying to install Ubuntu 16.04 on my new laptop peaq that I buy yesterday.. So to do that, i gone to the bios and desactivate the Secure boot, but when I reboot the computer and push on F12 and select the USB key where is installed Ubuntu, it doesn't work and the usb does not load. There is also a lot of security keys for Windows. 
I don't know what to do. 
Can anyone help me ? 
Thank's in advance. 
Gilles

---

### Post by Manuel_Olivier on 2016-06-26
Hello Gilles

Can you tell us which pre-installed OS you had on this computer plz? If it's Windows 8 or 10, then you have to make an UEFI boot with the usb key/HDD/CD which contain your ubuntu .iso
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

After doing that, make sure to follow the correct steps to install ubuntu (if you never did it before). The most important part is to create AT LEAST two partitions, root (/, it's an ext4 partition) and swap.
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Hope this answers your question

Regards
Manuel

---

### Post by gilles9 on 2016-06-26
The pre-installed OS is windows10 and there is some screenshots of the bios security manager. But Nothing to do, when I press F12 and select the usb flash drive, the same screen for selecting entries to boot reapear..
I'm now reading your link 
Thx for your answer

[[IMG]http://img11.hostingpics.net/thumbs/mini_946382IMG20160626204055.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=946382IMG20160626204055.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_877281IMG20160626204122.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=877281IMG20160626204122.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_902314IMG20160626204143.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=902314IMG20160626204143.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_297547IMG20160626204159.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=297547IMG20160626204159.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_121915IMG20160626204222.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=121915IMG20160626204222.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_148618IMG20160626204246.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=148618IMG20160626204246.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_148618IMG20160626204246.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=148618IMG20160626204246.jpg)
[[IMG]http://img11.hostingpics.net/thumbs/mini_260706IMG20160626204402.jpg[/IMG]](http://www.hostingpics.net/viewer.php?id=260706IMG20160626204402.jpg)

---

### Post by Manuel_Olivier on 2016-06-26
Actually you can modify that inside your Windows settings (at least that's what I did with my Win 8.1 after a few attempts).
Here is what I advise you:

Go to Settings -> General -> Advanced startup -> "Restart now"
You will access a few options which allow you to choose how to restart your computer, INCLUDING FROM AN EXTERNAL SUPPORT (your CD, usb key, etc.). So if you can restart from any external device in the "Startup Setting", choose the one you need

However this won't be enough to disable Secure boot. IN ORDER TO DO THAT, after having selected "Restart now" (mentioned earlier), click on Troubleshoot -> Advanced Options -> UEFI firmware settings -> restart
Now you might be able to turn off Secure boot and save your changes after rebooting.

Keep getting us informed!

Manuel

---

### Post by oldfred on 2016-06-26
Do not mess with Keys. Ubuntu uses the default UEFI Secure boot key from Microsoft.
If you have erased keys, restore them.

But often better to just turn off UEFI Secure boot, but you still want to install in UEFI boot mode, not CSM/Legacy/BIOS boot mode.

---

### Post by gilles9 on 2016-07-05
I still cannot disable protected and customized signatures. Now, UEFI secure boot is disabled but it doesn't load the key.

I didn't get the meanning of this message :
*But often better to just turn off UEFI Secure boot, but you still want to install in UEFI boot mode, not CSM/Legacy/BIOS boot mode. *
thx for your help

---

### Post by gilles9 on 2016-07-05
also when I try to lauch it with VirtualBox, I got this message : This Kernel requires an x86-64 cpu, but only detected an i686 cpu.
Unable to boot - please use a kernel appropriate for your CPU. 

Anyway, I don't know if it's why the key refuse to boot...

---

### Post by gilles9 on 2016-07-05
Anyway, I don't know if it's why the key refuse to boot because I have just not error message. Simply Nothing, the menu reapear.

---

### Post by oldfred on 2016-07-05
I do not know virtual installs. But if installing 64 bit virtual in a 32 bit install it will not work. Or you may need the 64 bit installer for UEFI install. The 32 bit will not install in UEFI mode.
Virtual may require different settings.

But if you deleted keys you have to restore them. It should have a way to just restore the default Microsoft keys.

New UEFI systems have three boot modes.
UEFI with Secure boot.
Standard UEFI (without secure boot)
CSM which also is not secure boot.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
Only Windows 8 or later installed by a vendor required Secure boot to be on. Many newer systems do not even call it Secure boot but have "Windows" and "Other" where even Windows 7 must use "Other".

---

### Post by gilles9 on 2016-07-05
I had effectively deleted all signatures for testing so bitlocker reinstaled it automaticaly. I m begginig to desesperate but i dont want to give up. I also tried to install the 32 bit version but it's still not working...

Ok, the tab authenticates signatures is empty. i'll try to resolve this problème. thx for your help and patience !

maybe someone know a way to restore the default Microsoft keys authentificates signatures ? if it's the problem ...


maybe someone know a way to restore the default Microsoft keys authentificates signatures ? if it's the problem ...i mean this [http://www.hostingpics.net/viewer.php?id=121915IMG20160626204222.jpg](http://www.hostingpics.net/viewer.php?id=121915IMG20160626204222.jpg)

---

### Post by gilles9 on 2016-07-05
...i mean this [http://www.hostingpics.net/viewer.php?id=121915IMG20160626204222.jpg](http://www.hostingpics.net/viewer.php?id=121915IMG20160626204222.jpg)

sorry for double posting

---

### Post by oldfred on 2016-07-05
In post #3 you show a reset to default option. Is that what is giving error?

---

### Post by gilles9 on 2016-07-06
I really don't know and I begin to feel bored by the situation. I meet an informatician who say that I have maybe to flash the bios but I dont know how to do that.

---

### Post by oldfred on 2016-07-06
This was the one you should not have done.
But entry above says reset to default. Have you done that?

[http://www.hostingpics.net/viewer.php?id=902314IMG20160626204143.jpg](http://www.hostingpics.net/viewer.php?id=902314IMG20160626204143.jpg)

Some systems do work better with latest update to UEFI. Often easier from Windows as vendors assume you have that.

But generally you have to go out to vendors site, find model number, and find updates. See if version is newer than one you have installed. Usually in manual in same location are instructions on various ways to update. Some update from Windows, some have you create a bootable DOS flash drive with update on it, and some let you read the update from any FAT32 formatted partition.

If not familiar with UEFI, have you reviewed link below in my signature? It can be a lot but often needed to understand UEFI and its new features to the old BIOS.

---

### Post by gilles9 on 2016-07-19
yes i reset the configuration. I seen your link but i don't know how to allow USB/DVD boot in the bios using chkdsk. I'm a little confused.

---

### Post by oldfred on 2016-07-19
Chkdsk is Windows only. 
It is part of the Windows repair console or may auto start on reboot if NTFS partition flagged during use that it has issues.

Allowing USB boot could be a setting in UEFI/BIOS. Many have to have that on to be able to boot any external device, especially if Secure Boot is on in UEFI systems as booting any other way would not be "secure".

---

### Post by gilles9 on 2016-07-19
OK, so how can I do it is turned off ? It stay w10 signatures that I can not remove even in haven make a admin user password. ? and it is still the same  p even with a key from 7 i can't boot on usb...

---

### Post by gilles9 on 2016-07-19
the bios it so limited and I don't know the way around

---

### Post by oldfred on 2016-07-19
Some BIOS open up more settings if you set a supervisory password? Does your BIOS have a password. If you set one, never ever lose it, or else you convert system to a doorstop. (there are ways to totally reset, but may require disassembly of system)

Where are Windows 10 signatures coming from? Was system originally Windows 10?
Windows 7 does not correctly convert gpt partitioned drives which Windows 10 in UEFI mode requires, to BIOS/MBR.
Better if drive was gpt to convert Windows 7 installer to UEFI to use gpt partitioned drive.

---

### Post by mook765 on 2016-07-24
Try to install from dvd. check the checksums off your downloaded iso, burn dvd at lowest speed wich is supported by your dvd drive.
i tried all the usb installer tools like rufus etc... 16.04 is not supported...
if there is no dvd drive in your laptop, use external drive via usb.

---

