---
title: "iso verification - No keyserver available"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by asgard2 on 2020-05-01
Hi,

I try to verify the xubuntu 20.04 iso, but the verification is not possible.

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

```
gpg --keyid-format long --keyserver hkp://keyserver.ubuntu.com --recv-keys 0x46181433FBB75451 
gpg: keyserver receive failed: No keyserver available
gpg --keyid-format long --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 0x46181433FBB75451 
gpg: keyserver receive failed: No keyserver available

```

On my router, I set anything to unblock ... the problem can not be my network.

Current system: xubuntu 18.04

thx

---

### Post by asgard2 on 2020-05-02
The page [http://keyserver.ubuntu.com:11371](http://keyserver.ubuntu.com:11371) is reachable via browser, what could be the problem?
How can I verify the iso file?

Well, somehow it worked now.

What I could find out:
- 1. when I used hkp://keyserver.ubuntu.com  and I tried with a restricted network before ... the import will fail with this message, even if it is currently reachable
- 2. when I used hkp://keyserver.ubuntu.com:80 and I tried 1. before, the import will fail, even when the port 80 is reachable any time

Maybe this blocked my verification? ... :lolflag:

---

