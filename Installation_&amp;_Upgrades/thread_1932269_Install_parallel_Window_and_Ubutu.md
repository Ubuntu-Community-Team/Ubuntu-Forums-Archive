---
title: "Install parallel Window and Ubutu"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by IUViet on 2012-02-27
,

My Window was renew because of failure, After finished I cannot see how to login to Ubutu. I have done it long time ago but I forgot now. I want to know that how can I login in Ubutu that I sure it still includes partation remain.

 Could someone help me to solve this problem?

---

### Post by chait on 2012-02-27
Hi,
 If you have re-installed Windows and if you still can view the linux partition, I think you need to re-install GRUB boot-loader so that it can show a menu for which operating system to boot.

Cheers!!.:popcorn:

---

### Post by Mark Phelps on 2012-02-28
If you installed Ubuntu using Wubi (from inside Windows), Ubuntu is GONE.  You would have to reinstall it from scratch.

If you installed to a separate partition, then use the Win7 Disk Management utility to confirm that the partition is still there.

If it's still there, you can use an Ubuntu desktop CD to reinstall GRUB, as per below:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by IUViet on 2012-02-28
Thanks for all,
I have succeed with install now.

---

### Post by Mark Phelps on 2012-02-28
Glad to see you got it working.  Please use the Thread Tools at the top of the thread to mark this as SOLVED.  thanks

---

