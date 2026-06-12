---
title: "Missing users on gui login screen"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by williamknight on 2010-03-23
Hi all, some help if you've got a moment, I'm quite new to installing Ubuntu, though I've been using the gui for a couple of months now.

I installed Ubuntu 9.10 from a disk at home, dual boot with XP.

The initial install goes fine, but after a reboot due to updates, the login sceen appears but with no users; just a blank, black rectangle beneath the shining Ubuntu stage light. Even the power on/off button is missing, but the usability icon appears, and works.

I have reinstalled. This did not make a difference.

I can get to a command line with shift-alt-f1, and can log in. But I can't get to Gnome from there, startx complains that the xserver is already running.

Can you offer any ideas?

Cheers
Will

---

### Post by stlsaint on 2010-03-23
Post the specs of your hardware on system.

---

### Post by Gregorybekkers on 2010-03-23
can u kill xserver and start it again?

---

### Post by williamknight on 2010-03-23
thanks for the replies.

I have stopped and restarted gnome using:
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

but the same issue returns. I cannot get into gnome at all.

Is it possible to log in on the command line and then get into Gnome with that user?

Will

I honestly couldn't tell you what the hardware is. But I can tell you I have had gnome up and running before on the same machine but with different partitions and without a dual boot. The machine is about 5 years old, though so it's not the most up to date motherboard or processor.

---

### Post by williamknight on 2010-03-24
SOLVED:

this is caused because of the choice of user names.

I used an "&" int the users real name - which is allowed in gnome - but caused a blank login when restarting.

The problem is signalled when you try to turn off, and 
gdm-simple-greeter is not responding and must be terminated.

Go into the command line  ctrl-alt-F1 
list the users: cat  /etc/passwd
then delete the users with a real name with the & in 
sudo userdel <username> (or something like that, I can't quite remember.)

---

