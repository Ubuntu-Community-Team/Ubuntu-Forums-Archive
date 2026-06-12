---
title: "Authentication Failed"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Business Convert on 2007-05-09
Hi everyone:

Old 6.06 LTS user here.  Wanted to do upgrade to 7.04, so went through process to upgrade to 6.10 before upgrading to 7.04.

Now, when trying to upgrade to 7.04 from 6.10, I get the following error message from the update manager:

Authentication Failed:

tommy@05-001:~$ gksu "update-manager -c"
warning: could not initiate dbus
extracting '/tmp/tmpaeffRC/feisty.tar.gz'
authenticate '/tmp/tmpaeffRC/feisty.tar.gz' against '/tmp/tmpaeffRC/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
tommy@05-001:~$ 

So, that's the command line result from the terminal entry.

Thoughts anyone?

Thanks!

---

### Post by Business Convert on 2007-05-09
ttt

---

### Post by Chappy7777 on 2007-05-09
I am not at all sure of this, but I think where you went wrong was replacing 6.06 with 6.10  I did that a month or so back, and had a number of buggy hassles. So I uninstalled 6.10 and reinstalled 6.06LTS IMHO, 6.06 is the "sweetspot" of Ubuntu. If you look at the order CD page (download page too, I think), you'll see that 6.10 is no longer on there. If I decide to install Feisty, it will be to a separate HDD, so that I can keep using 6.06  A few years ago I bought a bay w/2 docks(at least that is what I call them), so the bay is in the PC, and a HDD goes into each dock. I can have as many docks filled w/HDDs as I want, each being a totally separate install. All being setup on the same system. It's a cheap way to solve and prevent many problems. I have an empty HDD in a dock waiting for Feisty to show in the mail. If it works better than 6.06, great, if not, no problem, since I will still have 6.06 setup and working. 

Good luck and God speed getting your system working. Sorry I was of no "practical" help. At least ya got a reply,

Chappy

---

### Post by Business Convert on 2007-05-09
thanks Chappy!

yep, I think the 6.06 LTS version has longer support, better and smoother operation.  makes sense really; not bleeding edge for the fun of it.

Thanks again!

---

### Post by Business Convert on 2007-05-09
ttt

---

### Post by voam on 2007-06-13
I had the exact same problem.

Running 

```
sudo mkdir /root/.gnupg
```

as described [here ]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/82464") solved it for me.

---

