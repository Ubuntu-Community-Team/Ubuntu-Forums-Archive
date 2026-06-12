---
title: "Upgrading to Grub 2 in ubuntu 9.04 w/dual Boot windows linux"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by blitzracer on 2009-11-24
Upgrading to GRUB 2 in Ubuntu 9.04 with a Windows and Linux multi Hard Drive dual boot

    I searched hi and I searched low for instructions on how to upgrade to grub 2 on my computer, after quite a bit of searching I found the website listed below which helped more then all the tutorials combined, Its a great Idea to understand the new system before diving into Grub land and killing your MBR (master boot record) before it even knows what the heck just happened. I even had to reinstall my Linux os since I messed up. But here is the proper way to do it, the process is mostly similar for single harddrive computers, but this is for a dual boot system with Windows on one drive (in my case the First) and Linux on the Other (the second duh!)  this dual booting circumstance was difficult to find someone else with a tutorial with my issue so here it goes...

heres that website I was talking about isnt ubuntu forums great for ubuntu help!  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


first you have to install it, I used the Human method and just went into synamtec and searched GRUB then checked the box. It downloads... it installs... HEY LOOK GRUB 2!

sorry its not that easy, at this point theres a bit of work and paitience involved.

Fixing ERROR 11 on first Grub 2 boot

When you chainload into grub 2 after installing grub-pc (I assume its the same as grub 2 in synamptic in this regaurd) find the kernel you usually boot from and press "E" then find the line "root 5cbc6-86b6 blah blah blah" it shoud be very obvious there should only be two, the point is it shoud have root and then a bunch of numbers after it. I just said a lot to tell you that all you have to do is edit this line to say "uuid numbers blah blah blah" 

it should boot after that to your Linux login or desktop (whatever your case)
go to Kernel and type 

!WARNING! in case youre thinking about typing the next command in and then rebooting without reading ahead (im guilty of it) DONT REBOOT UNTIL I SAY "REBOOT" !WARNING!

sudo upgrade-from-grub-legacy

but dont restart yet, if you do you will get an error 15 aka missing file (THE MISSING FILE... THE BOOT RECORD!!) and that requires a Karmic CD, 9.04 wont work. You can find this tutorial elsewhere, I never messed with it after I fried my MBR and had to reinstall Linux 9.04 to get it working again.

if your like me and it doesnt ask for you to pick a harddrive then you have to do this a different way.

heres what my termial did after sudo update-from-grub-legacy

    :~$ sudo grub-install –recheck /dev/sda
    [sudo] password for $USERNAME:
    Installation finished. No error reported.

    This is the contents of the device map /boot/grub/device.map.
    Check if this is correct or not. If any of the lines is incorrect,
    fix it and re-run the script `grub-install’.

    (hd0)   /dev/sda
    (hd1)   /dev/sdb
    (hd2)   /dev/sdc

I used that little computer between my ears and figured hd0 referred to the one with the MBR so, the fix was simple. change the HD section to read

    (hd0)   /dev/sdb
    (hd1)   /dev/sda
        (hd2)   /dev/sdc

yours may be different, you kind'a have to know your system for this part.
but take notice that I changed hd0 to "/dev/sdb
and hd1 to read /dev/sda

at this point I was crossing my fingers and sweatting bullets, but after this I finally REBOOTED phew I said it, now you can reboot. It will boot into Linux, but windows still neeeds some fixin. I figured this part out on my own by accident. since I couldnt find anyone with a tutorial covering my specific boot setup (although I did find one on when the computer has 2 Hard drives but uses one as file storage and the other for the operating systems. which looking back can be fixed this way too) 

FIXING THE WINDOWS BOOT PROBLEM (or there lack of...)

I was sitting on my computer trying to fix the windows boot by using the windows cd and reinstalling the MBR, this has problems since it takes over the MBR and grub needs to be reinstalled, but that isnt as simple as on grub legacy. I restarted after working in the windows console command on the cd it didnt work so I went to the windows entry and clicked e to edit the command line. it "read boot from device (0,1)" or something like that I out of curiosity though "hmm that doesnt look right" and proceeded to change it to read (1,0) then booted with ctrl-X Eureka! it worked. this change was not permenent though and it needs to be changed in the grub.cfg file.

reboot from windows into Linx and follow the next steps


Type this command to access it and make grub.cfg writeable.

sudo chmod +w /boot/grub/grub.cfg
then
gksudo gedit /boot/grub/grub.cfg

if in root the file WILL still default itself at next "Sudo update-grub"
unless you use this command. 

find the windows entry 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7" {
    set root=(hd0,1)
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

and fix "set root=(hdx,y)" 
 to the proper number.
x being the hard drive 0= hd 1 1= hd 2 etc
y being the partition 1 being the first partition so on and so fourth. 

(I think os prober finds the old grub  menu.lst file then takes the hard drive map off there not converting it to the new format) in my case it was as easy as changing it from Hd(1,0) to (0,1)
since my windows is on the first hard drive first partition this is the format it must be. 
with old grub (1,0) meant the same thing but it was changed (why I dont know)

now highlight it as shown below with corrected hd coordinates

menuentry "Windows 7" {
    set root=(hd0,1)
    chainloader +1
}

make sure you get the entire entry ending in "}"

now go to etc/grub.d and remove the Os Prober file ( sudo Nautilus) and put it somewhere safe so you can use it for whatever reason. It has to be removeed and your windows boot saved as a custom entry or the next time grub is updated it will erase your fix. Now Paste this entry into your 40_custom file just below the example text 

like this: 

#!/bin/sh
exec tail -n +3 $0
# This file is an example on how to add custom entries
menuentry "Windows 7" {
    set root=(hd0,1)
    chainloader +1
}


This way its permanent.

now 1 more step. 

sudo update-grub
or 
sudo update-grub2 

both do the same thing 

To set your default boot go to /etc/default/grub and use the command "sudo gedit /etc/default/grub" or the GUI way of "sudo nautilus" and then browse to the file
remember the first entry will be selected if "0" is put there, the second if "1" is typed so on and so fourth

Quick note: remember this last command, it will be very useful when you want to add splash images and stuff!


now youre back in business sporting a linux windows dual boot!

---

### Post by phillw on 2009-11-24
drs, the author of that and other how-to's has done a stirling job of all things Grub2. 

You may also want to bookmark [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
(not one of his) and also [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

He's a real nice guy & supports and answers questions from anyone with queries about Grub2. (Yeah, so it makes him blush)

Oh, and if you fancy a giggle you can see him sorting out my mess-up - he has updated the instructions since that one :p

That's over here --> [http://ubuntuforums.org/showthread.php?t=1331465](http://ubuntuforums.org/showthread.php?t=1331465)

I did, however, learn a lot about Grub2 - lol

Oh, and for things FireFox - lovinglinux keeps an excellent area over at [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

They're both really nice guys.

Regards,

Phill.

---

