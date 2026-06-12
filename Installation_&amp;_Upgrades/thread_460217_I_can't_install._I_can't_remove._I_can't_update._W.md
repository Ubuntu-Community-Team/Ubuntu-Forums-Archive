---
title: "I can't install. I can't remove. I can't update. What's going on??"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Soglad on 2007-05-31
As the thread title says, I can't install, remove or update anything. If I install I get in terminal:

davitt@ArdRi:~$ sudo apt-get install vlc
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing ndisgtk (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

If I remove I get:

davitt@ArdRi:~$ sudo apt-get remove beryl
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing ndisgtk (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

And if I try to update I get:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Dynamic MMap ran out of room, E: Dynamic MMap ran out of room, E:Error occurred while processing ndisgtk (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

My system also starts running really slow & glitchy at times and I can't open Synaptic because it freezes.

What do I do?

---

### Post by Soglad on 2007-05-31
*ehem*

---

### Post by wpshooter on 2007-05-31
Why are you trying to remove beryl ?

---

### Post by Soglad on 2007-05-31
It's a test, I would never wish to do that :D

---

### Post by Soglad on 2007-05-31
So I'll just re-install Ubuntu then....................................................?

---

### Post by christhemonkey on 2007-05-31
Are you running low on hard drive space?

Whats the output of this command:
```
df -ha 
```

---

### Post by wpshooter on 2007-05-31
> **Soglad said:**
> It's a test, I would never wish to do that :D

Perhaps you should.  Every time I see posts like this I see the word beryl mentioned.

---

### Post by Soglad on 2007-05-31
I would try, but as I've said, I can't install, remove or update, hahaha

Here's what I got back from that command:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              27G   11G   15G  42% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                378M  220K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
procbususb            378M  100K  378M   1% /proc/bus/usb
udev                  378M  100K  378M   1% /dev
devshm                378M     0  378M   0% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                   378M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
nfsd                     0     0     0   -  /proc/fs/nfsd
rpc_pipefs               0     0     0   -  /var/lib/nfs/rpc_pipefs
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc

---

### Post by srt4play on 2007-05-31
Post the contents of your /etc/apt/sources.lst

---

### Post by christhemonkey on 2007-05-31
Ok after a quick google it would appear the problem is apt has a fixed cache for lists and yours has exceeded that.(! Congrats!)

All you need to do is edit the file /etc/apt/apt.conf:
```
sudo nano /etc/apt/apt.conf 
```

 and add this line to the end:
```
APT::Cache-Limit "16777216";
```

Then try sudo apt-get update-ing
```
sudo apt-get update 
```

---

### Post by Soglad on 2007-05-31
Ok I opened /etc/apt/apt.conf by using "sudo gedit /etc/apt/apt.conf" because I didn't understant that format the terminal brought up and "APT::Cache-Limit "1000000;" was already in it because I think I tried that before.

Oh yeah, I brought up /etc/apt/sources.lst and this is what is in there:






















Get that? (There's nothing in it :p)

---

### Post by srt4play on 2007-05-31
Yeah that was a typo, should have been /etc/apt/sources.list

Did you change the cache-limit number to what was suggested?

---

### Post by Death_Sargent on 2007-05-31
its not beryl for gods sake 

its addept

tell me where you trying to install something before this happened and the install failed 

if so run this

```
dkpg configure -a
```

if that does not work then look into cleaning out whatever it uses as a chache as it sounds like an error is being held over from a long past problem

---

