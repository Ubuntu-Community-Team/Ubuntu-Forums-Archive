---
title: "Save Ubuntu installation while reinstalling Windows 7"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by dejansoftware on 2011-03-24
Hi,

is it possible to save Ubuntu installation over Wubi in Windows because I have to totally reinstall Windows 7 and after that I would like to use Ubuntu that I already had installed.

Thanks

---

### Post by wilee-nilee on 2011-03-24
> **dejansoftware said:**
> Hi,

is it possible to save Ubuntu installation over Wubi in Windows because I have to totally reinstall Windows 7 and after that I would like to use Ubuntu that I already had installed.

Thanks

Wubi is inside of W7 it will be gone if you recover W7. You can move the wubi to a partition though, but if your running a recovery from the HD rather then a disc you will probably overwrite the whole HD.

---

### Post by bcbc on 2011-03-24
> **dejansoftware said:**
> Hi,

is it possible to save Ubuntu installation over Wubi in Windows because I have to totally reinstall Windows 7 and after that I would like to use Ubuntu that I already had installed.

Thanks
backup the \ubuntu\disks directory. There should be only two files root.disk and swap.disk. The root.disk is the important one but back them both up.

It's not straightforward to get your old Ubuntu restored after the reinstall, but it's not difficult either. the main issue is that the partition number and UUID from the install is saved within the root.disk. So you have to do some mods to that on the fly. I advised someone about this recently - I'll look for the thread.

---

### Post by bcbc on 2011-03-24
[http://ubuntuforums.org/showpost.php?p=10584729&postcount=4](http://ubuntuforums.org/showpost.php?p=10584729&postcount=4)

Personally if I was reinstalling I'd create a dedicated partition for Ubuntu. If you decide to do this, it's possible to migrate your existing Wubi.

---

