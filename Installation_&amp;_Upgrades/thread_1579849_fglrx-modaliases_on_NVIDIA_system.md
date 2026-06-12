---
title: "fglrx-modaliases on NVIDIA system?"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by Sin@Sin-Sacrifice on 2010-09-22
```
Killmandline:$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ***fglrx-modaliases***
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

So I even had to double check because I thought I had gone crazy.

```
Killmandline:$ dmesg | grep NVIDIA
[    0.000000] ACPI: OEMN 00000000bff9a4e0 008F4 (v01 NVIDIA NTUNEOEM 00312E30 MSFT 00000097)
[   28.786704] nvidia: module license 'NVIDIA' taints kernel.
[   29.440865] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Killmandline:$ 
```

---

### Post by efflandt on 2010-09-22
What is your question?  It is perfectly normal for the system to update kernel module aliases for things that you may not necessarily be using at the time, just in case you do use them.  It is not like replacing 15 kB of a file is going to grind you to a halt.

For example I have a USB hard drive that can boot on various computers with various video chips.

---

### Post by jpepin on 2010-09-23
Interesting.  I saw the same thing and thought it looked odd, since I have an nvidia graphics card.  Of course, I assumed it was OK, and installed it.  After that, it took an exceptionally long time to for me to login after boot (ie boot time was normal, but logging in took forever), and my cpu was at 100% usage.  Running "top" in the terminal showed that a process called "backend" was the culprit.  I searched for fglrx in synaptic, and uninstalled the 2 instances it found.  After that, the problem seems to have gone away.  

Did you install the update, and if so, did it give you any trouble?  I just want to make sure I fixed it, and that my assumption that fglrx caused it was not just a red herring for something else that may be going on.

---

### Post by Sin@Sin-Sacrifice on 2011-09-18
I did install the updates later and ran into some problems. Removing the fglrx-modaliases solved those issues.

---

