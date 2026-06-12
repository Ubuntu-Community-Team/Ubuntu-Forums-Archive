---
title: "X error of failed request:  BadRequest"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by Schappenberg on 2011-10-20
Hi,

after updating Ubuntu 11.04 to 11.10, i can not run any "3D graphic" program (sorry, don't know how else to describe).
For example running "glxgears" (same error trying to run urbanterror, torcs, ..., except different current serial number in output stream):
```
$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```like the error message supposed to me, the ATI driver have a problem, so i re-installed the newest fglrx (2:8.892, Catalyst 11.9) from the AMD driver page, no effect.

Does anyone can give me a hint what to do or where i can get further informations how to find out what causes this error?

Thanks in advance

Schappenberg

---

### Post by larsivi on 2011-10-24
I am seeing this too.

---

### Post by larsivi on 2011-10-24
Ok, I solved this for me.

I removed all fglrx packages that I had installed using

```
sudo apt-get remove --purge
```

and then installed the fglrx-amdcccle-updates and fglrx-updates packages, rebooted and it worked.

There is a conflict between those two lines, possibly because my fglrx packages at some point came from a ppa repository. If they came from the official ubuntu repos, it is an Ubuntu packaging bug.

---

### Post by Schappenberg on 2011-10-24
You removed fglrx*, right?

---

### Post by larsivi on 2011-10-24
@Schappenberg: yes

---

