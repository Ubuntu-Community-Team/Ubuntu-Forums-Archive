---
title: "Upgrd 7.10:failed to fetch .../medibuntu.sos-sts/repo/dist/feisty/..."
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-10-23
Upon upgrading to 7.10 from 7.04 with the System upgrade manager, I got these error on the "Preparing the upgrade" step.

Failed to fetch [http://medibuntu.sos-sts.com/repo/distfeisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/distfeisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/distfeisty/non-free/binary-386/Packages.gz](http://medibuntu.sos-sts.com/repo/distfeisty/non-free/binary-386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/distfeisty/free/Sources.gz](http://medibuntu.sos-sts.com/repo/distfeisty/free/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/distfeisty/non-free/Sources.gz](http://medibuntu.sos-sts.com/repo/distfeisty/non-free/Sources.gz) 404 Not Found

There were too many threads found with the "medibuntu.sos-sts" string and I don't have the time to investigate right now.

So what is wrong ?

Can it be fixed ?

Do we have to wait for a bug fix or an announcement ? If so, has it been done alredy ?


Is the full CD Install of 7.10 ok ?  If so, i'll simply download it and do a full install.

---

### Post by Browser_ice on 2007-10-24
Hummm, no one has an answer ?

In the mean time I am downloading the full install CD. I would rather upgrade as there are some stuff I want to keep but they are not essential.

---

### Post by brunog on 2007-10-24
Sorry, do not think I have answer for you.
Also have a problem.
Get the following error:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.bz2) MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.bz2) MD5Sum mismatch

Also prefer to run update.

Will try again later

---

### Post by TeaSwigger on 2007-10-24
Hello, Medibuntu changed their address, that's all. :) To resume using medibuntu repos, see the following page and follow the instructions to enter their new info.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Edit: oh and don't forget to remove the medibuntu.sos repos from your sources.list or through your package manger, Synaptic or Adept.

---

### Post by i8bugs on 2007-10-24
Go to System> Administration> Software Sources
Login
Hit Third Party Software TAB
Remove those not found lines from the list
Exit
Try reinstalling again.

i8bugs

---

