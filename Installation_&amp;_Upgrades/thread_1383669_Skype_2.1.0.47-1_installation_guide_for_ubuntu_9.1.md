---
title: "Skype 2.1.0.47-1 installation guide for ubuntu 9.10 64 bit"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by kouchris on 2010-01-17
hey all, 
this is my first post that i try to help people so be kind :)
i have been having problems installing skype from deb.
i was reading fotums trying to get rid of the "another skype instance thing"(sorry i dont remember the message), and even when i was online i couldnt get any calls through even when running skype with gksu command.

anyway.. the way i did it is:

get the skype version from the skype website :
[http://www.skype.com/intl/en/download/skype/linux/choose](http://www.skype.com/intl/en/download/skype/linux/choose)
i got the Ubuntu 8.10+ 64-bit
first i ran:
```
sudo apt-get autoremove skype skype-common
```
to remove existing versions of skype.
then i target Desktop
```
cd ~/Desktop
```
and then
```
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
```

and i got it up and running well..
i hope this helps..
dont kill me for making mistakes... im not that good in ubuntu..i found this though searching...
let me know if it helped..

---

### Post by cariboo on 2010-01-17
Just a note, **apt-get autoremove** just removes unneeded dependencies, it doesn't actually remove the program. For more info have a look at:

```
man apt-get
```

---

### Post by kouchris on 2010-01-20
> **cariboo907 said:**
> Just a note, **apt-get autoremove** just removes unneeded dependencies, it doesn't actually remove the program. For more info have a look at:

```
man apt-get
```

hey thanks for the tip,
so what should the command be?
should you add uninstall command or some thing before that ?

---

### Post by cybrsaylr on 2010-02-11
> **kouchris said:**
> 
and then
```
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
```

and i got it up and running well..
i hope this helps..
dont kill me for making mistakes... im not that good in ubuntu..i found this though searching...
let me know if it helped..

When I put that code in terminal this is what came up:
> -desktop:~$ sudo dpkg -i skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
dpkg: error processing skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb

Now what?

---

### Post by cybrsaylr on 2010-02-15
Ended up going to the Skype site and downloading it. Skype then installed and seems to be working fine after testing it and making a call.

---

