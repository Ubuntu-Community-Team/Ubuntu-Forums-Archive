---
title: "Ubuntu wont install"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by istealth shadow on 2013-02-23
i have Ubuntu 12.10 x64 on my laptop because its amd and 4gb ddr3 ram  and it works and is dual booting with windows 7. that's what im writing  this post on.

i have a desktop PC x32 (Intel processor) so i got a Ubuntu 12.10 x32 ISO and burned it to a disk to install.
(btw  this is what i did with my laptop so no wubi.) then i booted it up and  the PC was booting up Ubuntu then there was a kernel panic. i attached a  photo of it.

my tv isnt apple tv that is a sticker it is dmtech  lol. my desktop pc runs on windows 7 ultimate x64 (same as laptop) but  when i used x64 ubuntu it works on my laptop but on my desktop it  started flashing white for a long time then loads of words would scroll  down the screen mostly like f's and then a red/black screen then a black  screen with a white bit on it. WTF!!! so i didnt try that again. i  tried unetbootin on a usb flash drive (sandisk cruzer 16gb and it didnt  work, did the same) also the ISO used was the same x32 bit one.

---

### Post by sanderj on 2013-02-23
Your pic is out of focus, so I can only guess: does it say "kernel panic - not syncing - attempted to kill init"?

If so, did you google that?

Does the same Ubuntu CD/USB-stick boot in another system? If not, the problem is CD/USB-stick. If it does, your not-a-Mac system is the problem

---

### Post by istealth shadow on 2013-02-23
yes it says "kernel panic - not syncing - attempted to kill init"
but idk what it means and don't understand the google searches.
ill try to burn the DVD again and see what happens.
i use imgburn and the iso is called:

ubuntu-12.10-desktop-i386.iso

its 753 MB (windows 7)

EDIT: before burning ill try it on my laptop and see if it works

---

### Post by istealth shadow on 2013-02-23
my laptop received a kernel panic too with the DVD. 'the corrupt one' 
also, i didnt try the usb on my laptop but the ISO is the problem because unetbootin i did a check on that and it said error in one file.

---

### Post by sanderj on 2013-02-23
In my experience, burning a CD/DVD is more reliable than writing a USB stick.

So:
- download a fresh .ISO
- check the md5 checksum
- if correct, write it to CD/DVD, with low speed 
- boot from the CD/DVD

---

### Post by istealth shadow on 2013-02-23
ok ill do that but btw the unetbooting also KP'd when i tried it. downloading the ISO now.

x32 bit 12.10 ubuntu.

---

### Post by istealth shadow on 2013-02-23
[http://youtu.be/mVDh8JTd61k](http://youtu.be/mVDh8JTd61k)

it didnt work i uploaded the results to youtube.

imgburn made me burn it at 4x speed 
and i downloaded a fresh iso x32 ubuntu.

---

### Post by istealth shadow on 2013-02-24
bump

---

### Post by sanderj on 2013-02-24
So: you have two systems, and a few different Ubuntu-CD/DVD's, and none of that can succesfully live-boot Ubuntu?

---

### Post by istealth shadow on 2013-02-24
no.

EDIT: actually, i have this x64 disk of ubuntu 12.10 that i used to install on my laptop so i have ubuntu on my laptop but i used that disk on the other computer and it did the same as the youtube video.

EDIT 2: I have windows 7 ultimate x64 running on both computers too. so that rules out broken hardware etc.

---

### Post by istealth shadow on 2013-02-24
i use a seagate 500gb hard drive and its got non-RAID enabled because i had a 60gb hard drive plugged in but it was broken and the 500gb hard drive had windows on anyway, the 60gb one was broken i tried to get it to work like on saturday but i enabled RAID then the bios killed my computer because i tried to get it to run faster and i had to take the battery off of the motherboard to reset the bios then i went into the bios, configured it put the 60gb hard drive in the bin then it was non-RAID so i left it. then i config date/time then i load optimal defaults for BIOS then i restart. then i tried to install ubuntu.

idk this is what i did on saturday i dont know if it will do anything or not though, probably not. i don't want to just write bump again so i wrote this.

---

### Post by sanderj on 2013-02-24
You need stable hardware and a good CD/DVD/USB-stick to install Ubuntu.

I have the feeling you keep circling in the first phase, so I will unsubscribe now.

Sorry I couldn't lead you to installing Ubuntu.

---

### Post by istealth shadow on 2013-02-24
> **sanderj said:**
> You need stable hardware and a good CD/DVD/USB-stick to install Ubuntu.

I have the feeling you keep circling in the first phase, so I will unsubscribe now.

Sorry I couldn't lead you to installing Ubuntu.

what does unsubscribe even mean? i only made an account yesterday -.-

the dvd's are tescos DVD R

i will get the cpu-z specs!!!

OMG!!! my computers officialy dead it will NOT boot windows so yeah.

im not even the slightest bit bothered since the computer is like 6 years old. or at least the bios said 2007 when i reset it.

:-) the computer was crap so its good!:p

YES!! the computer works! i enabled RAID and it booted up. now its applying a windows update. Could that be the fix? Finding out now!!!

will post cpu-z specs.

---

### Post by istealth shadow on 2013-02-24
Intel Core 2 Quad Q6600

chipset via pt880 pro
southbridge via vt8237s
lpcio winbond w83697hf


bios
american megatrends inc
version p1.30
date 06/26/2007 (26/06/2007)

graphic interface
pci-express
link with x4 max x16

2gb ddr2 ram

nvidia geforce 8500gt 512 vram

thats the specs i belive that its a bios problem 6 year old bios -.-

i also am trying a ubuntu cd boot helper that could "help" lol.:p

[drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
Raw EDID:
Y00 FF FF FF FF FF FF FF 00 FF FF FF FF FF FF FF FF
YFF FF FF FF FF FF FF FF 00 FF FF FF FF FF FF FF FF

The system is running in low graphics mode
your screen, graphics card, and input device settings
could not be detected correctly. you will need to configure these yourself

RESULT!!!

its the NVIDIA graphics card!!!

[drm] nouveau 0000:02:00.0: DDC responded, but no EDID for DVI-I-1

if its talking about DVI, then what the hell because i use VGA

---

### Post by istealth shadow on 2013-02-24
i cant edit my post for some reason, but the screen keeps on flickering and going on and off.

off topic, but this is actually really fun for some reason. 

YOU have to wait a REALLY long time for a ubuntu window to show up.

 i clicked stay in low graphics mode for one session and the pc went crazy.

there is a nvidia geforce 8500gt (my graphics card) driver for linux x32 and x64

i would like to know if you can get ubuntu live dvd to boot this driver from its files, requiring another dvd i guess but its okay. i cant go into the desktop as it doesn't even get that far.

Thanks for any help you give.

erm, my pc is going mad

[        9 .           ]
[        9 .           ]
[        9 .           ]
[        9 .           ]
[        9 .           ]
[        9 .           ] all the way down the screen a few times then...
[        .           ]
[        .           ]
[        .           ]
[        .           ]
[        .           ]

i am going to reboot my computer in a few minutes as i don't want it to "explode" lol.
i know this is all the crappy graphics card's fault but this can be used for reference use.

---

### Post by MAFoElffen on 2013-02-24
> **istealth shadow said:**
> Intel Core 2 Quad Q6600

chipset via pt880 pro
southbridge via vt8237s
lpcio winbond w83697hf


bios
american megatrends inc
version p1.30
date 06/26/2007 (26/06/2007)

graphic interface
pci-express
link with x4 max x16

2gb ddr2 ram

nvidia geforce 8500gt 512 vram

thats the specs i belive that its a bios problem 6 year old bios -.-

i also am trying a ubuntu cd boot helper that could "help" lol.:p
v12.10 right? Read all of this post before starting...

When you burn the ISO on CD, select burn at lowest speed. When you first boot off it, it will have the first panel as a dark purple screen with a keyboard/person icon at the bottom...

At that panel, before it goes away,  press any key. That will bring up a low-res vga panel with the language popup. Select a language or press <Enter>. That will get you to the to the Advanced Install Menu.

At that Menu, arrow down to where it says "Check Disk." It will check the Install ISO for any errors and that your CD?DVD drive can read it. After that, Arrow back up the menu to Install.

While that menu item is hightlighted, press <F6> then arrow down to where it says "nomodeset". Press <enter>, then <Esc>. Press <Enter again to start the install.

At the end of the install, it will ask you to take out the disk and press enter to reboot... Before that (even before installing), go to this post:
[http://ubuntuforums.org/showpost.php?p=11491229&postcount=812](http://ubuntuforums.org/showpost.php?p=11491229&postcount=812)

...and print out the instructions. You will need to use those instructions to start the first time after the install, temporarily edit you grub menu and enter "nomodeset" into the bootline (You have nVidia graphics.) After it gets to the desktop, you'll have to go to system settings > software sources > last tab of that will be Additional Driver, where you will look for the driver that is "recommened" for your system. Hint- It should be "nvidia-current".

Tell me how it goes.

---

### Post by istealth shadow on 2013-02-24
> **sanderj said:**
> You need stable hardware and a good CD/DVD/USB-stick to install Ubuntu.

I have the feeling you keep circling in the first phase, so I will unsubscribe now.

Sorry I couldn't lead you to installing Ubuntu.

you were right, sanderj this is pointless and a waste of time now, yeah. its the stupid hardware. of course 6 year old hardware is not going to run. the pc should of been smashed apart already :) i can't believe that nvidia made such a crappy graphics card.

---

### Post by MAFoElffen on 2013-02-24
Yes, the Nvidia card. You posted about 3-4 postes before I got my one out... 

Slow down and breath...

Get the system installed. Install your video driver. The we'll see if the other is the monitor.

EDID is data in the monitor. Linux queries the monitor for that data to see if it can set appropriate modes to it. It it doesn't see that data (old monitor or bad/corrupt data in a newer monitor) then there are other ways to get around that... We have to have a working system first "to get around that".

---

### Post by istealth shadow on 2013-02-24
oh well, i guess the last thing i can try is to install ubuntu on a usb stick and boot it on the pc.

---

### Post by MAFoElffen on 2013-02-24
> **istealth shadow said:**
> you were right, sanderj this is pointless and a waste of time now, yeah. its the stupid hardware. of course 6 year old hardware is not going to run. the pc should of been smashed apart already :) i can't believe that nvidia made such a crappy graphics card.

Actually, the model you have is a good card,. Problem is that nVidia and a few others (AMD?ATI, etc) have video drivers that are not open source code... Ubuntu has packages for those drivers, but since they are proprietary and licensed code, they can't include them as a default to the install process. 

It's really just a legal hurtle. But the user can install it, so Ubuntu makes that fairly simple to do once you get the system started. And since it's installed by the user through a few more decisions, it then assumes that the user accepts the end-user agreement for that driver.

MS Windows does the same thing for using the specific nVidia and ATI drivers.

---

### Post by MAFoElffen on 2013-02-24
> **istealth shadow said:**
> oh well, i guess the last thing i can try is to install ubuntu on a usb stick and boot it on the pc.

Instead of using nomode set, following the more detailed directions of post #3 of the Graphics sticky in my sig line, use instead "nomodeset vga=791" that will manually tell the kernel to not use the edid, not pass kms and to manually put it into that VGA VESA mode.

---

### Post by MAFoElffen on 2013-02-24
Tell me if that works or not... There's another way if that doesn't work.

---

### Post by MAFoElffen on 2013-02-24
> **istealth shadow said:**
> oh well, i guess the last thing i can try is to install ubuntu on a usb stick and boot it on the pc.

After doing that. I think you'll find it has the same problems... And besides, you said you have an "old" PC. Is it new enough to boot from USB?

---

### Post by istealth shadow on 2013-02-25
somehow when i started up the live cd it said completing installation in 5 4 3 2 1

now i have to reboot as the white screen popped up.


*after reboot*

now im in the 

"TRY UBUNTU WITHOUT INSTALLING MENU"

im now trying nomodeset and vga=791.
ive noticed a slight better change in the resolution of the monitor :)

YES!!!! WE have ubuntu desktop!!! Well, at least the installer.:)

OMFG!!! ubuntu has resurrected my system!!! even before installing!!!! i discovered that there WAS a wireless adapter in there, but windows didnt even know/care.

ubuntu is installing :D 

apparently the only problem was that problem you described.

should i go to nvidia website to download drivers?

---

### Post by istealth shadow on 2013-02-25
Um, how do i boot the pc back up, the screen goes white, green black etc.

vga = 791 and nomodeset only work for one session -.-

this time, im gonna reinstall with same settings but when my computer turns off i will not reboot. i will wait in this thread to see what happens.

---

### Post by istealth shadow on 2013-02-25
i looked on the internet and tried typing into grub:
[B]GRUB_CMDLINE_LINUX_DEFAULT="nomodeset  vga=791"

but it didn't work and all that happened was nothing. i guess now that was because they were trying to open a cmd in arch linux but i dont know what arch linux is i guess its a distro but i only need to boot up the pc once to install a single driver then it will be done. but my ubuntu machine won't boot up and does the same thing as when i tried to boot up the live cd.

i don't know how to get nomodeset vga=791 while booting up. i tried typing just that into grub.

you hold shift to get into grub then click on e then i typed that in and it said like nomodeset does not exist or something like that.

i have absolutely no idea now how to boot it up.
[/B]

> **MAFoElffen said:**
> After doing that. I think you'll find it has the same problems... And besides, you said you have an "old" PC. Is it new enough to boot from USB?

somehow this post deleted itself so i will reply again.

it can do

cds 
dvds
usb
hard drive
floppy disk

---

### Post by arpanaut on 2013-02-25
Go here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Scroll down to [SIZE=4]**[FONT=System][SIZE=1]How to temporarily set kernel boot options on an installed OS[/SIZE][/FONT] **[/SIZE]

then boot and install the proper driver as directed in a previous post then reboot and things "should" work properly.

---

### Post by MAFoElffen on 2013-02-26
> **istealth shadow said:**
> somehow when i started up the live cd it said completing installation in 5 4 3 2 1

now i have to reboot as the white screen popped up.


*after reboot*

now im in the 

"TRY UBUNTU WITHOUT INSTALLING MENU"

im now trying nomodeset and vga=791.
ive noticed a slight better change in the resolution of the monitor :)

YES!!!! WE have ubuntu desktop!!! Well, at least the installer.:)

OMFG!!! ubuntu has resurrected my system!!! even before installing!!!! i discovered that there WAS a wireless adapter in there, but windows didnt even know/care.

ubuntu is installing :D 

apparently the only problem was that problem you described.

should i go to nvidia website to download drivers?
And did you install?

Once you installed, then when you first reboot, just after the BIOS messages finsh, press the left shift key. The Grub menu will come up. Quickly press the Down-Arrow key. That will keep the menu from dispeappearing. Arrow back up to the top line. Press the "e" key. It will get into an edit mode on that menu item. Arrow down to the first line that says "linux". Arrow over just past where it says "quiet splash". Put a space in a add "nomodeset vga=791". Hold down the "Ctrl" (control) key and press the "x" key. It should boot into the GUI.

That then works "temporarily" to get a gui on that session going, but remeber, you need to then install your nvidia driver once it "is" going...

Go the System Settings > Software Sources... In Software Sources, look for the Last tab, that says "Additional Drivers". Select NVidia Current, then select the "Activate" button. It will download and should install "nvidia-current" to your system, without you having to go to the commandline.

Got that?

---

### Post by istealth shadow on 2013-03-02
> **MAFoElffen said:**
> And did you install?

Once you installed, then when you first reboot, just after the BIOS messages finsh, press the left shift key. The Grub menu will come up. Quickly press the Down-Arrow key. That will keep the menu from dispeappearing. Arrow back up to the top line. Press the "e" key. It will get into an edit mode on that menu item. Arrow down to the first line that says "linux". Arrow over just past where it says "quiet splash". Put a space in a add "nomodeset vga=791". Hold down the "Ctrl" (control) key and press the "x" key. It should boot into the GUI.

That then works "temporarily" to get a gui on that session going, but remeber, you need to then install your nvidia driver once it "is" going...

Go the System Settings > Software Sources... In Software Sources, look for the Last tab, that says "Additional Drivers". Select NVidia Current, then select the "Activate" button. It will download and should install "nvidia-current" to your system, without you having to go to the commandline.

Got that?

sorry i forgot to respond but i got it working and its perfect now!!! i installed the driver and no more errors!!!
too busy to respond but this thread is SOLVED now.

---

