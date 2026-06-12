---
title: "[SOLVED] How can I change GRUB's default OS?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by tlinux on 2008-11-18
I have Kubuntu and Windows XP loaded in a dual boot system. Grub automatically opens Kubuntu by default. I want to change that to Windows. I thought there was a menu in one of the GRUB folders that I could edit to make this change, but I can'f find that menu. 

How do I change the default OS in GRUB?

Thank you.

---

### Post by zymjh on 2008-11-18
I am pretty sure that the menu.lst is in the /boot/grub/ folder.

---

### Post by girishsasikumar on 2008-11-19
u need to edit /boot/grub/menu.lst for which u need to have administrative privileges.
```
sudo gedit /boot/grub/menu.lst
```
the change # in the line ***'default #'***, to whichever OS/kernel u want 1, 2 ... etc as default

---

### Post by tlinux on 2008-11-19
> **zymjh said:**
> I am pretty sure that the menu.lst is in the /boot/grub/ folder.

You are correct. I overlooked the menu when I first searched for it.

Next question: Is there a way to get into Administrator Mode without using the terminal and entering command-line instructions?

Thanks for your help.

---

### Post by taurus on 2008-11-19
```
sudo nano -Bw /boot/grub/menu.lst
```
<Ctrl>x to exit.

---

### Post by Chazall1 on 2008-11-19
In your /boot/grub/menu.lst on the upper half of the page, there is an examlpe area, which gives you an example of an XP boot. These lines have a # in front of them, make any changes HERE not in the Main Kernel area. If you place your grub XP into the Kerel area, It will only work up until you get a kernel update, and grub will not function properly.
Look in the example area near the top of the /boot/grub/menu.lst.

---

### Post by aysiu on 2008-11-19
In Kubuntu I don't think you have Gedit.

So you would paste this command into [Konsole terminal](http://www.psychocats.net/ubuntu/terminal): ```
kdesu kate /boot/grub/menu.lst
``` and then change the *default 0* to a different number. 0 is for the first entry. 1 is for the second. 2 for the third. And so on.

---

### Post by dabl on 2008-11-19
If your Kubuntu version is 8.10, then you can use KMenu>System Settings>Advanced>Grub Editor (or something like that) to change the sequence on the menu.

In version 8.04 or earlier, to avoid the CLI, your can do Alt-F2 "kdesu kate /boot/grub/menu.lst" with no quote marks, and change the order by cutting and pasting the "stanzas" at the bottom of the file.

In 8.10, the command is "kdesudo kate /boot/grub/menu.lst".

And if you're editing /boot/grub/menu.lst, in addition to the edit mentioned by aysiu, make sure the "groot=" line has the hd(x,y) partition where your Ubuntu OS is located.

HTH.  :)

---

### Post by tlinux on 2008-11-19
"In version 8.04 or earlier, to avoid the CLI, your can do Alt-F2 "kdesu kate /boot/grub/menu.lst" with no quote marks, and change the order by cutting and pasting the "stanzas" at the bottom of the file."

This worked like a charm! Thank you for your help.

PROBLEM SOLVED

---

