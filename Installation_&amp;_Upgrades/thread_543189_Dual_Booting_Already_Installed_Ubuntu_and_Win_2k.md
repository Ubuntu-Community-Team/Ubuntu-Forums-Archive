---
title: "Dual Booting Already Installed Ubuntu and Win 2k"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by blazerqb11 on 2007-09-04
Is there way I can edit my boot.ini file in windows to dual boot windows 2000 and ubuntu?  I have been looking around for a while and found a lot of information that was close to what I needed but nothing seemed to be right on.

I currently have ubuntu installed on the secondary master and windows 2000 installed on the primary master and I can boot to either by selecting the hard drive I want in the bios.

---

### Post by shane2peru on 2007-09-04
> **blazerqb11 said:**
> Is there way I can edit my boot.ini file in windows to dual boot windows 2000 and ubuntu?  I have been looking around for a while and found a lot of information that was close to what I needed but nothing seemed to be right on.

I currently have ubuntu installed on the secondary master and windows 2000 installed on the primary master and I can boot to either by selecting the hard drive I want in the bios.

Why don't you just let Ubuntu handle your grub?  It does a wonderful job of handeling it, and there is probably much more written on dual booting that way.  Setup your Ubuntu disk as primary and edit the /boot/grub/menu.lst to include your second hdd with Windows on it, and you will be all set!  Of course be very carefull in editing that file, you should back it up before making any changes to it.  I hope that helps a little, though it may not be exactly what you are looking for.

Shane

---

### Post by blazerqb11 on 2007-09-04
how do I edit text files from the terminal? and also any help with your suggestion would be much appreciated.  I would like to make windows the default boot.

---

### Post by shane2peru on 2007-09-04
> **blazerqb11 said:**
> how do I edit from the terminal? and also any help with your suggestion would be much appreciated.  I would like to make windows the default boot.

blazer,

To edit that file you need to do this:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

```
That will back up your file and then to edit it:
```

sudo gedit /boot/grub/menu.lst  

```
I'm searching the forums as I know there are some threads discussing how to do this and specifically with two harddrives.  You will have to map the second harddrive.  What ever you make sure you add your windows to the end of that menu.lst and then we can help you change the default to windows so that it auto boots into windows.  I will get back to you with those threads if I can find them.

Shane

---

### Post by shane2peru on 2007-09-04
blazer,

Ok, I couldn't find the specific thread I was looking for, but this thread here:
[http://ubuntuforums.org/showthread.php?t=541973&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=541973&highlight=dual+boot)
seems to be a good example to look at and read through.  It has the hdd mapping that you will have to use, or a similar setup.  I know you have Windows 2K, but for the menu, it isn't going to make much difference, you can just write in 2K instead of XP.  Hope that helps a little.

Shane

---

### Post by blazerqb11 on 2007-09-04
Thanks, I've got a dual boot working using grub now. 

The reason I wanted to use the windows boot loader is because while using grub the computer appears to hang for about 10-15 before starting up, is this normal?  Also it seems a little weird to boot from my secondary hd back to my primary, lol, that is not a big deal though.

---

### Post by shane2peru on 2007-09-05
blazer,

     Glad to be of help.  I don't know if it is normal for grub to hang for about 10 seconds or so, I don't reboot often enough to know that, or I don't notice, but that has to be easier than changing your bios every time you want to boot to the other OS. :)  That is a little odd booting off the secondary hdd, (that could be why it hangs a little) I have never had a two harddrive setup.  Did you get it setup to autoboot into 2K by changing the default number it boots to?  You don't want to put windows at the top of the list because the top gets rewritten when the kernel is updated in Ubuntu, and you will loose your Windows option out of the menu, and have to go back and add it back in, been there and done that before. :lolflag:

Shane

---

