---
title: "[SOLVED] &amp;quot;The following packages have been kept back&amp;quot;?"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Fraoch on 2008-07-07
My Ubuntu 8.04 64-bit desktop has unfortunately been relegated to a server (long story, I would rather it hadn't...) so I'm interfacing with it over command line via SSH.

This is working well but I've had the line in the subject for a month or two now whenever I update:

```
mark@Sauron:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  language-support-writing-en linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
mark@Sauron:~$
```

(I used "sudo apt-get update" before, of course, and I am getting new updates and packages.)

I figured maybe it needed a restart, but that didn't help.

So how do I get these to install or at least get rid of the notice?  Thanks!

---

### Post by VMC on 2008-07-07
This might work. Someone with a similar problem, used Aptitude to fix their held back files:

```
sudo aptitude dist-upgrade
```

---

### Post by avtolle on 2008-07-07
The key here is ```
dist-upgrade
```whether using apt-get or aptitude. This will allow the kernel upgrades to be downloaded and installed.

---

### Post by Fraoch on 2008-07-07
Works perfectly!

At first I thought this might upgrade me to Ibex since this is the procedure you use to upgrade distributions, but I recall you have to edit sources.list before you do that.

Thanks!

---

### Post by avtolle on 2008-07-07
Glad everything is OK. Would you please mark this thread as Solved, using the thread tools at the top? Thank you.

---

### Post by Fraoch on 2008-07-07
Done, thanks for the help.

---

