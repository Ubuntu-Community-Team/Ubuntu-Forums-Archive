---
title: "chrome crashed with sigabrt in check_match()"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by dunbrokin on 2014-07-21
Cannot get Chrome, or Chromium or Steam to install...Firefox already installed and not a problem...as is Thunderbird. The title comment is what I find in the automatic bug report.....but there is no sign of a bur report like this that I can find on Launchpad. Any suggestions?

---

### Post by QIII on 2014-07-21
It would be helpful if you could tell us how you have tried to install these.

Cheers!

---

### Post by dunbrokin on 2014-07-21
OOops, sorry. I used the Ubuntu Software Centre to install them Chromium was in the repositories as is Steam. Chrome I downloaded from the official google site and use the Software Centre to install.

---

### Post by dunbrokin on 2014-07-23
Here is some more information....Steam will not run for me either. This is part of what I get when I run Steam --verbose. I have already done the sudo chmod 1777 suggestion...but it does not make any difference and, in fact, the suggestion comes up again next time...despite the permission being changed.

[0724/104700:ERROR:shared_memory_posix.cc(167)] Creating shared memory in /dev/shm/org.chromium.Chromium.shmem.libcef_18132305107414046285 failed: Read-only file system
[0724/104700:ERROR:shared_memory_posix.cc(170)] Unable to access(W_OK|X_OK) /dev/shm: Read-only file system
[0724/104700:FATAL:shared_memory_posix.cc(172)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.

---

### Post by dunbrokin on 2014-07-24
Mark as solved. The file /dv/shm/ is a symlink file. Delete this file...don't bother trying to change the permission as it does not work. Instead - mkdir a new version, change the permissioning as suggested and away you go.

---

### Post by dunbrokin on 2014-07-29
Nope, that was just a temporary solution...that only seemed to work once. Now when I delete /dev/shm or change the permission, nothing happens...neither Chrome nor Chromium nor Steam will open. All opened a few days ago. What is going on????

---

### Post by dunbrokin on 2014-07-29
Ah, what a pain, when I delete and then mkdir /dev/shm and chmod it again it works....not sure for how long....and not sure what will stop it again.....so am keeping this unsolved.

---

