---
title: "Can't boot after online upgrade to ubuntu 10.04 beta2"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by derlukers on 2010-04-10
Hi!

I'm using a Dell Precission m65 laptop, running Ubuntu and Windows in Dualboot.
I tried to upgrade Ubuntu 9.10 to 10.04 beta2 with the online upgrade.
Everything seemed to work fine until i restarted.
I cant boot Ubuntu anymore.
I tried it with kernel 2.6.31-20 and kernel 2.6.32-19.
After grub i just see the Starting up message.
In recovery mode, the last things done are:
mounting sda5, which is where grub and ubuntu are installed to
running /scriptslocal-bottom and /scripts/init-bottom, which it says that they are both done, and the last message is "EXT4-fs (sda5): internal journal on sda5:8"

Please help me, because i dont want to reinstall everything

---

### Post by uRock on 2010-04-10
As you know 10.04 is still in the Beta testing. When you boot to recovery mode, have you tried the option to repair broken packages?

If that doesn't work and you have the / and /home partitions, doing a clean install of 9.10 or 10.04 will be easier than trying to sort out a majorly broken upgrade.

Regards,
Ronnie

---

### Post by hof1063 on 2010-04-13
I was having the same problem but was able to make it go away if I chose the "Enhance contrast in colors" option in the Universal Access Preference screen. The screen can be accessed from the log-on screen. It is the icon to the left of the date.  Good Luck !

---

### Post by clafa on 2010-04-13
> **derlukers said:**
> Hi!

I'm using a Dell Precission m65 laptop, running Ubuntu and Windows in Dualboot.
I tried to upgrade Ubuntu 9.10 to 10.04 beta2 with the online upgrade.
Everything seemed to work fine until i restarted.
I cant boot Ubuntu anymore.
I tried it with kernel 2.6.31-20 and kernel 2.6.32-19.
After grub i just see the Starting up message.
In recovery mode, the last things done are:
mounting sda5, which is where grub and ubuntu are installed to
running /scriptslocal-bottom and /scripts/init-bottom, which it says that they are both done, and the last message is "EXT4-fs (sda5): internal journal on sda5:8"

Please help me, because i dont want to reinstall everything

I'm experiencing the exact same problem... :confused:

---

### Post by tendant on 2010-04-21
I have the same problem. Just upgraded yesterday. 

Now I cannot even boot to recovery mode. 

Thanks, 
Lei

> **uRock said:**
> As you know 10.04 is still in the Beta testing. When you boot to recovery mode, have you tried the option to repair broken packages?

If that doesn't work and you have the / and /home partitions, doing a clean install of 9.10 or 10.04 will be easier than trying to sort out a majorly broken upgrade.

Regards,
Ronnie

---

### Post by Fabio Ferrari on 2010-04-21
Same thing here.
Recover ends with: EXT3 FS on sda2, internal journal
Then nothing else happens...

---

### Post by Fabio Ferrari on 2010-04-22
> **Fabio Ferrari said:**
> Same thing here.
Recover ends with: EXT3 FS on sda2, internal journal
Then nothing else happens...

Solved:

It is the same problem that happened here:
[http://ubuntuforums.org/showthread.php?t=1441810&page=4](http://ubuntuforums.org/showthread.php?t=1441810&page=4)

Use init=/bin/bash to boot.
mount / -o remount,rw
vi /etc/fstab
And comment the lines that have usbfs

---

