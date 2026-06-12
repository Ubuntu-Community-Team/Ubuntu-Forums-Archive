---
title: "Update Manager error:"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by firsttiner on 2008-01-13
Hi there,

I am new to Ubuntu. Just tried to use the Update manager GUI to get all the latest updates and got the following error:

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

It wanted to do a partial upgrade???

And I cannot locate the bug report file???

---

### Post by santaslittlehelper on 2008-01-13
Hi

This may sound silly but here goes anyway.
What version of Ubuntu are you running? From terminal,
```
lsb_release -a
```

Also maybe the following output would be helpful.
```
cat /var/log/dist-upgrade/apt.log
```

Probably best to put the output in code tags or attach in a text file.

---

### Post by Partyboi2 on 2008-01-13
In a terminal (Applications>Accessories>Terminal)
type
```
sudo apt-get dist-upgrade
```
Post back any error messages it may give you.

---

### Post by David_1cog on 2008-01-15
Same problem here and 'sudo apt-get dist-upgrade' fixed most of the packages that would not install via Update Manager.

I had one remaining problem with libflickrnet - see [https://bugs.launchpad.net/ubuntu/+source/libflickrnet/+bug/182130](https://bugs.launchpad.net/ubuntu/+source/libflickrnet/+bug/182130) (to be fixed in next release and a workaround is in the comments - see comments by 'fork').

---

### Post by Partyboi2 on 2008-01-15
> David_1cog
I had one remaining problem with libflickrnet - see [https://bugs.launchpad.net/ubuntu/+source/libflickrnet/+bug/182130](https://bugs.launchpad.net/ubuntu/+source/libflickrnet/+bug/182130) (to be fixed in next release and a workaround is in the comments - see comments by 'fork')
that bug is related to Hardy alpha, worked for me :) not sure if it would work for Feisty.

---

