---
title: "updating grub packages"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by cmwhidmore on 2011-06-15
I was updating some of my packages, when I found this as the result when I try to update GNOME:
```

root@UBUNTU1104_1165213_HP_PC:/root# apt-get install gnome
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages
root@UBUNTU1104_1165213_HP_PC:/

```

CAn somebody help me with this?

---

### Post by tommcd on 2011-06-16
Are you using any third party repositories? This includes those all too problematic PPA repos. If you are, then this is likely the source of your problem. If you remove the third party repos this problem will likely go away.
Why, and how, are you trying to update Gnome?

---

