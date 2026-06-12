---
title: "Wubi installation problem"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by raja34766 on 2012-05-16
I decided to use Ubuntu 11.10 a few days ago.I downloaded the ISO. Then I installed Wubi and it installed perfectly. When I restarted my computer and pressed enter on that ubuntu option at the boot screen menu I got this error  [COLOR=Red]"prefix" is not set?[/COLOR] [COLOR=Red]          [/COLOR]
[COLOR=Black]I tried many times uninstalled Wubi then reinstalled it but got the same result everytime. [/COLOR]
I am using Windows XP SP 3. 
Please help me to install WUBI successfully.

Thank You

---

### Post by roelforg on 2012-05-16
> **raja34766 said:**
> I decided to use Ubuntu 11.10 a few days ago.I downloaded the ISO. Then I installed Wubi and it installed perfectly. When I restarted my computer and pressed enter on that ubuntu option at the boot screen menu I got this error [COLOR=red]"prefix" is not set?[/COLOR] 
[COLOR=black]I tried many times uninstalled Wubi then reinstalled it but got the same result everytime. [/COLOR]
I am using Windows XP SP 3. 
Please help me to install WUBI successfully.
 
Thank You
 
I've got that too.
 
I looked in to it and it's the result of dynamically detecting the partition on which wubi is installed: The prefix will be detected by a second command in the chain, it doesn't matter.
It's just a little hack, but it doesn't stop ubuntu from booting, does it?
 
The technical explaination:
Wubi causes several bootloaders to chainload:
WinBOOTLOADER -> grub4dos
Usually, grub searches for a partition and boots from that.
With wubi, the partition isn't set because there isn't any.
Instead there is a file (root.disk)
It's specified to load as: /ubuntu/disks/root.disk
There's no (hd<number>,<number>) to say grub where it is,
so grub warns about that and it searches every partition but the warning is to say that it might yield unexpected results.
The logic is:
Say this is there:
```

(hd0,0)/boot/myroot.disk
(hd0,1)/boot/myroot.disk

```
Grub would pick the first one, even though you might've meant to pick the second.
This isn't possible with wubi as the installer won't let you create such a setup, so just ignore it.
 
 
 
(PS. It took me a while to post b/c my internet went down after clicking "new reply" but before clicking "submit reply")

---

### Post by raja34766 on 2012-05-16
So what should I do now to get rid of this problem?

---

