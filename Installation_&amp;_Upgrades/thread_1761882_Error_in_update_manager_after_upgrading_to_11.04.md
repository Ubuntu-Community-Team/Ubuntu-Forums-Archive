---
title: "Error in update manager after upgrading to 11.04"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by li0id on 2011-05-18
I get this error when i open the system update. I installed a fresh copy of ubuntu 11.04 on my netbook via a usb stick. After booting in i ran system update and updated my system and then opened it again and got this message. Can anyone explain to me what this means and how to fix it please.


Could not initialize the package information.

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Blasphemist on 2011-05-18
Try this.
Run synaptic package manager, edit menu, fix broken packages.

---

### Post by wojox on 2011-05-18
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

I've seen this question a lot on Launchpad.

---

### Post by li0id on 2011-05-18
thanks, clearing the list worked. you guys over here are good people. thanks again.

---

### Post by zlot on 2011-05-22
> **wojox said:**
> ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```I've seen this question a lot on Launchpad.
wojox!
Thanks! Yours is the only thing I've found in two days that actually did something. Everyone else says, "Fix broken packages." Well, if the "fix broken package" package is broken, too, that makes things difficult. What had happened to me is that my 11.04 system was going along fine until the update manager got broke somehow, and there was no fixing it or even removing it. Your suggestion here is doing something, and I'm hoping that when I continue my efforts to repair the update manager, I'll be OK. I've even installed another 11.04 virtual machine - I was about ready to trash this one. Thanks again!
-zlot

---

### Post by zlot on 2011-05-22
Still can't remover or repair &^%$&#$# update manager! 
Oh, well, I'll just proceed with my new install....

---

