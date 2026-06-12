---
title: "Natty Bug 'update manager' - Could not initialize the package information"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by yug_matt on 2011-05-27
Hi,

   I have done a scratch install of Ubuntu 11.04 (natty) on my PC with an unrecoverable error during the installation phase. However, I was able to boot the PC with Natty but my package manager and update managers are not working properly. I am pasting below the error message shown by package manager.

[COLOR=Blue]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/COLOR]

Could you help resolve this issue.

Thanks in advance.

Regards
Yug

---

### Post by Rubi1200 on 2011-05-27
Hi and welcome to the forums :-)

Run these commands in the terminal and let us know if it fixes the problem:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by yug_matt on 2011-05-27
Hey Thanks for the quick reply !

The steps did work fine for me. I have found these exact steps just before reading your reply from a fiesty related thread. 

Anyway, Thanks for your help :p

---

### Post by Rubi1200 on 2011-05-27
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page so that other users can find a working solution if they encounter the same problem.

---

### Post by viking_bjorn on 2011-06-24
Hi,

Many thanks for the tip.

Worked perfectly!:P

Kind Regards,
viking_bjorn

---

### Post by Rubi1200 on 2011-06-24
> **viking_bjorn said:**
> Hi,

Many thanks for the tip.

Worked perfectly!:P

Kind Regards,
viking_bjorn
You are more than welcome :-)

And welcome to the forums.

---

