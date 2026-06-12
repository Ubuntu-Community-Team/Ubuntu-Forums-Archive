---
title: "error in upgrade to 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by catlover2 on 2010-10-10
hi,
i ran```
sudo apt-get dist-upgrade
```and after a reboot i get this:
```
init: Failed to spawn ureadahead main process: ubable to execute: no such file or directory
```after that i get a strange multi-boot screen, as i only have 1 OS.

after THAT, i get some scrolling text that ends with this:
```
Starting advanced periodic command scheduler: fcrom.
```
and at that point it freezes and here i am on a livecd.

i included some pics of the screen.

thanks,
catlover

---

### Post by mionescu on 2010-10-10
It seems that something went terribly wrong during upgrade. Did you reboot after all the upgrades were completed? I noticed that when I upgraded my system (using the update-manager) at some point it was a message that I need to reboot the computer, even though the update  was not complete. I did not until everything ended.

Did you try to select the other kernel version or the safe option? If none of them work, you might need to do a fresh installation.

---

### Post by catlover2 on 2010-10-10
no, i waited till i got the name@name-laptop:~$  

and the multi-boot disappeared as quickly as it came.

---

### Post by catlover2 on 2010-10-10
UPDATE:
the multi-boot screen is back!

with the safe mode i can get to a root command line.

what can i do from there??

---

### Post by mionescu on 2010-10-11
I would try to run again apt-get dist-upgrade and hope for the best.

---

### Post by catlover2 on 2010-10-11
ok, will do!

---

### Post by catlover2 on 2010-10-11
alright,

i told it to
```
apt-get dist-upgrade
```
and it said it needed to get 52KB yes, 52KB of archives(!!),
then it said there was an error getting the archives.

so, as far as i can tell,

it didn't do anything.

thanks,

catlover

---

