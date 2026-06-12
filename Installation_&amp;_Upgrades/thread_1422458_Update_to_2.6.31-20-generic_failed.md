---
title: "Update to 2.6.31-20-generic failed"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-03-05
I did an update today and it failed. Had a crash report. I did a recheck for updates and it said I was up to date. When I restarted it told me to sudo .... I forgot the rest to complete but said it encountered errors. Anyone else ? How do I redownload this update to retry?

---

### Post by stlsaint on 2010-03-05
For us to better help you please post the exact error message you are getting...and are you able to boot fully into the system?

---

### Post by Silvertones on 2010-03-05
Yes you'd never know there was an issue with the update. When I boot the latest is 19 as before.
E: linux-image-2.6.31-20-generic: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

What I think happened is that the restart dialog popped up prematurly during the initial install. By the time I noticed that the updates had not completed I had hit restart. I think things are broken. I tried to reinstall but these messages keep coming up.

---

### Post by stlsaint on 2010-03-05
try in terminal:

```
sudo aptitude clean
```
or 
```
sudo apt-get autoclean
```

After that try updating again:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by Soul-Sing on 2010-03-05
Most probably your sourceslist is messed up/stuck. If you can run your desktop, please try choosing another server from synaptic package manager, and try again via:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Silvertones on 2010-03-05
I ran those and am now in the process of re downloading. I had done a complete removal  linux-image-2.6.31-20-generic figuring that the packedge was OK but I still got errors so I assume the DL pckg was broken. It'll be awhile before I report back. Dialup takes a bit!!
It's interesting though. There are 2 pckgs  linux-image-2.6.31-20-generic:
1. says x86/x86_64  this is the one that was installed
2. x86 this one is  linux-image-2.6.31-20-generic pae
My machine is not 64 bit
Just thinking out loud.

---

### Post by Silvertones on 2010-03-05
Still get the error.
In order to try Leoguant's idea I have to wait untill tomorrow and go back to the library for WiFi. Too much for dialup.
So this is interesting. If I run the update manager set to the original site it says I'm up to date. When I tried from a UK site it had 58 files that was going to take too long and is risky with dialup. So it appears that the record of updates is stored at the server & not on the local machine? Thus it's probably going to update everything again from day one?
What would happen if I remove via synaptic all of the so called installed programs that have 2.6.31-20 in the name or version & then did the```
 sudo aptitude clean
```

---

