---
title: "can't upgrade to 16.04"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by hmiersch on 2016-10-03
i keep trying to upgrade from 14.04 to 16.04 but i keep getting the same errors again and again:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.12+16.04.20160126-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.12+16.04.20160126-0ubuntu1_all.deb) Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/account-plugins/account-plugin-twitter_0.12+16.04.20160126-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/account-plugins/account-plugin-twitter_0.12+16.04.20160126-0ubuntu1_all.deb) Size mismatch

it's always those 2 files. and the annoying thing is that i don't even need those files because i don't use facebook or twitter. never have, never will.

so what's going on here? and what can i do about it?

---

### Post by ian-weisser on 2016-10-03
Please show us the entire output. Context matters.

---

### Post by hmiersch on 2016-10-04
The context is that I use the software updater. It tells me that 16.04 is available, I click upgrade, and some time and several mouse clicks later a window appears with those 2 error messages.

---

### Post by ian-weisser on 2016-10-04
Well, that sure is context!

Please open a terminal, and run the command 'do-release-upgrade'.
If it fails, please show us that output.

---

### Post by hmiersch on 2016-10-04
i did that. once again it downloaded lots of files. and again those 2 files produced error messages. here's the end of the output:Get:11 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial/main javascript-common all 11 [6,066 B]                                 Get:12 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial/main libfile-homedir-perl all 1.00-1 [46.0 kB]                          Get:13 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial/main libxml-xpathengine-perl all 0.13-1 [37.1 kB]                       Get:14 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial/main secureboot-db amd64 1.1 [2,740 B]                                  Fetched 2,969 kB in 0s (0 B/s)                                                                                             Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial/main account-plugin-facebook all 0.12+16.04.20160126-0ubuntu1 [2,854 B]  Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial/universe account-plugin-twitter all 0.12+16.04.20160126-0ubuntu1 [2,338 B]Fetched 0 B in 0s (0 B/s)                                                                                                  Could not download the upgrades The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far have been kept. Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.12+16.04.20160126-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/account-plugins/account-plugin-facebook_0.12+16.04.20160126-0ubuntu1_all.deb) Size mismatch Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/account-plugins/account-plugin-twitter_0.12+16.04.20160126-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/account-plugins/account-plugin-twitter_0.12+16.04.20160126-0ubuntu1_all.deb) Size mismatch Restoring original system stateAbortingReading package lists... Done    Building dependency tree          Reading state information... DoneBuilding data structures... Done hope this helps

---

### Post by hmiersch on 2016-10-04
PS i have no idea why its all bunched up like that. when i pasted it in, it was formatted the same way as in the terminal window.

---

### Post by Kleenux on 2016-10-04
Before upgrading to 16, try 

remove any unused source in  /etc/apt/sources.list.d/ 
do

[FONT=Courier New]apt-get update
apt-get upgrade   (*upgrade current*)
apt-get clean
apt-get install -f
dpkg --configure -a
apt-get install -f   (*yes, a second time*)
[/FONT]
as root, or prefix all comands with 'sudo'.
This should fix / show where problems reside...

---

### Post by ian-weisser on 2016-10-04
> **hmiersch said:**
> Fetched 0 B in 0s (0 B/s)                                                                                                  **Could not download the upgrades The upgrade has aborted. **Please check your Internet connection or installation media and try again. All files downloaded so far have been kept. 

It's not a size mismatch. The upgrade seems to be aborting in the same location each time.
Is your disk perhaps full?
Open a terminal and try the following to see:```
df
df -i
```

Your output is all bunched up because you didn't use [code] tags for it.

---

### Post by hmiersch on 2016-10-05
> **ian-weisser said:**
> It's not a size mismatch. The upgrade seems to be aborting in the same location each time.yeah, its always the same 2 files.> **ian-weisser said:**
> Is your disk perhaps full?nope, not even a quarter full.

---

### Post by hmiersch on 2016-10-10
> **ian-weisser said:**
> Your output is all bunched up because you didn't use [code] tags for it.guess what? i just tried to reply to another post, and the multi-line output that i copied in from the terminal was bunched up again when i clicked preview. and yes, i did use [code] tags. Looks like the CRs and/or LFs in the original text are simply ignored. Question is why? whats going on here?

---

