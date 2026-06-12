---
title: "can't compile upstream kernel 2.6.33-rc8 on 9.10"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2010-02-23
I'm trying to build kernel 2.6.33-rc8 according to the documentation here: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) , but at a late stage in the compilation, I'm encountering the following error:

```
/usr/bin/make -f ./debian/rules 	debian/stamp/binary/pre-linux-image-2.6.33-rc8-custom
make[1]: Entering directory `/root/src/linux-2.6.33-rc8'
====== making target debian/stamp/install/linux-image-2.6.33-rc8-custom [new prereqs: ]======
This is kernel package version 11.015.
echo "The UTS Release version in include/linux/version.h"; echo "	   \"\" "; echo "does not match current version:"; echo "	   \"2.6.33-rc8-custom\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/version.h
	   "" 
does not match current version:
	   "2.6.33-rc8-custom" 
Please correct this.

```

what am I doing wrong?

---

### Post by cenwesi on 2010-02-25
Yep, i am getting this too even on the final kernel 2.6.33

---

### Post by CHaoSlayeR on 2010-02-25
See this bug: [https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/498747](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/498747)

...and out of it get this patch: [http://launchpadlibrarian.net/37497839/kernel-package-2.6.33.patch](http://launchpadlibrarian.net/37497839/kernel-package-2.6.33.patch)

And apply it on your system. Your other choice is to wait for an updated version of kernel-package in karmic.

C]-[aoZ

---

### Post by cenwesi on 2010-02-26
i tried applying this patch or so i think and i get this...

patch -p1 < ../kernel-package-2.6.33.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- /usr/share/kernel-package/ruleset/misc/version_vars.mk     2008-11-24 18:01:32.000000000 +0100
|+++ /usr/share/kernel-package/ruleset/misc/version_vars.mk     2010-01-06 16:16:28.662667462 +0100
--------------------------
File to patch:

---

### Post by CHaoSlayeR on 2010-02-26
Well, just cd into / and use sudo.

---

### Post by GrandTheft on 2010-02-27
Works for me! Thx !
GT

---

### Post by azwan on 2010-03-01
it seem make-kpkg cant find utsrelease.h in include/linux folder
quick workaround is i make symlink
ln -s ./include/generated/utsrelease.h ./include/linux/utsrelease.h
and make-kpkg again

good luck

---

### Post by hamidoo on 2010-03-02
> **azwan said:**
> it seem make-kpkg cant find utsrelease.h in include/linux folder
quick workaround is i make symlink
ln -s ./include/generated/utsrelease.h ./include/linux/utsrelease.h
and make-kpkg again

good luck

Well, that's simple and strait and works for me.It happens also in 2.6.33 mainline!
thx for sharing

---

