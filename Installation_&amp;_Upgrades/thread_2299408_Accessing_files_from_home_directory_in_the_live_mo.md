---
title: "Accessing files from home directory in the live mode - help!"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by marcin34 on 2015-10-18
Dear Users,

I have the following problem: I tried to upgrade my Ubuntu 14.04 Trusty Tahr to 15.04. Unfortunately, the installation failed, some files could not be downloaded and now I can't even boot (I get "attempted to kill init" etc.). I have an installer of Ubuntu 14.04 on a USB stick, I can easily reinstall the system and I will do that. Where does the problem lie? I have important files in my home directory and I don't want to lose them. First I plugged in the installer USB and an external HDD in order to backup all files from the CPU. I copied all files from other partitions, but not the ones from the home directory - I get "permission denied". Could anybody give me some advice on how I can safely copy these files before reinstallation?  Thank you in advance!

Marcin

---

### Post by howefield on 2015-10-18
Use the terminal command..

```
sudo -H nautilus
```

and you should be able to copy your files.

Not having a back up of the files that you would not want to lose is poor practice. 

Another seemingly little known process is that installing Ubuntu on top of an existing Ubuntu will not destroy your /home folder if you :- during the install procedure, select "Something Else" at the partitioning screen, mount the partitions as appropriate (do not mark / for formatting) and a clean install will be performed leaving your old /home folder intact. I wouldn't recommend this in your scenario without a back up of your files in place, accidents do happen ;)

---

