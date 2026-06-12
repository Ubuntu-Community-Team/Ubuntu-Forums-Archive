---
title: "ubuntu version upgrading"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by iMac on 2006-03-04
I have sampled many versions of Linux, but I am now settling in with ubuntu. I have one question, to upgrade a ubuntu version, lets say from an older version to Breezy. Would I get a notice in the updating program about the new version avaliable to update, or would I need to download the cd all over again and upgrade the version I have? In other words, if a new version of ubuntu comes out will I have the option to upgrade the version (with the ubuntu updating program) without downloading it over again, and booting from the disk and choosing update, like in some other distro's?

Also does anyone know the command to check and see if Firestarter is running in the background?

---

### Post by engla on 2006-03-04
Hello.

Currently it works like this: You won't be notified about any updates outside your release (Breezy), however if you consciously choose to change your repositories, you can upgrade from one release to the next... this can also be done with an install cd, without the need for a complete reinstall.

And perhaps even an upgrade tool will be developed in time for the release (there is one in the works for making this smoother for dapper > dapper + 1) that can be downloaded to make the process even easier.

So when dapper is released, a note will be posted about how to upgrade your breezy install. (This is already possible if you want to try the alpha/beta version, search around for "dist-upgrade dapper" or something)

Also, on my system it seems 
'sudo /etc/init.d/firestarter status'
returns the status of firestarter. You have to be root to run even the status command though :-(

---

### Post by iMac on 2006-03-04
Thanks for your help. Is it worth upgrading versions? Also, is there a way to check which version i am currentley running? The firestarter command worked great (it worked out of the root account).

---

### Post by jpkotta on 2006-03-04
You can check the version of Ubuntu you have with
```
cat /etc/lsb-release
```

Dapper is in development now.  If you're feeling adventurous, or have a spare partition you can install it on, go for it.  If you need a reliable computer, wait until it's released.  Also, it's fairly difficult to go from a new version to an old version of Ubuntu, from what I've read.

---

