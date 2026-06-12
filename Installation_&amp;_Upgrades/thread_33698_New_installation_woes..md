---
title: "New installation woes."
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by spiritunreal on 2005-05-11
So, i've reinstalled hoary, twice now. 

The first time it installed, booted just fine. GDM Came right up, I played around for a while got familiar with the filesystem I got a bunch of errors about some php or something. But it's not really important. Shutdown. The next day, it boots up, seems fine, I dont really..get any errors. Just goes through the whole start up, and then nothing. Blank screen...so i'm like WTF? I'm pushing buttons, movin the mouse around, nothing. 

So, I give up, reinstall. Boots up just fine, again, same ol same ole. I leave it running, I install a few things, change up the gdm, make it look alll pretty. Shut it down, I start it up the next day, nothing. Absolutely nothing. 

I'd rather not reinstall every time I'd like to use this. Anyone have any idea? 

Its on a 650 pentium III dell inspiron 5000. 128 ram, 40 gb freshly boughten hard drive.

Edit: 

So, apparently it is...kinda working. But, I think it's a problem with X? I'm pushing buttons hitting enter, and i'm noticing a faint noise, since it's on a laptop I barely heard it. But it was the error tone, so I typed in my login, and ...apparently logged in as the little hard drive light flashed. So..i'm logged in now, but...still no screen...at all. 

I'm thinking reboot in runlevel 1 or something and see what I can do

Double Edit (hoping for someone to chime in): 

So i've managed to login recovery mode via grub into root. Thankfully I enabled that earlier when it was actually working. But, I have no idea what to do now. Heeellp. The OS seems to be working just fine, with the exception that startx isn't exactly working file not found. Or something to that nature.

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=spiritunreal]So, i've reinstalled warty, twice now. 
[/QUOTE]

This is the Hoary section. If you want to install Warty post there. 


If you did, I would suggest installing Hoary though. Make sure you burn the ISO at a low speed. It has many fixes, since Warty was a first release.

---

### Post by spiritunreal on 2005-05-11
Sorry, it is in fact hoary. I downloaded and burned it just two days ago.

---

### Post by spiritunreal on 2005-05-11
Found what I was looking for . 

[http://www.ubuntuforums.org/showthread.php?t=1382](http://www.ubuntuforums.org/showthread.php?t=1382)

---

### Post by spiritunreal on 2005-05-11
Wait, no i didn't. Heeelp

---

### Post by poofyhairguy on 2005-05-12
I like that laptop. A friend of mine has one of those and I got it work great with Ubuntu by following the tip laid out here:

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsDell/view?searchterm=dell](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsDell/view?searchterm=dell)

And by putting 256mb RAM in it....

---

### Post by iron_spectre on 2005-05-19
Hi,

Totally new to linux here, but I have almost the same laptop (256 MB Ram) and the same problem.  I saw the note on the Compatibility page, so I changed to Suspend to Disk in the BIOS.  No help.  I reinstalled Ubuntu with the changed BIOS still nothing.  I tried to turn ACPI off, and adding "Suspend to Disk" to the menu.lst file as I found in the wiki, still a black screen.  I'm hoping this is something simple.  I am really new so if you can help in step by step instructions I would be grateful.

Help,
Please

---

