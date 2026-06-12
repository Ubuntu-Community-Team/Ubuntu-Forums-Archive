---
title: "How to update/upgrade overnight?"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by Daz1969 on 2007-07-27
Hi,

I'm still pretty new to Ubuntu, but learning fast(ish)
I've tried various searches and haven't found anything that quite covers this....

I'm on a limited download broadband deal - except overnight when there's no limit!!
That's why I'd like to do any large updates/upgrades overnight.

Anyway, I've set up a crontab that runs a script file in the dead of night.
The script is seen to run as it logs some messages in a file.

The script file just contains the standard:

sudo apt-get update
sudo apt-get upgrade

..plus some echo commands for logging

I don't think the update/upgrade is working.
The problem, as I see it, is that sudo wants a password - and I'm in my bed!

Is there a way to do this unattended??

Thanks for your help and patience with this one.

Darron

---

### Post by KiloEleven on 2007-07-27
Probably easiest would be to give root a password - 
```
sudo passwd
```
It will ask for your current password, then it will ask for a new root password. You should probably make this different than your current password. Now, you can log in as root by doing 
```
su -
```
Then it is just
```
crontab -e
```
to edit the crontab for root. This will negate the need to put the "sudo" command at the beginning of the line.

---

### Post by Daz1969 on 2007-07-30
Thanks - I'll try that.

Darron

---

