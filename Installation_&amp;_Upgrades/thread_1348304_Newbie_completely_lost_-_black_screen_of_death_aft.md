---
title: "Newbie completely lost - black screen of death after Karmic install"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by gemdot on 2009-12-07
I've been using Jaunty since first switching to Ubuntu in September.  I don't pretend to know much about linux, but I've gotten by well so far with help from these forums.
I just hit the button to upgrade to 9.10, and the install seemed to go well.  The system rebooted, BIOS loaded, GRUB loaded, and a small white ubuntu logo appeared, and then the screen went black, save for two small dashes on the top half on the screen.
On restart I try to press ESC to enter grub menu, but nothing happens, as though my keyboard is not recognised.
 
I've been looking everywhere online for help.  Other people seem to have encountered this or a similar problem, but I can't find anything to help me through it, and I really don't understand what's going on.
 
Any help or direction would be so so welcome!

---

### Post by iponeverything on 2009-12-07
> **gemdot said:**
> I've been using Jaunty since first switching to Ubuntu in September.  I don't pretend to know much about linux, but I've gotten by well so far with help from these forums.
I just hit the button to upgrade to 9.10, and the install seemed to go well.  The system rebooted, BIOS loaded, GRUB loaded, and a small white ubuntu logo appeared, and then the screen went black, save for two small dashes on the top half on the screen.
On restart I try to press ESC to enter grub menu, but nothing happens, as though my keyboard is not recognised.
 
I've been looking everywhere online for help.  Other people seem to have encountered this or a similar problem, but I can't find anything to help me through it, and I really don't understand what's going on.
 
Any help or direction would be so so welcome!

I have to admit that I am always a bit gun shy when comes to the "upgrade" button. 

Grab a Ubuntu CD and boot from it. The choose the menu option that is something like "boot from partition".. Once you are booted from the disk, try a "sudo dpkg-reconfigure grub"..

Another thing you should try is to hit the left shift key so that the grub menu appears -- hit "e" go to the second line and hit "e" again -- then erase "quite splash" then hit return and "b" too boot. 

This will show the boot messages and you might be able to see where it is getting hung up.

---

### Post by gemdot on 2009-12-07
> **iponeverything said:**
>  Once you are booted from the disk, try a "sudo dpkg-reconfigure grub"..
 
Tried this, got no visible response.  Rebooted and the problem was still there.
 
> **iponeeverything said:**
>   Another thing you should try is to hit the left shift key so that the grub menu appears -- hit "e" go to the second line and hit "e" again -- then erase "quite splash" then hit return and "b" too boot. 
 
This will show the boot messages and you might be able to see where it is getting hung up.
 
I would love to try this, but I'm still having a lot of trouble pressing keys during bootup.  I have told BIOS to load from the cdrom, which is the only way I can alter the boot location (as in, no amount of key pressing during bootup will allow me access to the menu, or if it does I can't scroll, select or exit within the menu).  When exactly do I hit the left shift key/access the grub menu?  Is there anyway of getting to the grub menu without relying on key presses during bootup?
 
I'm kicking myself for not realising that the update button was the wrong way to go...  Damnit, I had a really nice OS once upon a time!

---

### Post by iponeverything on 2009-12-07
Boot from the cdrom again --
do:

```
gksu gedit /boot/grub/menu.lst

```

Change

```
timeout 
```

value to something like 10 or 15

Also change 
```
hiddenmenu

```

to:

```
# hiddenmenu

```

This should force the menu to show up. 

Also I gave you wrong key before, It should have been the escape key and not the shift key.

---

### Post by darkod on 2009-12-07
It might be video driver issue. Strangely it seems it can work in 9.04 but not by default in 9.10. Don't remember whether it was the exact problem but selecting the recovery mode from the grub menu and installing EnvyNG package helped some people.

---

### Post by gemdot on 2009-12-07
> **iponeverything said:**
> Boot from the cdrom again --
do:
 
```
gksu gedit /boot/grub/menu.lst

```
 

 
This gets me nowhere, I just get this:
[COLOR=purple](gksu:5192): GTK-warning **: cannot open display:[/COLOR]
 
As an update:  Somewhere along the way I've noticed that bootup now results in "Out of Range!" coming up on my monitor.
 
I am getting very nervous that I'm about to lose 900G worth of data!

---

### Post by iponeverything on 2009-12-07
> **gemdot said:**
> This gets me nowhere, I just get this:
[COLOR=purple](gksu:5192): GTK-warning **: cannot open display:[/COLOR]
 
As an update:  Somewhere along the way I've noticed that bootup now results in "Out of Range!" coming up on my monitor.
 
I am getting very nervous that I'm about to lose 900G worth of data!

use nano instead of gedit.

You Data is pretty safe.

---

