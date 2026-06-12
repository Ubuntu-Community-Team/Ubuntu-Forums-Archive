---
title: "Update problem"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by itFinallyWorks on 2008-01-18
Today a few updates showed up in the update manager.  They all downloaded fine, except for xserver-xorg-core.  This one failed, giving the error message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

My Internet connection is just fine since I have gotten updates many other times with no problems.

So, I think this may just be a bug or an error in the update system.  Please advise.

Thanks.

---

### Post by NineseveN on 2008-01-18
I got the same issue...tried it three times today. Still a no-go.

---

### Post by eobard on 2008-01-18
I'm having the same issue myself. At least I know it's not on my end.

---

### Post by NineseveN on 2008-01-18
Open the update manager, click the **check** button, there is a new version of this update (first one was broken), if you force the manager to check again, it will find the new file instead of trying to install the broken one that was removed.

---

### Post by petermck on 2008-01-18
I got the same problem but fixed it by pointing the repositry setting to the main server instead of the local country one (ftp.ubuntu.co.nz in my case).

---

### Post by elamericano on 2008-01-19
I was going to change my repository server too, but I knew I'd find the answer here. I prefer the check button solution. Now I'm waiting for the update that fixes this bug, 'cause I'm under the impression that after finding the first version automatically, it was never going to find the new one by itself.

---

### Post by thelatinist on 2008-01-19
> **petermck said:**
> I got the same problem but fixed it by pointing the repositry setting to the main server instead of the local country one (ftp.ubuntu.co.nz in my case).

It makes sense that that would work because when you change the repository it will update apt's lists.  Basically it had the same effect as forcing an update check.

---

### Post by NineseveN on 2008-01-19
> **elamericano said:**
> I was going to change my repository server too, but I knew I'd find the answer here. I prefer the check button solution. Now I'm waiting for the update that fixes this bug, 'cause I'm under the impression that after finding the first version automatically, it was never going to find the new one by itself.

I don't know the specifics, but I'm guessing that tomorrow, at whatever time the Update Manager is scheduled to automatically check for updates on your system, it would have found the new one and scrubbed the old one. It only checks once per day unless you force it with the check button or update command, so it would have fixed itself tomorrow. The problem we ran into is that once it had today's list, whatever updates were not installed remained in the manager. That list, if I understand correctly, is saved locally on your machine until the next update check.

---

