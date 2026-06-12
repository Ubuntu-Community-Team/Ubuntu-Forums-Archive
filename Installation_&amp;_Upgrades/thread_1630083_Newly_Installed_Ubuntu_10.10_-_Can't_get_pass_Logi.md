---
title: "Newly Installed Ubuntu 10.10 - Can't get pass Login Screen"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by yarniwre on 2010-11-24
**DAY 1**

my OLD unit was Win XP SP2
i installed ubuntu 10.10 desktop, from cd, on it
(NOT DUAL BOOT)

==========
[COLOR="Red"]ECS P4M800-M
P4 - 1.8 GHZ
1x1GB + 1x512MB RAM
80 GB HDD[/COLOR]
==========

i had no problems with the installation, no errors

[COLOR="red"]now for the problem:[/COLOR]
when i purposely login wrong user/pass, it says "Authentication Failure"
when i login my correct username & password
after i login my username & password, the screen turns black for a few seconds and returns to login screen

i tried the LiveCD and thats what also happens i input user & pass for LiveCD( user: ubuntu, pass: ), screen turns black and returns to login screen

[COLOR="Sienna"]also i cant access terminal when i press ctrl+alt+f1-fN
when i press it, the upper half it displays some random red vertical lines
in the bottom half it shows the desktop bg[/COLOR]

[I]-- solution offered from ubuntuforums.org --
Try booting up in recovery mode. Hold down shift during boot-up, when you see the grub menu, choose the recovery option with the most recent kernel (closest to the top, make sure it says "recovery")

When it asks you how you want to proceed, choose to enter a root console with networking. 

From there you can try logging in or entering the command "startx" and see if that works.

I had this problem once because I uninstalled ubuntu-desktop
So try "sudo apt-get install ubuntu-desktop" If "startx" doesn't work.
---------------------------------------------[/I]

now, i get stuck in the boot menu, i cant move up, down or 'e' or 'c'
it seems to hang up when it show the boot menu


**DAY 2**
i installed 10.04, from cd, and the same thing still happens in login and boot menu
maybe my unit is incompatible?
after i installed 10.04, when the cd tray ejected on its own my whole screen was filled with an "i/o error" in sector

ill try to reinstall again and put the actual error here
*>> [ 2504.698873 ] end_request: I/O error, dev sr0, sector 507136*
thats one of 'em, the whole screen is filled with them.


**DAY 3**
i tried to install Win XP SP2 again
when i boot up it shows "Boot from CD: Press any key to boot from CD....", then i press enter
there a blinking underscore, in the upper left, in a black background for a few seconds and then boots up ubuntu

i tried to use KillDisk(Free) but it hangs up, just like the boot menu i cant move up, down and enter to choose an option
and then im thinking i can't use killdisk because it is for NTFS, am correct?

**DAY 4**
[I]ANOTHER = another fresh installed 10.04, my same cd, in another cpu which boots up with no problem and doesnt ask for user/pass because i selected automatic login

MINE = my 'problematic' hdd which can't enter desktop in my cpu[/I]

now i inserted ANOTHER in my cpu and it gets the same problem. asks for user/pass and cant go to desktop

now i inserted MINE on ANOTHER's cpu and it boots up properly and doest ask for a user/pass

======================================

[COLOR="DarkRed"]now i dont know what to do.
i can accept the fact that i can't use ubuntu, on my cpu, but i still want to know why.[/COLOR]

---

### Post by Zookalicious on 2010-11-24
Try booting up in recovery mode. Hold down shift during boot-up, when you see the grub menu, choose the recovery option with the most recent kernel (closest to the top, make sure it says "recovery")

When it asks you how you want to proceed, choose to enter a root console with networking. 

From there you can try logging in or entering the command "startx" and see if that works.

I had this problem once because I uninstalled ubuntu-desktop. So try "sudo apt-get install ubuntu-desktop" If "startx" doesn't work. 

Let me know how that works for you or if you have questions .

---

### Post by wojox on 2010-11-24
[How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by yarniwre on 2010-11-25
@Zookalicious & wojox: thanks for the quick replies
now, i get stuck in the boot menu, i cant move up, down or 'e' or 'c'
it seems to hang up when it show the boot menu


===
[COLOR="Navy"]i installed 10.04 and the same thing still happens in login and boot menu
maybe my unit is incompatible?
after i installed 10.04, when the cd tray ejected on its own my whole screen was filled with an "i/o error" in sector[/COLOR]

ill try to reinstall again and put the actual error here
 >> [COLOR="Red"][ 2504.698873 ] end_request: I/O error, dev sr0, sector 507136[/COLOR]
thats on of 'em
===

my mobo is **ECS P4M800-M**
im thinking this is hardware incompatibility

---

### Post by yarniwre on 2010-12-10
up - i really want to know whay the problem is even if i can't fix it

---

### Post by Zookalicious on 2010-12-10
Hey yarniwre sorry for the huge delay, exam time where I'm at. That error message sounds like there is a problem with the disk. Someone can correct me if I'm wrong but [COLOR=Red]dev sr0 [COLOR=Black]refers to the CD media. and I/O errors usually means that the computer can't read part of the disk (Can't tell if It's an on or off). Are you making sure to verify your iso's and disks after downloading and burning them? If you haven't already verified that, take a look at the md5 hashes and see if they are the same. (Sorry, let me know if you can't figure out how to do that, and I'll write it up quick, I'm just rushing a bit now because I have a BioChem midterm tomorrow :P )

If somewhere along the line the installation media got corrupted, that could explain why your installations are failing.

EDIT: A quick google search showed up that there are other people who are using your motherboard adequately with Ubuntu, so hopefully we can scratch that off. 


[/COLOR][/COLOR]

---

### Post by yarniwre on 2010-12-12
@zookalicious

i did a little experiment. im not sure if it counts to anything

**DAY 4**
-----
[I]ANOTHER = another fresh installed 10.04, my same cd, in another cpu which boots up with no problem and doesnt ask for user/pass because i selected automatic login

MINE = my 'problematic' hdd which can't enter desktop in my cpu[/I]
-----

im sure of my user/pass because if it's wrong i get the normal "Authentication Failure" message from ubuntu

now i inserted ANOTHER in my cpu and it gets the same problem. asks for user/pass and cant go to desktop

now i inserted MINE on ANOTHER's cpu and it boots up properly and doest ask for a user/pass (also set to automatic login)

---

### Post by Swagman on 2010-12-12
Are you entering your username in lowercase ?

---

### Post by yarniwre on 2010-12-12
> **Swagman said:**
> Are you entering your username in lowercase ?

yes i am :)

---

### Post by erikst on 2010-12-19
maybe not the same error but my intenal LCD screen goes nuts but a also connected an old CRT monitor on the external video port and this wworks with fine.

erik@NAS:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

if not the same problem - can someone help me?

---

### Post by mikymro on 2011-01-13
Heya! This is my first post for fixing troubles with Ubuntu. I have solved a lot of problems through a lot of research on this forum, but now i am stuck...
@ [yarniwre]("http://ubuntuforums.org/member.php?u=1193899"): I have the exact same problem as you. But mine started a little bit different.
I had on my computer a nvidia graphic board. i took it out and i plugged the monitor into the on-board graphic card 
lspci | grep VGA 
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)

When i restarted i got to the tty console. i logged in, i tried startx, nothing...
I tried reconfiguring, nothing, it said that it can't load the drivers from xorg.conf. Then i found the name for the driver, which was openchrome or something. i edited the the xorg.conf file with some more lines, and so now the x works, but when i try to log in the screen turns black and then the login appears again. when i try the Live-Cd, it keeps saying authentication failure. And if i try to go to the tty1 using Alt+Ctrl+F1, the screen turns black with some blu blurry things on top!

I have entered the grub menu, using the Shift key and entered the recovery mode and from the second menu i chose failsafeX. it logged in without any prompt and everything is ok....
I can't display the errors or my xorg.conf because i am on another pc now.... cursed!
So, i guess i am subscribing to your post with the same help cry!

---

### Post by mikymro on 2011-01-14
NEXT DAY!

I have managed to edit the xorg file from recovery mode, by copying the contest of the xorg.conf.failsafe or something. Now i can log in normally, but the main problem is that i can't start the network..... cursed!!!!
And i can't do a fresh install because i still have the problem with the authentification failure thing... so... we're almost back to square one. any help? any luck ... anyone???

LATER EDIT

It works! The network and the display... somehow. I don't have 3d suport, the compiz thingy is not doing his thing but i guess this is what you expect from a on-board graphic card.
Here's the content of the xorg.conf file:


Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

And the /etc/network/interfaces file:

auto lo
iface lo inet loopback

iface eth0 inet static

Off-topic:
So, i hope i can still be helped about the 3d somehow. Thanks and have a very trouble-less year everyone!

---

