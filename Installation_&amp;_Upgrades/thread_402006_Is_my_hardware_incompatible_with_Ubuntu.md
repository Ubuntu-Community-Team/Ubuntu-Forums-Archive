---
title: "Is my hardware incompatible with Ubuntu?"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by Gelinder on 2007-04-05
Hi, I've been trying to install Ubuntu now for the better part of a week and I'm not getting anywere.

I have managed to install the 6.10 x64 version but could not choose the right resolution. My monitor is a HP 23" LCD with 1920x1200 resolution.

I cannot get my computer to display linux without the graphical interface, the screen turns blank (signal still active though for it does not turn off). As soon as I press ctrl+alt+f1 or ctrl+alt+backspace I get the blank screen and need to restart my PC with the reset button.
Thus, I cannot install nvidia drivers.

I ran Envy to install the drivers and could not see the login screen after that and I needed to reinstall linux.

I have tried the 7.04 x86 version, hoping that the newer version had more hardware support ond maybe less bugs. But that CD wont load the graphical interrface. I get to the main meny on the CD but from there anything I choose results in the Ubuntu logo, the bar that goes back and forth for a few minutes then I get an endless row of error messages like this:

undev-event [2407] : run_program: '/sbin/modprobe' abnormal exit
[  129.253106] end_request: I/O error, dev fd0, sector 0
[  129.453673] end_request: I/O error, dev fd0, sector 0
[  142.234325] Buffer I/O error on device fd0, logical block 0

this repets until I reboot with the reset button.

I have checked the CD checksum on my other PC and it reads no errors, install works on that PC too, atleast I could startx on it.

I'm starting to think my hardware is not compatible with the current releases of Ubuntu. I haven't tried any other linux.

My hardware:
Core2Duo E6600
ASUS Commando (Intel P965)
2GB Corsair Dominator 8500
BFG nvidia 8800 GTX
3 sata drives and 1 IDE optical burner
HP f2304 23" LCD monitor 1920x1200

Anyone able to help me out? I really like Linux and Ubuntu and don't feel like going back to Vista.

---

### Post by dannyboy79 on 2007-04-05
WOW, everyone is having this issue. I too have it. Although I don't want to install Edgy Eft 6.10 Live CD version, I merely was trying to use linux to see a windows hard drive that has the NTLDR is missing error. I tried various methods to FIXBOOT, use the ATTRIB command, copy files to it's root drive but no, windows won't boot. Anyway, back to the Live CD problem at hand. 

Setup
~Asus P4P800-E Deluxe (Bios 1009, i think)
-North Bridge Intel® 865PE Memory Controller Hub (MCH); 
-South Bridge Intel® Intel 82801ER Enhanced I/O Controller Hub (ICH5R); 
-Interbridge link: Hub Link v1.5;
-AGP 4x/8x
~Intel P4 Prescott 2.8E (originally overclocked 20% using asus option BUT I ended up clicking on the global setting to make it all default, NOT optimum or best, but standard or default. this depends on bios)
~ATI AIW 9800 Pro, DVI Interface (AGP 4X/8X) 
~1.5gb RAM (Kingston Value Ram)
~2 Optical Drives (Toshiba as slave and NEC as master both on ide0 [ide1 not being used])
~Floppy (unknown)
~120gb Samsung Sata drive-simply NTFS storage for my winbloz xp pro box (connected to ICH5R controller)
~Synergy714 17" flat panel monitor (DVI)
~iogear mini-kvm 2 computers ([http://www.iogear.com/main.php?loc=p...20KVM%20Switch](http://www.iogear.com/main.php?loc=p...20KVM%20Switch))
~wireless (RF, ps/2) mouse and dell keyboard (ps/2) plugged into kvm (wireless keyboard is acting weird so not using it) [[http://www.newegg.com/Product/Produc...2E16823201019]](http://www.newegg.com/Product/Produc...2E16823201019]) this is the same model I have but when I bought it, the wireless module box had 2 ps/2 connectors instead of 1 usb!
~80gb sata windows hard drive-OS=Windows Media Center-1 fat16 partition, 1 NTFS partition, 1 fat32 partition (originally connected to Promise controller BUT switched it to ICH5R)
~originally had left all usb plugs in, printers, usb extender cables, etc, etc BUT removed them all and ran bare min! keyboard connected to kvm and RF wireless mouse to kvm as well and monitor staright to box. See I only use the kvm for mouse and keyboard because my monitor has 2 inputs, so i just use the input button on the front of the monitor and hit scroll lock twice and I am in my other computer. i love it.

No matter what I did I could NOT boot any live cd, I tried Knoppix (i think 5.0), DSL (latest as of 3-17-07), Puppy (latest 3-17-07), Edgy and everyone either stalled during bootup or ended up at the infamous black screen that doesn't do s__t. NO, ctrl-alt-F1 thru F6 didn't bring up a console, and no vga= didn't do anything, trying boot to safe mode didn't work either. Even tried to remove "splash" and then add break=bottom after the "--". I followed this guide: [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)
but even when I got to the initramfs and used the command as noted, I get an error that says that nano doesn't exist. YES, I did verify the cd and I checked my RAM. All ok!! I was like come on, I can't win!!!!!! So, I was thinking to myself, gosh what else can I try. Well I read somewhere that you can add other options for "broken bios" but I knew my bios wasn't broken but I figured, I'll try anything!!! I did what the above guide said but also added noapic and nolapic to see what would happen. Still it either wouldn't make it to the initramfs or nano didn't exist? Then I remember reading that people suggested removing all devices like usb devices plugged in etc etc, just base min, keyboard, mouse, monitor. I also thought I would try a different sata port as my motherboard has 4 total, 2 of them are built into the ICH5R and 2 are on a promise controller. I had the windows drive in the promise port and the other storage NTFS drive in the built in sata port. I thought maybe I'll not use the promise and just use the built in ones because I wasn't sure about support for the controller within the livecd. Still NOTHING!!! AWWWWWW. I have spent 3 hours total gogling and just booting live cd's and still nothing. So I happen to watch the output of it booting 1 time and it suggested trying irqpoll as a boot option and I thought, well nothing to lose. I get to the menu, click F6, edit the boot line like the above guide BUT also REMOVED quite and added irqpoll noapic nolapic AND I GOT IN!!!!!!!!! YES, I screamed as loud as I could and thought, persistance always wins out!!!!!!!!!! 

Let's recap some important things, at least for my situation.
-make sure you have bare min hooked to your computer: monitor, keyboard, mouse period! (i am surprised that it worked with the kvm. i also was about to try and remove 1 of the optical drives so Ubuntu had to check less hardware)
-maybe change bios to defaults, some have reported that changing bios agp to 4x instead of 8x helps but I don't have that option in my bios. nor did I have an option for fast writes which I have also read works if you DISABLE it.
-use controllers that you know are supported by Ubuntu or the native ones (in my case I had a promise sata controller as well as a RAID ide controller built into my mb, DON'T use these, try the ones built into southbridge if you can)
-At the boot screen where it says the following: Start or Install Ubuntu, run in safe graphics mode, Check CD, boot first hard disk, memtest etc etc (see this link for awesome guide with pics: ([https://wiki.ubuntu.com/EdgyKnownIssues/5961](https://wiki.ubuntu.com/EdgyKnownIssues/5961), follow the guide BUT also delete "quite" and add these options if that guide alone didn't work. irqpoll noapic nolapic. so the final end of the line would be: .............../ram rw irqpoll noapic nolapic -- break=bottom (NOTE: the "dots" just represent the begining of the boot line that doesn't need changing). There are also other options that may work if these didn't. you can also try: 
acpi=off
pci=irqroute
xmodule=vesa
vga=normal
vga=771
pci=irqroute
framebuffer=false

You should end up in Ubuntu Edgy Eft Live CD Environment!!!!!!! YEAH

There are also so many guides out there for various situations where certain things didn't work for this bug (there is also more than 1 bug so I am going to post 1 and also post the bug report to reference.
-ATI X700 on a Asus laptop Turion Amd: [http://linuxmint.com/forum/viewtopic.php?p=8065](http://linuxmint.com/forum/viewtopic.php?p=8065)
-https://launchpad.net/ubuntu/+bug/67487

(NOTE: I haven't tried to install just so that everyone realizes this, this is all only to run a live cd. So, once you're install finishes and it tells you to remove the cd and it reboots, once grub appears, you can edit that boot line also by hitting E again, just use the same options and do that same thing again using "vesa" to get into your graphical environment. Then you can install another driver or whatnot. I might suggest ENVY, it worked wonders for my GeForce 6200 but I can't speak for ATI cards as I didn't install Edgy onto this machine. This is my winbloz xp pro box, only using it to troubleshoot friends windows install. Long story short my main ubuntu box is in pieces cause I need to install the E4300 and ASRock 775dual-VSTA motherboard I just bought to replace a Celeron 2.66 and Foxconn MB both of which worked fine I am just a computer freak. I can't wait!!!! GOOD LUCK TO ALL. We should maybe sticky this if something like this isn't already!!

---

### Post by Gelinder on 2007-04-05
I managed to install Ubuntu 6.10 now but I still have the grafical errors, I went for another version of the nvidia driver (second newest, cant remeber the number) and now the system crashes on boot, I get an error saying it cant start the x server. When I press ctrl+alt+f1 I see reports of lots of PCI errors, then it sais:

Starting up ...
[17179570.116000] PCI: JMB36x: Enabling dual function on 0000:03:00.0
[17179570.128000] PCI: Cannot allocate rescource region 0 of device 0000:03:00.0
[17179570.128000] PCI: Cannot allocate rescource region 1 of device 0000:03:00.0
[17179570.128000] PCI: Cannot allocate rescource region 2 of device 0000:03:00.0
[17179570.128000] PCI: Cannot allocate rescource region 3 of device 0000:03:00.0
[17179570.136000] PCI: Error while updating region 0000:03:00.0/0 (0000a008 !=00000000)
[17179570.136000] PCI: Error while updating region 0000:03:00.0/2 (0000a008 !=00000000)

Ubuntu 6.19 commando tty1 (where commando is what I named my computer)

commando login:_

my normal log in does not work

---

### Post by dannyboy79 on 2007-04-05
did you try to do what I suggested by adding break=bottom at the end of your boot line and then do what is suggested bye trying out the vesa driver just so you can get in the xserver? you need to show us the output of

sudo cat /home/username/.xsession-errors

and or 

sudo cat /var/log/Xorg.0.log

and

sudo cat /etc/X11/xorg.conf

good luck.

---

### Post by Gelinder on 2007-04-05
Yeah, I gave up trying to install 7.04, this is after I have installed 6.10 x86 and the nvidia driver wich I installed with Envy (driver installation program).

The problem is I cannot set my resolution to 1920x1200 with vesa drivers. Also moving windows around or scrolling is hardly doable. This is why I tried installing 7.04 hoping it would give me better results.

Now I'm back on 6.10 since I can get that to work atleast. But trying to install nvidia drivers results in above problems.

---

### Post by dannyboy79 on 2007-04-05
and you said you tried Envy? did you ask tseliot for any suggestions? he is the author of Envy. Also, maybe your card is just so new, that it's not supported yet? did you try the nv driver? just change vesa to nv and see how that goes. according to this article/review ([http://www.phoronix.com/scan.php?page=article&item=582&num=1](http://www.phoronix.com/scan.php?page=article&item=582&num=1)) the 8800 GTX is supported in  linux. also, here is a forum where a guy states that he got the 8800 GTS working with 9746. ([http://www.phoronix.net/forums/showthread.php?t=1377](http://www.phoronix.net/forums/showthread.php?t=1377)) good luck

---

### Post by Blackforge on 2007-04-06
For 8800 users, I would definitely recommend Sabayon Linux (which is based on Gentoo).  This is the only one I've tried that has a working Nvidia driver for my 8800GTS "out of the box".  I currently have a triple booting system (Vista, XP, Sabayon) using EasyBCD and Vista's bootloader.  It's running on a 8800GTS with a Dell 3007WFP at 2560x1600.  Didn't even have to mess with xorg.conf.

[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

This is a installable LiveCD or DVD too..

---

