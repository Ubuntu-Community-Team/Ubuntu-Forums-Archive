---
title: "urgent ,GRUB 1.5 error17"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by nukemelamers on 2008-03-24
i've just installed ubuntu 1hour ago,
then i reboot and check my vista, then i wanna use ubuntu 7.10 that one just installed, then
Grub loading,
please wait,
error 17.


WTF,
what should i do??
anything i look up on forum&google doesnt resolve'

---

### Post by Schalken on 2008-03-25
so is it ubuntu or vista that doesnt boot?

---

### Post by Kevin Funnell on 2008-03-25
Check out the my post in Other OS Talk: - Windows Discussions, it may help you
Old Kevin

---

### Post by Boatswain on 2008-03-25
The Grub Error 17 means that Grub is looking for a particular drive and can find it, but can't use it because it's the wrong filesystem--[here's a link to the appropriate section of the manual.]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors") 

To see where Grub is being pointed, you need to look at your menu.lst. If you still have a Live CD around, you should be able to find it in /media/drive/boot/grub/menu.lst. Open it up with GEdit and scroll down through looking for boot drive assignments. They should look like (hd0,1). The 0,1 in this case means first drive, second partition--numbering starts at 0 instead of 1.

If you open a terminal and use 'sudo -i' (with no quotes) that will log you on as root. Your next command is "grub'. Then type 'find /sbin/init' and you should get a return that tells you what your boot drive is in the above format. When you're done with that type 'quit' to get out of the grub prompt.

Compare what menu.lst says and what find /sbin/init told you. If they're different, you might have found your problem--all you'll need to do is change  your menu.lst and restart, and hopefully it'll work. Bear in mind that you'll want to back up the surrent menu.lst before you change it, and you'll have to open it as root or with sudo gedit menu.lst in order to modify the file.

If that doesn't help, you might check out this [link to a thread I started with a similar problem]("http://ubuntuforums.org/showthread.php?t=734471")--I'm still trying to figure that one out, and there may be some answers in there for you.

Good luck!

---

