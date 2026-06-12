---
title: "do-release-upgrade did not seem to upgrade kernel,  manual kernel upgrade not working"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by psyc2 on 2014-05-08
I recently updated my distribution to trusty. Everything seems to go fine. 

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
root@zelda:/home/jlangton# 
```

However, when I check the kernel I get: 
```
uname -a
Linux zelda.dyndns.tv 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I thought a release upgrade would upgrade the kernel as well, so am a bit mystified. So I went about trying to upgrade the kernel manually - did some commands to download it with dselect, but it didn't install. So I used apt-get to find it in the cache then tried to install it: 
```
apt-get install linux-image-generic-lts-trusty
```

It seemed to go through fine. I rebooted the server, did uname, and got the same response. My kernel doesn't look like it's changed. 

What am I doing wrong?

thanks!

---

### Post by deadflowr on 2014-05-08
What's
```
dpkg -l linux-image*
```
say?

---

### Post by psyc2 on 2014-05-08
It includes the image I installed in my original post. 

I hosed the machine - tried to remove old kernel and for some reason networking stopped though it's booting and reporting old kernel still. It's a cloud machine, with web access to terminal, so the print out of the dpkg command is incomplete - but basically it lists a lot of images, and in there is the trusty one that I tried to install as indicated in my original post. 

I'll have to restore from a snapshot.

Can you tell me though - shouldn't a release upgrade also upgrade the kernel? 

And - I guess - I'll have to try and manually upgrade the kernel, obviously didn't work this time

---

### Post by deadflowr on 2014-05-08
Could you post the output of the command I suggested?

---

