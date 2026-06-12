---
title: "Live CD freezes, and alternate miss CD-Rom drivers"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by oyroy on 2007-10-15
Trying to install Ubuntu on my desktop (got it on my old Dell laptop). Ive tried running the Live CD, but it just freeze just after choosing Run/Install Live from the menu. Flashes Loading Kernel swiftly, but then screen goes blank. Ive tried 7.04 64-bit Live CD, 7.10 64-bit Live CD and 6.06 32-bit Live CD (what my laptop is running). I tried using the nolapic and acpi=off commands too, but nothing worked. Burned out the 7.10 64-bit Alternate CD, and can start the text install, chose language, location and keyboardsettings, but it fails to find my CD-Rom, so I cant go any further. Says it needs drivers.

Some HW specs:

Asus P5W DH Deluxe
Intel Core 2 Duo E4300
Nvidia 8800 GTS 640MB
4GB DDR2 Memory
NEC IDE DVD-Burner

Some HDs:
150GB WD Raptor (SATA)
2x500GB Samsung Spinpoint (SATA)
200GB WD (IDE)
250GB Samsung (IDE)
Cant remember the exact names on the 2 last drives. Shouldnt matter for booting the live install anways. Ubuntu is going into a 50GB partition of the Raptor.

Monitors:
Samsung Syncmaster 245B 24"
Some old 17" crap as secondary

Regular usb mouse and keyboard

So, Ive tried 4 diff Ubuntu CDs, several of the suggested solutions, but still cant load Ubuntu. Im not an epic coder, but Ive had Ubuntu on my laptop for some time, so Im not a complete noob either. Shouldnt be that difficult to install it :(

---

### Post by Pumalite on 2007-10-15
When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

---

### Post by oyroy on 2007-10-15
Well, I dont have Ubuntu on my desktop at all. Only Xp and Vista. Which means I wont get a terminal, and I cant download any drivers. apt-get doesnt work from Ctrl+Alt+F2 when doing the text-based install, and nothing would be saved anyway when rebooting. Cant even get a terminal from the Live CD. 
All I got is 4 diff Ubuntu CDs, which aint working, and 2 versions of Windows thats both pissing me off :(

---

### Post by Pumalite on 2007-10-15
To boot Live CD try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by oyroy on 2007-10-15
As seen in the image attached, it didnt work so well. (Had to dig up an old keyboard as well, as my usb keyboard didnt work in initramfs). Just got the:
FATAL: Module piix not found

---

### Post by Pumalite on 2007-10-15
Install with Alternate CD and at the end of install, apply recipe in my first post.

---

### Post by oyroy on 2007-10-16
Well, as said, alternative CD does not find any CD-Rom drives, even tho the CD itself is running from it, and when using a terminal there it does not recognise either sudo, apt-get or any of the commands from that post.

---

### Post by Pumalite on 2007-10-16
You seem to have a Raid Array. (2x500 GB). Just in case:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Even if you are installing in different drive, I think Grub will have a problem installing itself in the Raid. As for CD not seen: fiddle with your BIOS. CD 2nd Master and set as 'Auto' in BIOS seem to work for some.

---

### Post by oyroy on 2007-10-19
I pulled out the cords on the raid-disks, but still not working. They are used for pictures and personal stuff, so shouldnt interfere anyway. 

As for the CD-Rom, it just wont get it to work. Tho, it seems its hanging a bit latley, so maybe its time to swap it out. I'll see whats I'll to over the weekend.

Is there any network install of Ubuntu maybe? So I can boot the install from CD, but take rest from online.It exists for openSUSE (which a buddy of mine is trying to make me install instead).

---

### Post by oyroy on 2007-10-22
Well, I managed to install Ubuntu. Seems my DVD-Burner was buggy. When I got a new one, I could use the alternative install just fine.

Got some more problems tho. Cant boot regularly (prob cause the nVidia drivers), but even worse, I cant get my network up and running.

DHCP autodetect failed when doing the install, so I chose to wait and configure later. Now, I cant get them running. I managed to get a semi-working graphical interface, but settings is screwed up. Problem is I cant access the Configurations->Network to set it up.

I took a couple of screenies of some commands I used to find out whats happening. Would be great if anyone knew how to get my network up and running.

---

### Post by oyroy on 2007-10-23
Mehh, something happened to thos thumbs. Pulled out 2 new ones, that should be readable.

Would be very grateful if someone could help me with this, else I might have to surrender and try openSUSE thats my buddy is bugging me about...

---

