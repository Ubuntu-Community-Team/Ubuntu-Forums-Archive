---
title: "Fresh server: installation fine, but PC reboots"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Witchole on 2007-07-19
Hi,

Yet another newbie with installation problems.  I've been battling with this for a couple of days now, have not found any other thread reporting the same problem, so would appreciate any advice on how to go about diagnosing this kind of problem.


Both Ubuntu 6.10 and 7.04 server i386 installation CDs produce the same result - the installation runs seemingly with no problems, on restarting the computer there are three grub menu options if I press Escape:
e.g.
> Ubuntu, kernel 2.6.20-15-server
Ubuntu, kernel 2.6.20-15-server (recovery mode)
Ubuntu, memtest86+
The memory test runs without any errors, but both of **the kernel boot options result in "Starting up..." being briefly displayed, then the PC simply reboots, with no error message whatsoever**.

* The "acpi=off noapic nolapic" boot options have no effect on this behaviour.

* Have also tried many different BIOS settings

* Can boot using the "Rescue a broken system" option from the installation CD, but can not find any error log to indicate what went wrong:

* changed /etc/default/bootlogd to read BOOTLOGD_ENABLE=Yes

* /var/log/boot still contains "(Nothing has been logged yet.)"


I suspect the following might be a useful step forward, but I'm not sure how to proceed now.  I got hold of a Puppy installation CD, and noticed it has an option to install in "co-exist" mode, so chose that.  On restarting the PC, the grub menu is identical, and now linux does start up, but there appears to be a mix of Ubuntu and Puppy:

- the Feisty server options like Apache and MySQL server are started

- I can login as the user I configured during the Ubuntu installation

- There are some Puppy-related errors such as
> WARNING: Couldn't open directory /lib/modules/2.6.18.1
and
FATAL: Could not load /lib/modules/2.6.18.1/modules.dep  No such file or directory

- "uname -a" reports
> Linux ubu 2.6.18.1 #1 Sat Nov 11 07:52:06 PUP 2006

- and /proc/version contains
> Linux version 2.6.18.1 (root@puppypc) (gcc version 3.4.4) #1 Sat Nov 11 07:52:06 PUP 2006

TIA!

---

### Post by Witchole on 2007-07-19
Update: This thread seems to be about the same problem:

[[7.04 server edition] reboot pc after grub]("http://ubuntuforums.org/showthread.php?t=504076")

will try suggested solution and report back...

---

### Post by Witchole on 2007-07-19
> **Witchole said:**
> Update: This thread seems to be about the same problem:

[[7.04 server edition] reboot pc after grub]("http://ubuntuforums.org/showthread.php?t=504076")

will try suggested solution and report back...

...yup, the problem does appear to have been caused by the VIA processor on this PC, and 

[wallyhall's solution]("http://ubuntuforums.org/showpost.php?p=2371357") did the trick (many thanks!):

```
apt-get install linux-386
```

---

