---
title: "Messed up my sudo user"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by gdboling on 2005-06-28
So I was trying to get myself read/write access to the raw1394 and I did this

sudo usermod -Gvideo gdboling

Worked great.  But now I am not in the sudo group.  And I don't have access to put myself back in it.  Does anyone have any tricks on how I can get my user back the way it was without a reinstall?

Thanks.

---

### Post by mingus on 2005-06-28
If you boot using the Recovery menu choice you can get in to a terminal as root . . . from there, you can modify the sudoers file or whatever you need to do to fix.

If you don't know how and need to get into Gnome to do it, you'll need to login as root.  Gnome is not set up by default to allow that.  To change that, get in as above and in the terminal do:
#nano -w /etc/gdm/gdm.conf
this is a curses text editor.  scroll down to the line "AllowRoot=" and change the value to "true".  then reboot as normal and login as root.

---

### Post by kvidell on 2005-06-28
[QUOTE=mingus]If you boot using the Recovery menu choice you can get in to a terminal as root . . . from there, you can modify the sudoers file or whatever you need to do to fix.

If you don't know how and need to get into Gnome to do it, you'll need to login as root.  Gnome is not set up by default to allow that.  To change that, get in as above and in the terminal do:
#nano -w /etc/gdm/gdm.conf
this is a curses text editor.  scroll down to the line "AllowRoot=" and change the value to "true".  then reboot as normal and login as root.[/QUOTE]
 Will the second method work if there's no root user set password? He'd have to set one while in recovery mode, right?
- Kev

---

### Post by gdboling on 2005-06-28
[QUOTE=mingus]If you boot using the Recovery menu choice you can get in to a terminal as root . . . from there, you can modify the sudoers file or whatever you need to do to fix.

If you don't know how and need to get into Gnome to do it, you'll need to login as root.  Gnome is not set up by default to allow that.  To change that, get in as above and in the terminal do:
#nano -w /etc/gdm/gdm.conf
this is a curses text editor.  scroll down to the line "AllowRoot=" and change the value to "true".  then reboot as normal and login as root.[/QUOTE]

Going to recovery mode and doing a usermod -Gsudo gdboling but that didn't seem to fix the problem.  Where is the sudoers file that I need to edit?

---

### Post by gdboling on 2005-06-28
Ok, I had to add my user back into the admin group, not the sudo group.  That seemed to fix the problem.  However, in the future, what is the best way to add my user to a group without removing it from the groups it belongs to?

---

### Post by mingus on 2005-06-28
[QUOTE=kvidell]Will the second method work if there's no root user set password? He'd have to set one while in recovery mode, right?
- Kev[/QUOTE]

Not sure.  (I assumed he had set one.)  Recovery drops you to a password prompt just before gdm is called.  I suppose he could tty and set one from there.

---

### Post by mingus on 2005-06-28
[QUOTE=gdboling]Ok, I had to add my user back into the admin group, not the sudo group.  That seemed to fix the problem.  However, in the future, what is the best way to add my user to a group without removing it from the groups it belongs to?[/QUOTE]

System/Administration/Users and Groups . . . a user can belong to more than one group.

---

