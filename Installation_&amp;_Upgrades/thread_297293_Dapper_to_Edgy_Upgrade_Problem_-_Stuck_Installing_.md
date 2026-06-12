---
title: "Dapper to Edgy Upgrade Problem - Stuck Installing Flash"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by mtn on 2006-11-10
Just want someone to confirm I have been an idiot! I had FF open while upgrading Dapper to Edgy, was that bad?

I decided to upgrade so after reading the relevant threads did 
```

gksu "update-manager -c"
```

It took ages  so I was browsing with Firefox and I think this may have been a bad thing to have done.

The upgrades finally downloaded and then started to install but it stopped while installing the Flash player (after about 20mins with 6mins to go of the install). I tried searching to find out if this was a problem that had turned up before but it does not look like it. Eventually I forced Synaptic to quit and now it won't let me log back in as root.

I'm fearing the worst at this point i.e. a fresh install.

Any ideas if this can be fixed? What has happened (was it the fact I had FF open?) and what, if anything I can do about it?

Cheers

---

### Post by adwait on 2006-11-10
Try loggin from the CLI by pressing Ctrl+lt+F1 at the login screen and then logging in as root/your regular user. Then just force the update to continue using
```
sudo apt-get install -f
```

---

### Post by mtn on 2006-11-11
Thanks, I tried it, but I couldn't login as root. Am thinking now that I was trying Ctrl, Alt + F1, not sure what Lt is. Anyway, I didn't get back in I had to reboot in fail safe mode to the a prompt. I then tried the command you suggested but was told to do "dpkg --configure -a" which to ages but I can now boot up as normal and login in to what looks like Edgy, the only problem is I don't have menu bar and task bar - a real pain. Be great if anyone had suggestions about getting the menu bar back. think that would solve things completely!

---

### Post by adwait on 2006-11-11
You probably need to run the command I gave in the first post from the terminal and then run
```
sudo apt-get dist-upgrade
```

I am guessing there are some updates yet to be downloaded/installed and that is causing the problems..

---

### Post by mtn on 2006-11-11
Thanks again. Is there a way of popping up a terminal using the keyboard? I'm really stuck with out a menu!:(  

Also, is it better to do a fresh install? Windows upgrads were always a bad idea in my experiance so was wondering if this is the same for Ubuntu?

Cheers

---

### Post by darrenm on 2006-11-11
Alt-f2 then type gnome-terminal to get a command line.

Updates / upgrades on Ubuntu are nothing like Windows. They always work fine (apart from the dodgy flash that is ;) ) I wouldnt bother reinstalling for this. Just force the update manager to continue or reboot then do it.

---

### Post by mtn on 2006-11-12
thanks darrenm,

that has done the job. Edgy seems nice, I like the new boot slash screen!

many thanks

P.S. been toying with the idea of putting the amd64 version on my amd64 but have this impression that the 64 version is not as well supported as the 386 version. I don't really understand how this works so could be totally wrong. any ideas?

---

