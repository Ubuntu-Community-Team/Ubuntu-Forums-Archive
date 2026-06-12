---
title: "apt-get / dpkg error"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by remu on 2009-04-11
I was trying to install firefox-3.5 after it installed it kept giving me a "Bus error (core dumped)" so after I tried removing it, I now keep getting this message from apt whenever I try to do something. How can I resolve it? [http://pastebin.com/f4b8c47e](http://pastebin.com/f4b8c47e)

---

### Post by cariboo on 2009-04-11
Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages to repair the problem.

Jim

---

### Post by remu on 2009-04-11
Doing that didn't make a difference.

---

### Post by paul_in_london on 2009-04-11
Try these commands:

sudo rm -vf /var/lib/apt/lists/*
sudo rm -vf /var/cache/apt/archives/*.deb
sudo dpkg --configure -a 
sudo aptitude update 
sudo aptitude safe-upgrade 
sudo aptitude upgrade 

You may also need to do this:

sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

and then rerun the first set of commands.

If this doesn't work, reboot and repeat.

---

### Post by remu on 2009-04-11
I followed your instructions, and again after rebooting. Unfortunately I am still having the same issue.

---

### Post by paul_in_london on 2009-04-11
Are you still getting the same output?

The packages "firefox-3.1" and "firefox-3.5" both "point to" v3.5 of firefox - see Synaptic.

Similarly with "firefox-3.2" and "firefox-3.6"

See if this works:

sudo aptitude -f install
sudo dpkg -P --force-depends firefox-3.1
sudo aptitude install firefox-3.1
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude upgrade 

Instead of/as well as this you may need to do:

sudo aptitude -f install
sudo dpkg -P --force-depends firefox-3.5
sudo aptitude install firefox-3.5
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude upgrade

---

