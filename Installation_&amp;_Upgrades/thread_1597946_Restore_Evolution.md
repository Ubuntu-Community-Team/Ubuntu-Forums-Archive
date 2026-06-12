---
title: "Restore Evolution"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by jws957 on 2010-10-15
I was running 10.04 and my hd crashed in the area of the operating system.  I bought a new hd and started with a fresh install of 10.10  I mounted the old hd and can access all the files under the "home" folder - and others also.  I copied the hidden folder ".evolution" to the new hd but when I started Evolution, it started from "scratch".  Are there other files I should copy and where are they located?  (I had two users set up but only one was running email.)

---

### Post by sgosnell on 2010-10-15
From the user folder using email, copy .gconf/apps/evolution.

---

### Post by drs305 on 2010-10-15
When you use the backup option in Maverick (File, Backup Settings) it stores both the *~/.evolution* and *~/.camel-certs* folders.

---

### Post by jws957 on 2010-10-16
I copied the .gconf/apps/evolution folder but that didn't change the behavior.  Evolution still starts up like it's the first time.

---

### Post by jws957 on 2010-10-16
Solved.  After copying the folders above I "bit the bullet" and configured the account from scratch, but when I did, I found I had all my emails and it worked as it should!

---

