---
title: "will not let me login to session in during 6.10 upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by A*p on 2006-10-27
I set my machine upgrading to edgy last night, woke up now and the XscreenSaver is asking for a password, but it will not let me login, it just says Sorry!

I have gone to another terminal Ctrl+Alt+F2 and can login perfectly, but when I go back to my graphical session it will not let me in ](*,) 

The update must be toward the end as when I went to sleep it was in the download and install process showed 8 minutes to go.  I am running XFCE, luckily for some reason, the screensaver has always had a slight transparancy over my desktop (don't know why, but it has never bothered me) so I have been able to turn my monitor up to full brightness and can see that a dialogue is asking for confirmation to replace the customised configuration /etc/login.defs with a newer version.

How can I login to the graphical session to finishe the update?

---

### Post by magicfab on 2006-10-27
1. from terminal, issue the "ps -e | grep screen" command
It should list something similar to :
4769 ?       00:15:09 gnome-screen-sav
2. Copy or write the "4769", it's the process ID
3. Kill it, using "sudo kill -9 4769" , 4769 being the process ID
4. Go back to your now unlocked esktop with CTRL-ALT-F7

I just locked my own screen and tried that procedure and i could regain access to my desktop.

---

### Post by A*p on 2006-10-27
You are the man, magicfab that sorted me out and has got the install moving again.

I had horrors of having a frozen machine that I was too scared to reboot for the next week as It may boot back up dead.

Many Thanks

:-D

---

