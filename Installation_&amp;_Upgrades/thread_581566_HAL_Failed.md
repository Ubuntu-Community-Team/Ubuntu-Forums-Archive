---
title: "HAL Failed"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by bendy on 2007-10-19
I have upgraded on two dell laptops from fully patched 7.04 to 7.10

Now i get this on each every time i boot,
 
    Internal error

    failed to initialize HAL!

The system seems to run ok (have lost 3d cube even though activated)


Any ideas?

---

### Post by xcesarfrancox on 2007-10-21
I had the same issue, and it solved when I did this:

```

gksudo gedit /etc/init.d/rc

```

Look for a line that says

```

CONCURRENCY=shell

```

and change the "shell" word for "none" (without the "")

Now save the file and close gedit

Restart X by typing Ctrl-Alt-Backspace and you should login fine this time

(this solved my problem, if this doesn't work for you maybe is not the same problem... but I really hope that this may help you :)

---

### Post by bendy on 2007-10-21
Thanks for that

I did try that plus a few other things

Ended up with a reinstall and all was good

ta

---

### Post by kloudy on 2007-10-21
I have the same problem.  Have actually upgraded several times over past two day.  The line you site was already "CONCURRENCY=none" on my load.  Is that what it should be?

Thanks,
Levi

---

### Post by skompier on 2007-10-21
I had that problem show up and I just reinstalled HAL via Synaptic. Fixed it for me.

---

### Post by dshan on 2007-10-22
I've got the problem on a 7.04->7.10 upgraded virtual machine (under Parallels on a MacBook Pro). Didn't get the problem when upgrading my Dell Inspiron from/to same versions. Didn't get the problem when I installed a new 7.10 in a new virtual machine on the MBP (sadly I blew this install away before realising the upgraded vm had this problem).

I've tried reinstalling HAL (from 7.10 disk) using Synaptic, didn't help. CONCURRENCY=none is already set in /etc/init.d/rc. I'm using auto-login so I tried delayed login for 30s and 1m but got same error. Switched to manual login and waited 4m but made no difference. hald is not running, dhcdbd not running either. 

"sudo /etc/init.d/dbus restart" seems to work, everything starts again and Network Manager applet can now see n/w, both dhcdbd and hald are running. Shutdown/restart and we're back to the same problem however. Used Synaptic to reinstall dbus but it didn't help.

Looks like I'm going to have to go with a new virtual machine, recustomize it and copy across all my data and apps, etc. Damn.

---

### Post by shrinkpad on 2007-10-29
> **dshan said:**
> "sudo /etc/init.d/dbus restart" seems to work, everything starts again and Network Manager applet can now see n/w, both dhcdbd and hald are running. Shutdown/restart and we're back to the same problem however."

I am having exactly the same issue - word for word to what you are seeing.

---

### Post by computer_user_au on 2007-10-31
As a temp fix, try command:
```
sudo /etc/init.d/dbus restart
```

The check out the fix in thread:
[http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL]("http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL")

Good luck.

---

### Post by computer_user_au on 2007-11-01
Also, check out:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")

I manually did the following on my system:

```
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
```

rebooted and the system worked, no more "Failure to initialize HAL" error messages and my network connection is working well.

---

