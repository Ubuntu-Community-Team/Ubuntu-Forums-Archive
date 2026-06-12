---
title: "Help Me With Grub Plz!!"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by mothafukaa on 2006-09-26
well, i love my ubuntu, but this is a family computer, and the rest of my family uses windows
so, i want to change my GRUB loader to run windows XP as default, instead of picking linux automatically after a few seconds
help me plzplz

---

### Post by orb9220 on 2006-09-26
Install this might help [http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)
Gui based Grub editor.
or
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by lukanium on 2006-09-26
$sudo nano /boot/grub/menu.lst
```

default         0   <-------- change this to your XP orders

## timeout sec  
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10   <-----change this to 0

```

---

### Post by turbojugend_gr on 2006-09-26
> **lukanium said:**
> $sudo nano /boot/grub/menu.lst

timeout         10   <-----change this to 0
[/code]

Well do not do this cause you will only be able to boot WINDOZ! SO change this to 2 or 3 so you have 2-3 seconds if ou wish to choose ubuntu.

---

### Post by mothafukaa on 2006-09-26
ok, thanks guyz, i tried this method : [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
and that didnt work, it said it couldnt find 
/boot/grub/menu.lst
so, i was gonna try this method...
[http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)
but, i cant get online with that machine when in ubuntu, and i dont have a home network installed at the moment, just my cable modem, which i switch between this PC, and the one i share with my family
(i dont have ubuntu on this PC because of some incompatibility)
(but thats irrelevant)
so i need to fix my internet problems

---

### Post by turbojugend_gr on 2006-09-26
OK, allready stated but I 'll make it clearer, do this in a terminal:
```
sudo gedit /boot/menu.lst
```
You should get a text file in the end of which there should be a section under the name of Windows XP Home Edition or sth relevant.

After the commented lines (those starting with #) you should enter the following lines :```
default *nUmBeR*
```

where *nUmBeR* put the number that windows hold in your list. That will make grub to boot into windows by default.

If you wish to shorten the time of waiting till boot too, you should also add this line:```
timeout *number*
```
where instead of *number* put the amount of seconds you wish grub to w8 for you to choose sth. Try putting at least 3 secs or you might end up not being able to boot anything else than windoz.

---

### Post by mothafukaa on 2006-09-26
the menu.lst is blank
wtf?

---

### Post by TiredBird on 2006-09-26
Have you fixed it yet? I think I can help but I'm not going to bother if you've got it working.

---

### Post by mothafukaa on 2006-09-26
> **TiredBird said:**
> Have you fixed it yet? I think I can help but I'm not going to bother if you've got it working.
no, i havent, plz help help

---

### Post by TiredBird on 2006-09-26
You've got to get access to the directory /boot/grub on the last install done on that particular machine. Let me know when you got it. You should be able to do a directory list and find 'menu.lst'.

---

### Post by mothafukaa on 2006-09-26
ok, im getting pissed
i mean, ****, it cant be THIS hard to make windows boot by default
and, i could fix it probably with that program mentioned above, but i need to fix my internet....
(cable modem, wired directly to comp to onboard LAN, wont connect in linux, but it will in windows)

---

### Post by randell6564 on 2006-09-26
> **mothafukaa said:**
> well, i love my ubuntu, but this is a family computer, and the rest of my family uses windows
so, i want to change my GRUB loader to run windows XP as default, instead of picking linux automatically after a few seconds
help me plzplz
Hi!
'Lukanium' is right!  Just open your /boot/grub/menu.lst and find the line that reads "default 0".  Just change it to 1,2,3,4 or whatever number that will boot to Windows automatically. In my case, it's 4.

---

### Post by confused57 on 2006-09-27
You can enter the menu.lst by:
```
gksudo gedit /boot/grub/menu.lst
```
The menu.lst entry is short for menu.list, not menu.first.

Then you can change the default OS from the link(s) you've already been give.

---

### Post by turbojugend_gr on 2006-09-27
> **mothafukaa said:**
> the menu.lst is blank
wtf?

Well ma8 you typed it wrong: you need to type exactly: ```
sudo gedit /boot/grub/menu.lst
```

In case you get misleaded by any letter I 'll write it in capitals (though you need to write it as above of course): SUDO GEDIT /BOOT/GRUB/MENU.LST

then do as I suggest (and all others here do also) in my previous post.

---

