---
title: "Ubuntu Install Wont Show Up at Windows Startup"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by ZainZXC on 2006-08-29
When My friend gave me a UBUNTU install disk to put up on my computer and showed me how to partition, I went home and when i put the Install cd in the install menu never showed up... so i tried with the 64-bit and the 32-bit versions and nothing so i spent like all day trying to install it!!](*,) ](*,) :mad: :mad: ... if anyone recognizes this problem plz post ASAP with a solution or tips thanks to all :) :) :-D :-D

---

### Post by reacocard on 2006-08-29
You probably just need to tweak your bios setting so your computer can boot from the CD. watch carefully right after you turn on the computer for what key to press, its usually something like F1 or delete. Then look for a boot section and put the cd drive before the hard drive. save the settings, reboot, and that's it!

---

### Post by atomkarinca on 2006-08-29
and even if you miss that part, install is on the desktop after the cd boot.

---

### Post by ZainZXC on 2006-08-30
Yeah... Im not really a techy and if i tweak the settings im afraid im gonna change something important and yes it is DEL... so if anyone knows what to change it will be really apreciated... THNX:-D :-D :-D :-D :-D:-D :-D :-D

---

### Post by randell6564 on 2006-08-30
Just look for something in your Bios that refers to 'Boot Sequence' or 'Boot order'.  Something like that.  Dont worry, if you goof, you can always go back in and reset it!  You want cdrom to be first in the order.

---

### Post by ZainZXC on 2006-08-30
I just gotta say thanx and can you tell me more about the cd during windows because i might not be able to do it and i wanna start it up from the cd itself and THNAX:-D :p :-D :p :-D :p :-D :p

---

### Post by randell6564 on 2006-08-30
> **ZainZXC said:**
> I just gotta say thanx and can you tell me more about the cd during windows because i might not be able to do it and i wanna start it up from the cd itself and THNAX:-D :p :-D :p :-D :p :-D :p

Not sure what you mean.  I'm thinking that you want to know how to complete the installation once that you begin correct?

If I'm right then the first question would be, do you want to keep your windows installation?

---

### Post by ZainZXC on 2006-08-30
well you see what i mean is someone prevously said that it possible to install it while on windows... aqnd if i can get the installation going i can do the rest like dual boot and partitioning it because my friend showed me how:-D

---

### Post by randell6564 on 2006-08-30
> **ZainZXC said:**
> well you see what i mean is someone prevously said that it possible to install it while on windows... aqnd if i can get the installation going i can do the rest like dual boot and partitioning it because my friend showed me how:-D

You Can NOT install it from your windows desktop.  You must reboot with the cd in your  cd drive.  Windows does not like Linux and will not allow you to do that.

When you reboot into the ubuntu installation, you will get plenty of options for partitioning.  Then towards the end of the installation, you will be given the option to install the grub bootloader to your MBR.  Depending on which installation cd that you are using, you might not get that option, but then ubuntu's default is to put grub on the MBR anyway.

Another thing.,Do you have any free space on your HD?  If Windows is utilizing your entire HD, then you will have to resize windows to make room for Linux.

---

### Post by ZainZXC on 2006-08-30
Yes... :shock:well someone earlier said that it possible to be booted from windows:shock:... and i will try to do the tweaking so thnx... if there is anything anyone wants to add to help me feel free and just give me some hints and tips... o and btw i have windows xp home;) ;) :p :p \\:D/

---

### Post by hakre on 2006-08-30
> well someone earlier said that it possible to be booted from windows
yeah, you can configure the windows boat loader to load the ubuntu installation next time you're booting. that way you won't need a install-cd so this might be handy if you've got no cd-rom drive. I guess that was meant. :wink: ([Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows))

---

### Post by ZainZXC on 2006-08-30
Yes... but i do have a cd drive... but what i meant is the while you are on windows u can go and install from there like with the cd in and all

---

### Post by atomkarinca on 2006-08-30
actually booting from cd is much more simpler (and i haven't heard anything about installing on windows). you press del on boot and enter "boot device" menu (usually something like that, you don't even have to look through the menus), change the first boot device to cdrom and then save & restart.

it boots from the cd and when gui is loaded you can double-click install on the desktop.

---

### Post by randell6564 on 2006-08-30
> **atomkarinca said:**
> actually booting from cd is much more simpler (and i haven't heard anything about installing on windows). you press del on boot and enter "boot device" menu (usually something like that, you don't even have to look through the menus), change the first boot device to cdrom and then save & restart.

it boots from the cd and when gui is loaded you can double-click install on the desktop.

What atomkarinka is saying Zain is what everyone has been trying to tell you.

It's really very simple, and I dont understand why you are trying to make it difficult!  Boot into the Live CD.  once you are at the Ubuntu Desktop, you will see an install icon there.  open it and BAM.,you are on your way!!

---

### Post by Super King on 2006-08-30
Couldn't he just press F12 or whatever it is to bring up a boot list, then boot from CD (without changing the boot order)?

---

### Post by randell6564 on 2006-08-30
> **Super King said:**
> Couldn't he just press F12 or whatever it is to bring up a boot list, then boot from CD (without changing the boot order)?
Actaually, I'll have to try that Super King!  Never heard of it though.

Be back with the results!

Though thats not a whole hell of a lot less laborious than changing the order in your Bios!

---

### Post by ZainZXC on 2006-08-30
ok yes everybody i got ubuntu started up but now theres another problem... when i was at the resize hd during the install because im going to dual boot windows xp and ubuntu i partioned my hd so 10gb was free for ubuntu... and after i made sure of that i closed it and then started the install again and selected use largest available space it said that it will delete my files. Now im not sure it means that it will delete that space and use it as Ubuntu or something else:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:  Well thanx with my first problem.

---

### Post by randell6564 on 2006-08-30
> **ZainZXC said:**
> ok yes everybody i got ubuntu started up but now theres another problem... when i was at the resize hd during the install because im going to dual boot windows xp and ubuntu i partioned my hd so 10gb was free for ubuntu... and after i made sure of that i closed it and then started the install again and selected use largest available space it said that it will delete my files. Now im not sure it means that it will delete that space and use it as Ubuntu or something else:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:  Well thanx with my first problem.

It will always say that!  It's just warning you that if you have any files on that free space, it will delete them.  If you are sure that you see 10Gb of free space, and that is what you selected for installation, then you are fine.

---

### Post by enopepsoo on 2006-08-30
I think I did see a linux distro once that  booted from windows.  I tried everything to get my old crappy computer working before I found Ubuntu (which worked on the first go).:-D 

Also Knoppix helped. :rolleyes: 

:KS

---

### Post by ZainZXC on 2006-08-30
Well These might be my last few words for now but all i gotta say is THANX!!!! :-D :-D :-D :-D :-D :-D :-D :-D . I would like to thank everyone that has posted something on and I really apreciate the help!

---

### Post by ZainZXC on 2006-08-30
Well i guess im back and with another problem. When i do the resizing i close it and go back to the beggining so i can use the "use largest space available" and when i selected that it said cannot partion something something... but i selected that anyways and when the "installing system" came up a few moments later its said something like cannot find root file.:confused: :confused:

---

### Post by randell6564 on 2006-08-31
> **ZainZXC said:**
> Well i guess im back and with another problem. When i do the resizing i close it and go back to the beggining so i can use the "use largest space available" and when i selected that it said cannot partion something something... but i selected that anyways and when the "installing system" came up a few moments later its said something like cannot find root file.:confused: :confused:
 You are not suppose to "go back" or no changes will take place!  Nothing will be executed until you get to the end of the partioning part of the installation.

---

### Post by ZainZXC on 2006-08-31
Ya i didnt go back i applied it then closed it. I started the installer again and when i did it it said the file thing wasnt found But my friend came back and fixed it for me.

---

