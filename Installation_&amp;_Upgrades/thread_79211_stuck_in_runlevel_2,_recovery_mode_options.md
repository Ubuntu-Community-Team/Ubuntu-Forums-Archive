---
title: "stuck in runlevel 2, recovery mode options?"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by yesplease on 2005-10-19
After resizing my home directory I ran into trouble.

I managed to restore Grub and can boot into windows, from windows I can read all directories I tried.

In Ubuntu breezy 2.6.12-9-386 boot stops in runlevel 2. There are many errors in /etc/rc2.d/S## command not found in line #.

I can boot in the recovery mode.

My question is: what are my options there? I can see there is a list of commands, but perhaps there is a method that forces boot to continu or start gnome as normal and repair affected  packages?

Or should I re-install?

---

### Post by yesplease on 2005-10-20
I resized the /home partition because it was very large; 190 MB. I used /usr for the new partition where I want to store backups. Now I read that /usr is for superuser binairy files and not for user. 

If that is correct, what do I use instead of /usr for a backup partition?

Thanks in advance.

Edit: I copied the files from usr to home with the install cd, and mounted /usr as /media/sdb7. This got me as far as the normal login screen, with no complaints before that. However, during login I got the message that my /home/username directory could not be found. I checked and /home has become /usr.

It was nice to experiment, but I ran out of time and will reinstall.

---

