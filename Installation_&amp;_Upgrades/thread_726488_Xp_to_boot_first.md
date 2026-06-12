---
title: "Xp to boot first"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by MSdefecter on 2008-03-16
Hi all,

This is a fairly stupid question I know, but I have had no luck in solving this on my own.
I had 7.10 and XP loaded on my system and my Wife asked me to change it so that XP would boot automatically instead of Ubuntu. I followed the advice of others and managed to change the time that the boot option screen appeared for. However it did not boot into XP but tried to boot into Ubuntu except it stopped and gave me an error message. I have since reinstalled Ubuntu because of this and am trying to, this time correctly change the boot order. I have looked at more posts about this and have seen the people suggesting that I would have to post 
                            /boot/grub/menu.lst

I did this and this time it told me that permission was denied. I figured that it was because I was not identifying myself as the root user, so I used the same post but with Sudo in front of it. It this time said that there was no such command. I appreciate that I am probably being completely stupid but  could anyone tell me what I am doing wrong?

---

### Post by jken146 on 2008-03-16
You need to edit the file /boot/grub/menu.lst 

First, make a backup:  ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then edit it:
```
gksu gedit /boot/grub/menu.lst
```
Change the 0 in the line that says ```
default    0
``` to the correct number for the entry for Windows (1 if Windows is the 2nd entry in the list, 2 if it is the third, and so on).

Save the file and reboot to test it.

---

### Post by Lantesh on 2008-03-17
Alternatively if you don't want to edit menu.lst in terminal you can actually edit it with "text editor".  If you do it this way you can see all the contents of the file, and simply type your changes therein.  In order to do this though I copy the file into another folder.  I make my changes to the copy, save it, and then open a terminal session, and move the copy to back to the source folder, thereby overwriting the original.  You have to move it over using sudo or it won't overwrite.

---

### Post by MSdefecter on 2008-03-19
Hi,
I decided to edit the grub list and changed the boot order. Xp is listed 4th on the list so, naturally I changed the default entry to 4. When I rebooted Xp was highlighted and it loaded automatically. Now however, Ubuntu will not boot up. It runs 4 process messages and displays O.K next to each one, the last message being something about running scripts and has O.K next to it but it does not do anything else.

---

### Post by forestpixie on 2008-03-19
can you post it here and did you back up first?

```
cat /boot/grub/menu.lst
```

---

### Post by MSdefecter on 2008-03-19
Hi,
I don´t know why or what happened, but after two unsuccessful boots yesterday I just selected Ubuntu and it booted straight in.

---

