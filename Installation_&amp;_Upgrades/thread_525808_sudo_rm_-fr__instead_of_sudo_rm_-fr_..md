---
title: "sudo rm -fr /* instead of sudo rm -fr ./*"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by obley on 2007-08-14
yea.. I did it. The worst typo I have ever made. So my server is a little jacked up now :|

I'm not even sure the extent of the damage I did. Once I realized something was wrong (permission denied errors in /lib) I killed the job. It went soo fast :( I know my home folder was nuked. logging out and back in will not load bash correctly. I'm afraid to reboot.

Is there anything I can do to restore this short of backing up what config files I have left, reinstall, and copy them back over?

*sigh*

thanks

---

### Post by obley on 2007-08-14
well while poking around I was able to recreate my profile from cat /home/anotheruser/.profile > ~/.profile

What other profile related files could I be missing? (automatically generated files)

Is there anyway to see what was actually deleted in say /bin or /etc? (logs, system messages, anything?)

---

### Post by mssever on 2007-08-14
> **obley said:**
> well while poking around I was able to recreate my profile from cat /home/anotheruser/.profile > ~/.profile

What other profile related files could I be missing? (automatically generated files)

Is there anyway to see what was actually deleted in say /bin or /etc? (logs, system messages, anything?)

That really stinks. I once did something similar to my home directory.

As far as I know, the only way to know what you lost is to look around. Of course, if you don't know what's supposed to be there...

I hope you have a good backup. One tip for the future: ```
sudo rm -rf *
``` is identical in meaning to ```
sudo rm -rf ./*
```, but since there's no slash it's a bit safer. Since ./ refers to the current directory, it's usually unnecessary.

As far as profile items go, many programs store their settings in $HOME/.something. All those settings are presumably gone. You'll probably have to redo them. If you're using .profile, then you must be using csh, right? Bash keeps it's settings in .bash*.

---

### Post by obley on 2007-08-17
hey thanks. I know about ./* versus, I don't know why, but I just always do it. I agree, its time to break that habit.

I have a backup of my scripts and .bashrc but nothing else.

I'm using bash, not csh. I restored my .bashrc file and it had no effect. I created a new user (adduser) to see what is made by default, and all I was missing was .profile

---

