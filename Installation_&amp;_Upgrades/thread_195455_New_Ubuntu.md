---
title: "New Ubuntu"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by Fittersman on 2006-06-12
ok i have breezy or worty installed (whichever is newer) and i just downloaded the new one 6.06 (its an iso image if thats alright) and i want to know how to use it, ive put it in the cd drive and it doesnt auto load when i restart so i really dont know what to do.

---

### Post by kb3hkg on 2006-06-12
if it doesn't auto load then it is possible your computer isn't set to check cd drive first, either change that in your bios or press F key for boot options, usually F12 or F8.

---

### Post by Fittersman on 2006-06-12
i tried, but when loading bios it says that it fails, so i dont know what to do. 

it did take alot of configuring to get the old one to work, i had to go throught hte black screen alot to get the pictures and stuff and alot of other work so if you could help me but allow it to keep the old settings somehow that would be sweet

---

### Post by kb3hkg on 2006-06-12
if you still have the old one installed you can just do an upgrade, you don't need a cd for that at all in a terminal just type the command 

gksudo "update-manager -d"

this will give you an option to upgrade the full system to dapper if you already have the newest update manager otherwise you'll have to get that first.

---

### Post by confused57 on 2006-06-12
[QUOTE=kb3hkg]if you still have the old one installed you can just do an upgrade, you don't need a cd for that at all in a terminal just type the command 

gksudo "update-manager -d"

this will give you an option to upgrade the full system to dapper if you already have the newest update manager otherwise you'll have to get that first.[/QUOTE]

Try the above suggestion first.
Here's a tutorial on burning an iso:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by Fittersman on 2006-06-14
when i type in the gksudo "update-manager -d" i get a popup that says...

It is not possible to upgrade all packages....

The following packages are not upgraded:
cpp
cpp-4.0

and in another window it says the system is up to date, but i only have breezy or warty (whichever is newer) so maybe if i get this update manager thing, but i dont know how and is ubuntu compatable with the psp system because i have a 1GB memory card and i could use that to transfer files from windows to ubuntu because ubuntu cannot detect my modem. Basically im just updating to see if the modem will work with the new one.

---

### Post by rcarring on 2006-06-14
If its a winmodem, possibly not. But try it anyway =D

If you are running Breezy you'll need to update the update-manager.

---

### Post by Fittersman on 2006-06-14
Where do i get this update manager

---

