---
title: "Not able to log on"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by jimmy510 on 2006-10-19
I have installed ubuntu today when evet ubuntu boots up in GUI mode i try to log on using root as the user name and abc as the password but it gives me error that administrator can not log on using this screen as well as i made a use as i can log on using text mode but when i try to log on using that user it gives the the following error


/etc/gdm/PreSession/Default:Registering your session with wtmp and ctmp
/etc/gdm/PreSession/Default:Running:/usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x"/var/lib/gdm/o Xservers" -h " -l":o" "jimmy"

/etc/gdm/Xsession:Beginning Session Setup (gnome-session:4903)libgnomevfs-Warning *.* unable to create /Gnome2 directory:Permission Denied

Could not create per user gnome configurationdirectory /home/jimmy/gnome/:Permission Denied

---

### Post by taurus on 2006-10-19
You cannot log in as root since root is inactived!  You need to log in with the username and password that you have created during the installing process.  And if you need to run a command that requires root, then use the sudo with it...

```
sudo <command>
(and use the same password that you use to log in...)
```

---

