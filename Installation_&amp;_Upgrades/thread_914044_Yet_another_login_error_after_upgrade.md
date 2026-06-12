---
title: "Yet another login error after upgrade"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by Erszebet Lunah on 2008-09-08
Hi all,

I recently re-installed Ubuntu from my old 6.06 LTS CD (32 bit) - a clean, fresh install with no problems. Right after that I did a full update of the system, again no problems.
After that I upgraded my install to the latest 8.04 Hardy Heron release, following the steps provided at Ubuntu.org (via System -> Administration -> Update Manager)
This is where the troubles begin.

When booting the computer I now get 4 options:
[INDENT]8.04.1-kernel 2.6.24-19-386; normal & recovery mode[/INDENT]
[INDENT]8.04.1-kernel 2.6.15-52-386; normal & recovery mode[/INDENT]
	
You may have guessed by now: I can't log in anymore. I keep getting the wellknown "incorrect username or password..." comment.

Steps I took trying to solve the problem:
[LIST]
Entered recovery mode
cat /etc/passwd | grep 1000 -> listed my username and /home dir so seems ok
passwd [username] -> entered new password -> updated succesfully
[/LIST]

[LIST]
booted normally
typing correct or incorrect password always gives the same error message
Ctrl+alt+F2 to enter shell
entered username + pass -> login successfull!
rebooted (shutdown -r now)
Still can't login using graphical menu
[/LIST]

[LIST]
entered recovery mode
xfix (did change some settings as screen resolution, refresh rate were different). message: "x server-org postinst warning: overriding possible customized configuration file; backup in /etc/x11/xorg.conf.20080908180623"
resume normal boot -> still can't login
[/LIST]

To sum it all up: I **can** log in using the shell, both as root and my regular user account.
I **can't** log in using the GUI -> correct or incorrect password always gives the same error, so no blanking or flickering, no freeze...just doesn't accept my username / password.
I did check for changes in azerty / qwerty layout everytime,
so that's not it either :p

Maybe not relevant, but this is my disk layout:
/dev/sda (80 GB IDE Linux drive)
sda1 (boot)
sda2 ext
sda5 (swap)

/dev/sdb (Mirrored RAID Windows XP)
sdb1 (boot)
sdb2 Win ext
[extra non-boot partitions)

/dev/sdc (mirror)
[same as sdb]

---

### Post by Erszebet Lunah on 2008-09-09
Bump, anyone have a clue ?

---

### Post by Erszebet Lunah on 2008-09-09
Small update, as I'm a bit puzzled by the following:

if I boot normally (GUI screen) and type ctrl+alt+F1 to go
to shell (instead of ctrl+alt+F2) I can't log in - again:
I'm able to log in using ctrl+alt+F2 - shell...

Is it possible this can be solved by creating a new user ?

---

### Post by Erszebet Lunah on 2008-09-10
Seems like I'm doomed to forever use Windows too...

---

### Post by Erszebet Lunah on 2008-09-10
Ok, I managed to create a new user and am able to log in with the new account now.

---

### Post by bve on 2008-09-14
I ran into a very similar situation by picking the wrong keyboard type once, because the special characters in my password were different under the wrong kb type than the correct kb type. I figured this out when I typed my password when asked for my username. I wouldn't be surprised if that is the case.

---

### Post by Erszebet Lunah on 2008-09-16
> **bve said:**
> I ran into a very similar situation by picking the wrong keyboard type once, because the special characters in my password were different under the wrong kb type than the correct kb type. I figured this out when I typed my password when asked for my username. I wouldn't be surprised if that is the case.

Yeah I did the exact same thing too, before posting on this forum.
I created another account and currently lots of reading / experimenting with it before I delete the whole thing and install it properly :p 
Thanks for replying though.

---

