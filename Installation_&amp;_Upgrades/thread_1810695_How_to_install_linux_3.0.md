---
title: "How to install linux 3.0"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by alegomaster on 2011-07-23
Hi, I started to upgrade my computer (which has ubuntu 11.4 installed) kernel to 3.0. I tried to compile from source and boot, but I believe something messed up and I had to reinstall Ubuntu. This time I plan to use the precompiled version here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/) . Can anyone tell me how you install the precompiled version. Any help will be good.

---

### Post by alegomaster on 2011-07-23
Nevermind, I fixed the problem. I just had to use dpkg with the -i flag.

---

### Post by MAFoElffen on 2011-07-23
> **alegomaster said:**
> Hi, I started to upgrade my computer (which has ubuntu 11.4 installed) kernel to 3.0. I tried to compile from source and boot, but I believe something messed up and I had to reinstall Ubuntu. This time I plan to use the precompiled version here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-oneiric/") . Can anyone tell me how you install the precompiled version. Any help will be good.
Yes--- But see below first.

Install it as a debian package > the kernel for your architecture, the header for your architecture and the header all... 

Then you are going to want to apply the patch below.  The reason you are going to want to apply this patch... Because of the numbering shema change, it's going to be challenge afterwards:

 - The kernel numbering schema changed for this kernel.
 - Debian packages check the kernel numbering schema for a range before installing or compiling to ensure that it's going to be able to work for the kernel it was intended for.
 - Recent kernels prior to the 3.0 series kernel, was set to 2.4.x, then 2.6.x...  

See where that version check limit needs to be changed?  Oneiric already includes this patch. (You are running Natty.)

patch /usr/src/linux-3.0-0-generic/include/linux/rcupdate.h according to [http://choon.net/forum/read.php?21,82725](http://choon.net/forum/read.php?21,82725) 
> rcu: avoid build error for third-party modules

The initial definition of __kfree_rcu() checked a static inline function  argument to see if it was a compile-time constant.  Apparently not all  compilers are willing to put up with this at all optimization levels.  Add a nasty comment and remove the warning, relying on the fact that  __kfree_rcu() is called only from kfree_rcu(), which always passes in a  compile-time constant.

```

diff --git a/include/linux/rcupdate.h b/include/linux/rcupdate.h
index 99f9aa7..58b13f1 100644
--- a/include/linux/rcupdate.h
+++ b/include/linux/rcupdate.h
@@ -814,13 +814,14 @@ static __always_inline bool __is_kfree_rcu_offset(unsigned long offset)
     return offset < 4096;
 }
+/*
+ * Intended to be called only from the kfree_rcu() macro.
+ */
 static __always_inline
 void __kfree_rcu(struct rcu_head *head, unsigned long offset)
 {
     typedef void (*rcu_callback)(struct rcu_head *);
-    BUILD_BUG_ON(!__builtin_constant_p(offset));
-
     /* See the kfree_rcu() header comment. */
     BUILD_BUG_ON(!__is_kfree_rcu_offset(offset));

```Refer to this post:
[http://ubuntuforums.org/showpost.php?p=10924650&postcount=306](http://ubuntuforums.org/showpost.php?p=10924650&postcount=306)

---

