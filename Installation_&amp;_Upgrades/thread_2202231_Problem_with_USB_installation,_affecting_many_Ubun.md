---
title: "Problem with USB installation, affecting many Ubuntu users"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by rob33 on 2014-01-28
>>>> SYSLINUX 4.03 2010-10-22 EDD Copyright (c) 1994-2010, H. Peter Anvin et al <<<<

This problem is affecting thousands of Ubuntu users, and still nobody appears to have come up with a proper solution to it! 

I used to have an Acer D250/eMachines EM250 netbook, and when installing Ubuntu via a USB memory stick i would always get the message above. I would plug the memory stick into the netbook, press F12 at the BIOS and select the USB to boot Ubuntu; but as soon as i did this the dreaded 'Syslinux - Peter Anvin et al' error would come up. After months of searching looking for an anwser, i eventually found out myself that the memory stick needed to be in FAT format and not FAT32 or NTFS, otherwise Ubuntu would not boot. 

Yesterday i decided it would be a nice idea to attempt an install of Ubuntu onto my 80GB external hard drive. Big mistake!

I installed Ubuntu 64bit onto my 8GB Sandisk Cruzer memory stick, formatted as FAT32 with Unetbootin, and i get the same message. This time i am using an Acer V3-571G notebook. 

Remembering my previous problem with the D250 netbook, i decided to format another different memory stick as FAT, rather than FAT32. Again, the USB was made in Unetbootin. The memory stick was a 4GB TDK USB drive. The Unetbootin menu came up on boot, but it froze when i clicked on any of the boot options. Even if i left the menu to go past the boot timeout, it would still freeze.

I then used Lili USB creator instead, again with the TDK memory stick, but this doesn't work either. I get to the purple Ubuntu screen with the keyboard symbol next to the little little man symbol, and then it goes onto a black screen with a blinking cursor.

This problem with the 'Syslinux - Peter Anvin et al' error needs to be sorted out! There are loads of people on the internet complaining of this issue, especially with Acer laptops. If you Google the error, hundreds of pages come up, but none seem to have a straight forward and working solution. Of course, the people who have spent the time to write on forums about this error are only a small population of the people who are actually getting it, i bet thousands of people are trying to install Ubuntu with no luck!!

Please, i am begging, someone help us!! We need suggestions on how to fix this error with these laptops. 

I am literally just about to give up on Ubuntu, and the whole of Linux altogether if i am unable to solve this problem. This is a last attempt and then i will have to say goodbye to everything Linux!

I hope you guys can help. Any advice would of course be greatly appreciated!

Cheers! :)

---

### Post by Bucky Ball on 2014-01-28
Don't format it as anything. Let Unetbootin take care of it. I have created five install USBs with Unetbooting over the last four days and not had a prob with any of them. 

[QUOTE=rob33]There are loads of people on the internet complaining of this issue, especially with Acer laptops.[/QUOTE]

And that might sum it up. Perhaps it is specific to Acer computers, or more likely, a range of models. I'll have a look.

---

### Post by Bucky Ball on 2014-01-28
Have you tried this:

Open syslinux.cfg on the USB drive and replace the following line:

> ui gfxboot bootlogo

with

gfxboot bootlogo


From here:

[http://askubuntu.com/questions/34088/cant-install-with-usb-pen-drive-syslinux-problem](http://askubuntu.com/questions/34088/cant-install-with-usb-pen-drive-syslinux-problem)

? When you've created the USB with Unetbootin, open it in a file manager, find that file and change.

 Universal USB Installer also appears to solve the issue.

PS: It does get formatted to FAT32. That's what you should have been formatting it as so not the issue.

---

### Post by rob33 on 2014-01-28
> **Bucky Ball said:**
> Have you tried this:

Open syslinux.cfg on the USB drive and replace the following line:




From here:

[http://askubuntu.com/questions/34088/cant-install-with-usb-pen-drive-syslinux-problem](http://askubuntu.com/questions/34088/cant-install-with-usb-pen-drive-syslinux-problem)

? When you've created the USB with Unetbootin, open it in a file manager, find that file and change.

 Universal USB Installer also appears to solve the issue.

PS: It does get formatted to FAT32. That's what you should have been formatting it as so not the issue.
[FONT=verdana]
Hi, 

Thanks for the response. I have created an Ubuntu 13.10 64bit USB in Unetbootin 585, but when i open syslinux.cfg, there is no line there which matches the one you posted.
[/FONT]
default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 


label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --


label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --


label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --


label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 


label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 


label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --


label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --


label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

I have also made a USB in Pendrivelinux and this didn't work either. I did this yesterday but i forgot to mention about it in my original post.

Here is something **very** interesting though; i remember from when i had the same problem with my Acer D250 netbook, that when the USB was inserted into the machine i got 'Syslinux - Peter Anvin et al', but if i plugged the USB into another computer, which wasn't an Acer, the USB booted up perfectly straight into Ubuntu.

Clearly it is a problem with specific computers.

But the issue on the D250 netbook was also 100% definitely releated the the drive format. I did many tests at the time and i had no end of evidence to show that it was FAT32 and NTFS formats causing the issue. But i don't know whether it was just that specific laptop which didn't like the other formats? I don't think this has much to do with the problem on the V3-571G notebook.

What to do now?

---

### Post by Bucky Ball on 2014-01-28
Apparently there is no such problem installing from a disk. Got a blank one?

What you could specify is that this is only happening with Ubuntu or also with all attempted installs of anything from USB using Unetbootin.

---

### Post by rob33 on 2014-01-28
> **Bucky Ball said:**
> Apparently there is no such problem installing from a disk. Got a blank one?

What you could specify is that this is only happening with Ubuntu or also with all attempted installs of anything from USB using Unetbootin.
[FONT=verdana]
I've got loads of spare discs at home, so burning the Ubuntu to one won't be a problem. 

I'm just trying another memory stick, a 4GB Transcend, just to be sure it's not an issue with the actual memory sticks i'm using.

Not sure whether the problem occurs on any other Linux distrobutions with USB's made through Unetbootin, i will investigate this morning.

Thanks.
[/FONT]

---

### Post by sudodus on 2014-01-28
I'm interested in solving issues with booting from USB. Maybe I can help you, or maybe your experiences will help other people with Acer, and maybe also some other systems.

Your problems might depend on the hardware, for example the USB system on the motherboard, or on the BIOS/UEFI firmware as well as on the pendrives and the systems installed in the pendrives.

Generally, I've had good experiences of booting from USB pendrives, where the iso files was flashed or cloned directly with dd. But it is risky, so I made a shell-script to make it safe, ***mkusb***. See this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

I have tested booting (speed and ability to boot) recently and reported it in this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

See also this general Ubuntu wiki page with a lot of tips about booting from USB [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by rob33 on 2014-01-28
[FONT=verdana]Hi again,

Thanks very much for the responses. I have found the information provided in the links posted very interesting and informative. 

In my last post i said that i would try using my Transcend 4GB USB drive as well, just to be on the safe side and ensure that it was indeed a problem with the USB drives i was using.

I made a bootable USB inside LinuxLive USB creator (Here: [/FONT]http://www.linuxliveusb.com/), and this time i plugged the memoru stick into the USB 3.0 port, rather than the USB 2.0 port. I booted the computer and hit F12, and then selected the Transcend USB stick. It rapidly flicked some writing on the screen for about half a second (It looked like the 'Syslinux - Peter Anvin et al' error again, but amazingly, i was greeted with a blank purple screen and then to my biggest relief, the Ubuntu loading screen!!! Ubuntu loaded to the desktop after about twenty seconds, and i was able to complete the install no problem. Strange!

If anyone is reading this, with the same error as what i recieved, here is my advice to help you sort the problem out:

+ Format the USB as FAT (Not FAT32 or NTFS) and then put Ubuntu on the drive, making sure that the installer does not overwrite the drive format. It needs to have 4GB memory maximum to be formatted as FAT.
+ Try swapping the drive to another USB port, preferably a USB 3.0 port as this is the one which worked for me.
+ Check the MD5 of the Ubuntu ISO you downloaded. (There is a good tool here to help do this: [http://www.winmd5.com/](http://www.winmd5.com/))
+ Swap the memory stick for one that is a different brand. (People on internet forums have said that Sandisk drives are causing trouble).
+ If using an Acer laptop, realise you have bought a laptop from the worst computer manufacturer in history! I had to return my laptop last month because of several faults which had developed, and their customer service was absolutely terrible. The repair was said to take 7-9 days from the moment i posted it to the moment i recieved it, but the repair actually took almost a month! And this was over the Christmas period, when i'd be needing my laptop the most! They also did various other things to annoy me also, such as stealing the hardware stickers off the palm rest and nicking my memory card tray too!!

But anyway, thanks again guys for helping me with this issue. I am so happy that i have finally got Ubuntu working on my laptop!

Cheers!

---

### Post by Bucky Ball on 2014-01-28
Great news! Could you please follow the instructions in the link in my signature and mark as solved to help others. Thanks for sharing the fix. It is the done thing. ;)

Enjoy the forums, the learning curve and Linux!

---

