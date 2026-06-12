---
title: "New 6.10 Install &amp; Can't Login"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by zepster on 2006-12-12
Hi,

I've installed 6.10 twice now and both times I can't login.  I supply my first name, my initials as the login name and a standard password and no success.

Any idea?  Thanks,

Zep

---

### Post by taurus on 2006-12-12
Did you use the LiveCD or the alternate CD to install it?  And when it asks for a username, it's the actualy username that you've created during the installing process, not your first name, middle name, or your last name, the actual username...

---

### Post by zepster on 2006-12-12
I used the alternate cd - the install ask for a username, login name & password.

I tried both user name and login name with no success.

---

### Post by taurus on 2006-12-12
Okay, boot into recovery mode from GRUB menu and at the prompt, paste the output of this command here (or at least the last few lines at the end)...

```
cat /etc/passwd
```

---

### Post by wpshooter on 2006-12-12
> **zepster said:**
> I used the alternate cd - the install ask for a username, login name & password.

I tried both user name and login name with no success.

I definately think these are case sensitive in Ubuntu.

Are you using the same CASE/case that you input the username and password ?

---

### Post by Dr Dan on 2006-12-13
I had a very similar problem installing 6.06 from both live cd and alternative cd. Eventually i came to the conclusion that it had not in fact created a user at all during the installation! (i there was nothing in /home, no user or group with the name i gave etc).

I could not in the end figure out how to remedy this (it happened with multiple installations) though I am quite new to ubuntu and linux, so i gave up and installed 5.10 then upgraded this to 6.06. 

This won't help those with the same problem, but it might help someone more experienced figure out a solution i hope.

Dan

---

### Post by zepster on 2006-12-14
I used the same user name and login name on the previous two attempts.  This last time I used a different user name and login name and it seems to be working now... go figure.

Anybody know how to get root access?  I tried installing MYSQL, but it says I can't run the process because I don't have root access.

---

### Post by taurus on 2006-12-14
If you want to use sudo, you need to belong to groups adm & admin in /etc/group.  Boot into recovery mode from GRUB menu and at the prompt, open a text editor and add your username to the end of those two groups then.

```
nano -w /etc/group
```

---

### Post by emarkay on 2006-12-20
Jeez - my new 6.10 install (I used the alternate CD) gave me the user name of "OEM"!!

Maybe because I used the OEM install?  (It did say GRAPHICAL...)  Some genius needs to look into this for I STILL can't figure how how to get the username I want.  

Mighty counter-intuitive I'd say...

ALSO the user directory names became what I THOUGHT was the "computer name"

This is NOT as simple as my 6.06 install!

AAARGH!

---

### Post by bapoumba on 2006-12-20
@ emarkay : when installing with the alternate CD, the user is "OEM" and the password the one you gave. Just run **sudo oem-config-prepare** from a terminal. Next reboot, oem user will be deleted and you will be prompted to create a new login and password. This user will have sudo priviledges  ;)

---

