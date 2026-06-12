---
title: "Feisty Upgrade - 403 Forbidden"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by pcpinkerton on 2007-04-13
This morning I ran apt-get update, then apt-get upgrade.

All packages listed were upgraded except : 

linux-image-2.6.20-14-generic_2.6.20-14.23_amd64.deb

Terminal Output:: (after running --fix-missing )
*****
apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.20-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.1MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main linux-image-2.6.20-14-generic 2.6.20-14.23
  403 Forbidden [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_amd64.deb)  403 Forbidden [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
*****

Is this just a glitch in the server ? 403 Forbidden [IP: 91.189.88.31 80]

I have not seen this error before since I started using Ubuntu.

My current system is:
2.6.20-14-generic #2 SMP Mon Apr 2 16:32:46 UTC 2007 x86_64 GNU/Linux
Acer Aspire 5102 AMD Turion 64(x2) 2GBDDR2

---

### Post by nbound on 2007-04-13
Trust me you dont wanna upgrade to that, it could possibly render your PC unbootable, possibly why it was been made unavailable, a replacement should be up soon

---

### Post by selfeky on 2007-04-13
I have the same problem.
I'm guessing that that kernel was faulty and it caused a lot of problems to other people thus they took it off the servers till its fixed.

kind regrads.

---

### Post by pcpinkerton on 2007-04-13
If indeed it is a problem with the kernel Image and it was rendered inaccessible do to problems then congratulations to the repository keepers and a job well done.

This type support "problem prevention"  is rare.

great job.

---

### Post by selfeky on 2007-04-13
> **pcpinkerton said:**
> 

This type support "problem prevention"  is rare.

great job.

I agree!
gr8 job

---

### Post by nbound on 2007-04-13
Except for those of us who installed before it was blocked, luckily i have my trusty laptop :P

---

### Post by rand76 on 2007-04-13
I was wondering about that 403 too. Props to the repo guys for the fast catch! :guitar:

---

### Post by louieb on 2007-04-13
Yes:guitar: they did a great job this time. They must have learned something from the xorg update debacle of 2006. Everybody makes mistakes. The smart ones don't make the same one twice.

---

### Post by Neobuntu on 2007-11-16
Same prob with Gusty now.


Anyone have some concrete info on this problem?

---

### Post by jdong on 2007-11-16
Yes, this behavior is intentional. See my post at [http://ubuntuforums.org/showpost.php?p=3783704&postcount=4](http://ubuntuforums.org/showpost.php?p=3783704&postcount=4)

---

### Post by jdong on 2007-11-16
Closing thread, continue discussion at [http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

Thanks

---

