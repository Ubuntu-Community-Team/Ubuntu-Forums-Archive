---
title: "HOWTO: get through the infamous Unable to mount root problem."
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by Patrick-Ruff on 2006-06-22
hey all, I decided to write up a little howto for those that have this monotonous issue ** in dapper**... at the first installation screen, where you have your install types... select safe graphical installer, then hit f6 before hitting enter, then you should see a bunch of code, add ```
 root=/dev/xdan   ** remember, these are variables, x, n ** 
```

x=type of hard drive
n= hard drive number

now with the x variable, your going to have either an h or a s, or maybe something completely different, depending on what kind of hard drive your using,  or if your using a usb flash stick for ubuntu, etc. if you have previous versions of Ubuntu, your type of hard drive will be in /dev/. 

now with the n variable.  thats the number of the drive, often it would be 1. so say you have a sda hard drive..
it would look like the following

```

a bunch of code------- root=/dev/sda1

```
then you would hit enter, and after install, you will receive an error on restart, unable to mount root.

do not give up! here is my particular resolution to this, edit your menu.lst through grub, you have to edit it again after you boot to save the changes.  so, the common problem I saw with this is, it said SDA but it didn't identify a number. so I changed it to root=/dev/sda1 instead of root=/dev/sda

first off, to do this, in the grub menu, you hit escape first of all when you see the 2 seconds of grub, then you hit e as of selecting the os you intend to boot, then you hit e on the line that you see a bunch of stuff about root= and such. 

note: you will have to hit the right directional button to see the rest of the text on this line, it often wont show all of it just from looking over it. 

put in the necessary information, then hit B while selecting THAT particuhar line **DO NOT** hit escape after adding this info, unless your getting back to the menu.lst area, once you get back to the menu.lst area, select the line of code you edited, and hit 'b'. you shoudl boot up correctly, then your gonna want to do the followign

```

sudo gedit /boot/grub/menu.lst



then your going to want to change the necessary information (its pretty straight foward if you look at it) 
to sda1 instead of sda

```

all the hard drive info used in the examples is what I did for my situation, if this didn't work for you, and you have a remedee that happens to work for your particular issue, please feel free to add it and I shall  edit my post.

another note: unplugging flash drives, iPods, etc. help with the installation process, prevents confusion and all that, after you get your menu.lst set up and everything, you should have no issues keeping USB-type drives plugged in.



good luck

---

### Post by Patrick-Ruff on 2006-06-22
has this worked for anyone else?

---

### Post by Patrick-Ruff on 2006-06-23
I would like to request this be sticky unless someone objects...

---

