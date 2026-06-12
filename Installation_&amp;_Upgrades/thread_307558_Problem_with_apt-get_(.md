---
title: "Problem with apt-get :("
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by BlueStreak on 2006-11-26
Ever since attempting to install openclipart I'm having big problems with managing packages. Everytime I attempt to do something in either synaptic, apt-get, aptitude, automatix I get the following error:

E: openclipart: files list file for package `openclipart-png' contains empty filename

The clipart install failed saying it failed to fetch some files from the server (it wasn't real specific). In synaptic it appears to be installed but any attempts to reinstall or remove result in the above error.

Note that I get this error regardless of what package I'm attempting to remove or install, even those completely unrelated to openclipart.

Please help. thank you!

---

### Post by groggyboy on 2006-11-26
run an update (sudo aptitude update) and then try using this command in the terminal:```
sudo aptitude upgrade -f
```

if you prefer, you can run the command using apt-get instead of aptitude.
the '-f' option tells the apt-get package system to fix broken dependencies.  maybe that will clear it up.

---

### Post by BlueStreak on 2006-11-26
Thanks groggyboy, tried that but it didn't help.  Still getting that same error.  Any more ideas?

---

