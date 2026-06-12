---
title: "init.d script for stylus"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by zackiv31 on 2007-12-14
```

me@x61u:~$ cat /etc/init.d/stylus.sh
#!/bin/bash
xsetwacom set stylus Button1 "button 1"
xsetwacom set stylus Button2 "button 1"
xsetwacom set stylus Button3 "button 3"
me@x61u:~$ ls -alrt /etc/init.d/stylus.sh 
-rwxr-xr-x 1 root root 132 2007-12-14 20:31 /etc/init.d/stylus.sh
me@x61u:~$ sudo update-rc.d stylus.sh defaults
 Adding system startup for /etc/init.d/stylus.sh ...
   /etc/rc0.d/K20stylus.sh -> ../init.d/stylus.sh
   /etc/rc1.d/K20stylus.sh -> ../init.d/stylus.sh
   /etc/rc6.d/K20stylus.sh -> ../init.d/stylus.sh
   /etc/rc2.d/S20stylus.sh -> ../init.d/stylus.sh
   /etc/rc3.d/S20stylus.sh -> ../init.d/stylus.sh
   /etc/rc4.d/S20stylus.sh -> ../init.d/stylus.sh
   /etc/rc5.d/S20stylus.sh -> ../init.d/stylus.sh

```

After performing all this, I restart gdm, and the script is not executed.  if I manually run it, with ". /etc/init.d/stylus.sh" and then test it, it works...

what am I doing wrong?  (Gutsy 7.10 on X61 tablet]

---

### Post by ectospasm on 2007-12-14
Init scripts are meant to be run when you change runlevels, or when you're booting.  Simply restarting GDM won't run an init script...

---

### Post by zackiv31 on 2007-12-14
even if that is true, i just restarted my computer and it doesn't work still...

---

### Post by ectospasm on 2007-12-14
It may be that you don't have the normal start/stop/restart functions in your script.  I'm guessing that init is trying to run this:

/etc/init.d/stylus.sh start

Which is meaningless to the script.  Nonetheless, it should still be executing the lines in your script.  Another thought is that your script is running before the Wacom driver is loaded.  Try this:

update-rc.d stylus.sh defaults 99

That will make sure that the stylus.sh script is one of the last to run.  You may need to adjust the 99 value to something else to best suit your needs.  If all else fails, you can stick the contents of the stylus.sh file into rc.local.  If it still doesn't work after a reboot then, then there's something else wrong with your setup.

---

### Post by zackiv31 on 2007-12-15
I've put it in /etc/rc.local   -> no luck
I've put it int /etc/init.d/rc.local  -> no luck

I tried to put it in at 99, with sudo update-rc.d stylus.sh defaults 99   -> no luck


What is going on?  The only thing i can notice is that rc.local uses shell instead of bash, but that should NOT matter...


I don't understand why this isn't executing.. or if it is, why its not working..

---

### Post by ectospasm on 2007-12-15
Wait, maybe you need to put it in your user startup scripts.  The commands in /etc/init.d run as root, which is probably why you're not seeing the changes take effect for you.  I don't know if you should put it in ~/.bashrc or ~/.bash_profile, or your window manager's appropriate script.  ~/.xninitrc may be one place to look, or if you're using KDE put it in ~/.kde/Autostart.  I don't know where you'd need to put it for GNOME, or other window managers.

HTH

---

### Post by zackiv31 on 2007-12-16
I put it in xinitrc.. and it seems like its running before the WM is up, because I get 3 messages before X loads about "Failed to open Display" which to me means that its trying to load it too early.

putting it .bashrc would execute it everytime I open a terminal, which isn't really what I want, and I would still need to open a terminal to have it take effect.

I don't have a bash_profile file.. do I need to create one?


I don't understand how it's so hard to make a program/script execute on startup.. what is wrong with Ubuntu/Linux?

---

### Post by zackiv31 on 2007-12-16
Writing this last post refreshed my memory.. and I remember that I did something like this in Fedora.. being Gnome probably the same..

System>Preferences>Sessions>Startup Programs

Just added my script there, and all is well :)

---

