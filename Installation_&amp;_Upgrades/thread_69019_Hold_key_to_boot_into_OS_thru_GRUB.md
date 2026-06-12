---
title: "Hold key to boot into OS thru GRUB?"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by jedcred on 2005-09-25
Is there a way to get GRUB to automatically boot into an operating system by default unless you hold down a certain key to:

A) go into the boot menu 
or
B) boot into x OS by holding y button?

I ask because I'd like to boot into Windows by default, as I use that most of the time and I resume from hibernate most of the time, but I'd like access to the Linux partition explicitly when I want to. If you own a Nintendo DS you know exactly what I'm talking about: if you do nothing, it boots to a DS game, if you hold START, it boots to the DS menu, and if you hold B, it boots into a GBA game. Is that possible through GRUB, and how would you go about doing this?

Thanks in advance.

---

### Post by papangul on 2005-09-25
When was your grub installed, I'm asking this because ubuntu by default hides the boot menu and boots into your preffered OS.
this is the relevant portion of grub :
```
Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

 hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
You have to either uncomment the hiddenmenu line or add it to menu.lst. 
You won't see the menu after this, the OS listed at "0" position will be booted after three seconds. You can get the menu by pressing <Esc>.

---

### Post by dakpowers on 2005-09-25
[QUOTE=papangul]When was your grub installed, I'm asking this because ubuntu by default hides the boot menu and boots into your preffered OS.
this is the relevant portion of grub :
```
Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

 hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
You have to either uncomment the hiddenmenu line or add it to menu.lst. 
You won't see the menu after this, the OS listed at "0" position will be booted after three seconds. You can get the menu by pressing <Esc>.[/QUOTE]
 I am also curious about this, and have found nothing about it. Thanks :)

---

### Post by jedcred on 2005-09-26
That's basically what I was looking for. Thanks!

BTW, GRUB was installed with Ubuntu, so it is the "default" config: 10 seconds to pick OS, with Ubuntu, Ubuntu safe mode, Ubuntu mem test, and Windows. Anyway, thanks again!

---

