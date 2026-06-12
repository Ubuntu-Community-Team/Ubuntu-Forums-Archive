---
title: "dpkg-reconfigure -a complains but nothing seems wrong"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by ocwo92 on 2012-07-06
When I upgraded our computers to 12.04 in May, all of the upgrades went smoothly, except (maybe?) on two of them where suddenly dpkg-reconfigure isn't working.

When I execute dpkg-reconfigure -a, I get errors such as the following:

```
$ sudo dpkg-reconfigure -a
Package `ia32-libs-multiarch' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: ia32-libs-multiarch is not installed
```

However, attempting to install the library yields:

```
$ sudo apt-get install ia32-libs-multiarch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs-multiarch:i386 is already the newest version.
```

I have tried to uninstall the package and run dpkg-reconfigure -a again, but then it makes a similar complaint about another package, and removing that package makes it complain about yet another package. Reinstalling the packages does not help, as dpkg-reconfigure -a just starts complaining about these packages again.

What could be wrong here, and how do I fix this issue?

---

### Post by jmfal on 2012-07-06
Try this

```
 sudo dpkg --configure  -a           
```

---

### Post by ocwo92 on 2012-07-06
> **jmfal said:**
> ```
 sudo dpkg --configure  -a
```
returns almost immediately with no error messages or anything. (This, and the behavior of dpkg-reconfigure, makes me worry that maybe the dpkg database is broken on my system, but I have no idea how to check that or repair it.)

---

### Post by drmrgd on 2012-07-06
> **ocwo92 said:**
> returns almost immediately with no error messages or anything. (This, and the behavior of dpkg-reconfigure, makes me worry that maybe the dpkg database is broken on my system, but I have no idea how to check that or repair it.)

There's not yet any blatant evidence that dpkg is broken.  If dpkg --configure -a doesn't return anything, it just means there are no packages that have not yet been configured by dpkg.  

Why are you trying to run dpkg-reconfigure -a?  Are there packages that you need to reconfigure for some reason, or is there another goal you have in mind?

---

### Post by ocwo92 on 2012-07-06
> **drmrgd said:**
> Why are you trying to run dpkg-reconfigure -a?  Are there packages that you need to reconfigure for some reason, or is there another goal you have in mind?
I don't need to run it right now, and in fact the problem has been around for weeks. I discovered it when a package didn't get fully installed and I attempted to catch up with dpkg-reconfigure. It failed as described above, but I managed to install the package by simply removing it and trying once again.

I can't rely on such luck, however, so I want to prevent the problem that I'm going to face when eventually I'll need dpkg-reconfigure.

---

### Post by jmfal on 2012-07-06
Your sig says 10.10

Did you go from 10.10 straight to 12.04??

---

### Post by ocwo92 on 2012-07-06
> **jmfal said:**
> Your sig says 10.10

Did you go from 10.10 straight to 12.04??
No, but for some reason I'm not allowed to edit my profile details. I went from 11.10 to 12.04.

---

### Post by jmfal on 2012-07-06
dplkg is working ,, if there are no broken  packaged it will not do anything.

I would open update manager an untic all in other softwae tab, wait   a few seconds and put a tic back in except for cd at top(both of them)

then run ```
 sudo apt-get update    
```

and ```
  sudoapt-get upgrade   
```

  and post back any errors

---

### Post by ocwo92 on 2012-07-06
> **jmfal said:**
> ... and post back any errors
No errors, no warnings, nothing. Not after unticking all but the essentials and apt-get update/upgrade, nor after re-ticking everything followed by another apt-get update/upgrade. (That is, except for a kernel update to 3.2.0-27 that is kept back while waiting for dependencies to trickle out to the download mirrors, but that's hardly the issue here.)

And dpkg-reconfigure -a is still not working. :-/

---

### Post by jmfal on 2012-07-06
Is everything good??

when the headers are ready you will get an update

---

### Post by ocwo92 on 2012-07-06
I'm not worried about the kernel update; it's common for kernel packages to be held back for a day or two waiting for dependencies to propagate to the download mirrors.

Everything is working fine on both computers, except for that pesky dpkg-reconfigure thing. I probably wouldn't have worried too much had not one of the computer happened to be a server. Clients are easy to reinstall.

---

### Post by jmfal on 2012-07-06
If your really worried about it you can reboot to grub and go into the recovery kernal, select dpkg-fix broken packages and run that, follow the prompts and enter the command that it asks for.
if it asks for configure enter command as I gave it to you.

when you get back to  menu  click resume normal boot and follow prompts.

---

### Post by drmrgd on 2012-07-06
> **ocwo92 said:**
> I don't need to run it right now, and in fact the problem has been around for weeks. I discovered it when a package didn't get fully installed and I attempted to catch up with dpkg-reconfigure. It failed as described above, but I managed to install the package by simply removing it and trying once again.

I can't rely on such luck, however, so I want to prevent the problem that I'm going to face when eventually I'll need dpkg-reconfigure.

Fair enough!

This problem is perplexing as there really only seems to be an issue with the dpkg-reconfigure component of dpkg, and there no indication that anything else is broken.  Since dpkg-reconfigure is part of the whole dpkg package, about the only thing I could think to do is to reinstall dpkg.  It's a little nerve wracking to mess with the whole dpkg system for that utility, though.

---

