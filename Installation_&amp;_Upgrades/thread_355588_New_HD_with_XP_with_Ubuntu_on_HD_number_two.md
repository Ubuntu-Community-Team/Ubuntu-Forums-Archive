---
title: "New HD with XP with Ubuntu on HD number two?"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by sljung on 2007-02-07
I'm a one week noob with Ubunto so please be nice:)

I've installed Ubuntu on my primary HD and now I want to install XP to my secondary HD wich is partitioned with 40GB and 160GB.

Is the easiest way to do this to change the IDE cable going to my primary disk with the IDE cable to my secondary disk?

My wife is not into Ubunto and she would like the computer to automatically start with XP...

What do i need to do to make this work?

Kind regards
Stephan

---

### Post by milton1 on 2007-02-07
The windows install should allow you to choose the install partition. If it doesn't, you could switch the cable, but you will need to change the device references in fstab and /boot/grub/menu.list. In either case, installing windows will fubar your bootloader. You will need to reinstall grub (search this forum, many references). Once all is installed, edit /boot/grub/menu.list so default is the number of the windows os (remember to index from zero).

---

### Post by Medieval_Creations on 2007-02-07
Idealy you should install XP on the desired HD first.  Then install Ubuntu.

Ubuntu will then overwrite the MBR and Grub will have a Windows XP option in it which you can then set as default, so after a set amount of time will automatically boot into XP.

---

### Post by sljung on 2007-02-07
I know that installing XP would **** up the GRUB from hours of scanning trough this forum trying to find the best way to install my damn Belkin F5D7050 v3000 USB **** wireless to work.
Finally made the right connection last night after almost 2 days!

I was hoping to avoid the coding on a new Ubuntu install as i've already tweaked it and installed lots of codecs and progs....

I'll bite the sour apple and go home to install the XP first and the Ubuntu next:)

---

### Post by Medieval_Creations on 2007-02-07
There is a way to fix grub if you have to install XP after Ubuntu.  Off the top of my head I can't recall the command, but it can be done.

---

### Post by Medieval_Creations on 2007-02-07
This Thread might help.  You can always install XP and try it.

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)

---

### Post by confused57 on 2007-02-07
> **sljung said:**
> I'm a one week noob with Ubunto so please be nice:)

I've installed Ubuntu on my primary HD and now I want to install XP to my secondary HD wich is partitioned with 40GB and 160GB.

Is the easiest way to do this to change the IDE cable going to my primary disk with the IDE cable to my secondary disk?

My wife is not into Ubunto and she would like the computer to automatically start with XP...

What do i need to do to make this work?

Kind regards
Stephan

This setup works for me:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by sljung on 2007-02-07
> **Medieval_Creations said:**
> This Thread might help.  You can always install XP and try it.

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)
**[COLOR="Red"]Super Grub Disk[/COLOR]**
[IMG]http://supergrub.forjamari.linex.org/imagess/main_menu.png[/IMG]
[http://supergrub.forjamari.linex.org/?section=home]("http://supergrub.forjamari.linex.org/?section=home")

Think I'll install XP and run this nice tool afterwards!

---

