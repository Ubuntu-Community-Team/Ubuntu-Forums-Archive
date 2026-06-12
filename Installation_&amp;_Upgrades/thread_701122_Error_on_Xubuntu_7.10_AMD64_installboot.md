---
title: "Error on Xubuntu 7.10 AMD64 install/boot"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by NoobBen on 2008-02-19
Hi there Listen I'm a complete N00b when it comes to Ubuntu and have been using Windows since I was 6 so be kind :-)
I recently tried to install XUbuntu 7.10 AMD64 version using the alternate CD ISO that I burnt onto a CD (I did burn the image not the ISO file incase anyone is wondering) onto my PC:

-AMD 64 bit 3000+
-1 GB RAM
-160 GB HDD
-GeForce 6800XT
-TV Card
-External slot for 3G card
-WinFast mother board

When I install it, it runs perfectly and goes through all the menu's fine.
When I get to the option to patition the drive I choose the option that uses the whole hard drive and the installer formats and then installs Xubuntu on the HDD and when finished I'm asked to remove the install CD and reboot...
Once I reboot everything runs smoothly: it says it is loading the GRUB loader and then proceeds to the splash screen but at the splash screen it either completly loads and then hangs on a blank black screen or it does a error test or something similar and the final lines give me a similar error to this:

"des/sdl1 was not cleanly unmounted check forced"
and then gives a loading bar
and then the error "fsck died with force 3"
and reboots the PC

PLS HELP!!!
Thanks

---

### Post by jan de beuker on 2008-02-19
You could try this

des/sdl1
I think this shut be dev/sda1
This means first partion on first HDD
Fsck detected a failure on this hdd
During boot when the grub menu is on pres escape
Select the second option (recovery mode)
After booting you get a root terminal
Then type

umount /dev/sdb1

This will unmount the hdd

fsck /dev/sdb1

This will manually check the hdd

reboot halt now

this will reboot 

Mayby it will work but make shure you have the right id for the hdd 

Jan

---

### Post by NoobBen on 2008-02-19
Thanks Dude I'll try it tonight once I can get back to my PC :)

---

### Post by NoobBen on 2008-02-19
Hey there again- sorry i forgot to mention that I tried installing XUbuntu 7.10 but I also tried Installing Ubuntu Ultimate Gamers Edition (From the Feb PC Format magazine) and it runs the first window with the option to istall, memmory test, check CD for errors etc. but then when I enter the option to install it brings up the splash screen and after loading that goes blank...is this at all related to the problem I'm having with XUbuntu (maybe a HDD error or something) or is this the Black Screen of Doom every one seems to get with a AMD64/NVidia system?

Thanks again for your advise in advance and patience with the n00b :)

---

### Post by NoobBen on 2008-02-19
Hey there I tried the command lines you gave me using dev/sda1 and it reacted saying it is clean but but when I tried going into XUbuntu it just hanges after the splash screen again and when I go into recovery mode it gives me the errror same error as before and when it booted up the second time it says

"chown: failed to get attributes of 'var/log/dmesg': No such file or directory"
 and"
"chmod: failed to get attributes of 'var/log/dmesg': No such file or directory"

---

### Post by jan de beuker on 2008-02-19
Mayby this will help
In the recovery root terminal try this command

dpkg --configure -a

---

