---
title: "[SOLVED] Login and Passwd Problems"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by jatinder on 2008-03-17
I have a Toshiba Satellite Laptop with Win XP on which I installed Ubuntu 7.04 with dual boot options. However, on loggin in Ubuntu as Admin, I get only a blank screen with mouse working, but I can login normally as user. Another issue is when I try to update, it does not accept my admin or root passwords although I have changed the passwd using sudo passwd commands, but it still says password incorrect. The laptop has Radeon 9000 igp card installed. can anyone help

---

### Post by Rocket2DMn on 2008-03-17
You can reboot into the recovery kernel at the GRUB menu, and run "passwd" from there to change the root password.  You actually can't login as root until this is done anyway, since the root account is disabled in Ubuntu by default.
I have a Mobility Radeon 9000, and I have my graphics working OK in Gutsy (but not Hardy).
After setting up root are you still having problems with the video card?

---

### Post by jatinder on 2008-03-17
I have changed the passwd from grub but still it does not accept the changed passwd when I try updating it from GUI and the screen still goes blank when I login as Admin

---

### Post by jken146 on 2008-03-17
```
passwd
``` in recovery mode will change the password for root.  Disable the root account, you don't need it and you don't want it: ```
passwd -l root
```

Then you can reset the password for your user.  ```
ls /home
```will show you the users that are currently there.  For a user called *bob*, do ```
passwd bob
```

If you want bob to be able to use sudo ('administer the system') then you must make sure that bob is a member of the *admin* group: ```
useradd -G bob admin
```

Now reboot: ```
reboot
```

---

### Post by Rocket2DMn on 2008-03-17
+1 for jken's post.  If you can login to the GUI fine with your user but only get the black screen with root, then you X configuration should be OK.  Try selecting a different session at the login screen, like the Failsafe option.  It might yell at you and say you shouldn't be logging in as root, but tell it to proceed anyway.

---

### Post by jatinder on 2008-03-18
Thanks. I was able to add another admin user and this time the GUI worked and was able to update as well

---

