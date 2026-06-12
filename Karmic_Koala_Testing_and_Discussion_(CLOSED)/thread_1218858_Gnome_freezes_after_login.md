---
title: "Gnome freezes after login"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by neferty on 2009-07-21
Hello,

after the last update tonight my gnome freezes after login. (blank wallpaper screen, nothing loads)
The same user logs in successfully via terminal.

I created a new "test" user and it seems to log in OK and gnome loads fully, too.

Therefore, the problem has to be in some configuration problem in my normal user account, right? Any ideas? :confused:

---

### Post by hernad on 2009-07-21
I have the same problem

---

### Post by jppr on 2009-07-21
just updated system without that problem

---

### Post by taavikko on 2009-07-21
Upgrade in recovery root console with networking.
then try to login once more.

make sure that you're logged in, instead of root
If it doesn't work, let's check the ownerships of files in ~/
```
ls -lR ~/ | grep root
```

If there's nonem then let's move the important settings folders in to backup
```
cd; mkdir .backup; mv .config/ .gconfd/ .gnome2/ -t .backup/
```
this is best done in virtual terminal so that any running sessions doesn't just overwrite the files inside those folders.

---

### Post by neferty on 2009-07-21
I've tracked down the problem to the following:
**The system doesn't seem to automount crypted home directory**.
Here's what i did 
[LIST=1]
[*]When you reboot and are presented with the login screen **do not login**. 
[*]Press ctrl+alt+F1 to access terminal. Login with your details
[*]Now check your home directory and you'll see it's empty (not crypt mounted) apart of the .desktop and readme files
[*]Do manual ecryptfs-mount-private . It will ask you for your password ( i had the same pass as my user login)
[*] Switch back to graphic login with Ctrl+alt+F7 and login
[*] Done. It should load OK.
[/LIST]

Now, the problem seems that the automount of the crypted home directory disappeared. When creating a new user with unencrypted directory, it works fine, logically.

I don't want to remove my old user nor format the home directory to make it un-encrypted. Does someone know how to fix this?

(EDIT: I would want to manually mount through terminal and enter my pass each time I login. Kinda nasty :))

---

### Post by jerrylamos on 2009-07-21
Wow!

What a mess for every boot!

Is there a launchpad bug # ?

Any hope of a fix or a workaround?

Updated my Thinkpad R31 which gets the same problem.

I'll be booting Intrepid on it until the karmic forum says there's a fix for this mount problem.  Karmic video is 2x slower than intrepid on intel i830 anyway launchpad bug #382017.

No updates on my other pc's either.

Thanks much for the very good post.

Jerry

---

### Post by neferty on 2009-07-21
You're welcome :)
I've seen another post here on forums related to the same problem ([http://ubuntuforums.org/showthread.php?t=1218584](http://ubuntuforums.org/showthread.php?t=1218584)) however I'm not sure if there's a bug report on launchpad already.

This solution is only temporary, I hope :P

---

### Post by neferty on 2009-07-21
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/402222](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/402222)

---

