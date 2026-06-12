---
title: "Upgrade Manager wants 2.6.32-41 when present"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by SBFree on 2012-05-27
I am running 10.04 Desktop LTS as a file server for storage. Update manager wanted to update a kernel to 2.6.32-41 generic along with some security patches. I let it but after upgrading there were errors on startup and the case speaker was beeping. I did a restore to find that I already was running kernel 2.6.32-41 . I can't understand why the update manager would offer it when it wasn't needed. My reading suggests that I will be offered 12.04 LTS in July. The restored system seems stable and works. Is something wrong that I was not offered an update to 11.10 at some point?
Scott

---

### Post by raja.genupula on 2012-05-27
do you got any updates after doing this ?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

is it showing any?

---

### Post by SBFree on 2012-05-29
Thank you so much for the reply.
scott@scott-files:~$ sudo apt-get update
Gets updates, about 13 MBs

but
sudo apt-get upgrade
sudo apt-get dist-upgrade

both respond with the same error:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I tried to kill what ever was using apt-get with:
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a

After that I ran:
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@scott-files:~$ 

So after this I ran the Update Manager and it no longer tells me that it wants to upgrade anything at all. The indication to upgrade to the same Kernel I have is gone. The Update Manager is configured to only show new distributions for "Long term Support releases only". From my reading it looks like 12.04 LTS may not be available yet as an upgrade. Update Manager did not show that updates were needed but running the apt-get's above caused system to want to restart. On restart the system triggers the internal speaker to beep like a warning indicator. I am assuming that the same updates that caused this problem were loaded by apt-get.

Thanks for the help and response.
Scott

---

### Post by raja.genupula on 2012-05-29
its looking like a BUG , report it to launchpad .

---

### Post by SBFree on 2012-05-29
It is definitely a problem related to the Kernel. I let the install get updates but excluded updating the Kernel without a problem.
Scott

---

