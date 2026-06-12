---
title: "Wine won't install"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by SPConsole on 2010-02-12
I cant get wine to work!  Help!

I added the wine repository, and went to install it, and this is what I got.
```
####@############:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
####@############:~$ 

```

I tried "apt-get install -f" and the "Fix Broken Packages" option in Synaptic, neither did anything.

This exact error has occurred on 4 different systems for me.  (all of my systems)

---

### Post by drpereira on 2010-02-16
Same here... anyone?

---

### Post by ahso4271 on 2010-02-16
I compile the sources like in the readme. Then with a new release you can simply do from the install directory: "make uninstall"

if u accidentaly removed the install dir: "whereis wine" and remove those files manually leaving the hidden files .wine

---

