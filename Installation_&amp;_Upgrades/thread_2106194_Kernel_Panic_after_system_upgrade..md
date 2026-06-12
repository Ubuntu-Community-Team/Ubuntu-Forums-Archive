---
title: "Kernel Panic after system upgrade."
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by rafaelhsn on 2013-01-18
Hello!

I'm using Lubuntu 12.04.

Usually (once a week, on more) the system ask to perform some updates. I always do it. But on last update, after reboot, I got a kernel panic ,apparently.

I already performed a fresh install (resized the partition to preserve my data) , it runs fine at first moment, but after update same crash again.

I cannot determine which update is because usually the system asks to perform lot of packages upgrades at same time. (like 10, 100 or more updates).

This is a photo of the error.
[http://db.tt/eRbsD40z](http://db.tt/eRbsD40z)

Anyone can give a advise about what I can do?

Thanks in advance.

---

### Post by ajgreeny on 2013-01-18
There has just been a kernel upgrade yesterday or today in 12.04, so it is possible that the new kernel is the problem.  Try booting to the previous good kernel from grubmenu (hold shift at boot if you don't normally see the menu) to see if that is OK, and if it is just configure grub to use that kernel instead of the newest, or pin the version of the kernel using apt preferences to avoid continual notification to update it.

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name
Pin: version (number from repos)
Pin-Priority: 1001
```

---

### Post by rafaelhsn on 2013-01-18
> **ajgreeny said:**
> There has just been a kernel upgrade yesterday or today in 12.04, so it is possible that the new kernel is the problem.  Try booting to the previous good kernel from grubmenu (hold shift at boot if you don't normally see the menu) to see if that is OK, and if it is just configure grub to use that kernel instead of the newest, or pin the version of the kernel using apt preferences to avoid continual notification to update it.

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name
Pin: version (number from repos)
Pin-Priority: 1001
```

solved! chosed the old kernel and worked =)

thanks!!

---

### Post by amjjawad on 2013-01-18
I see ajgreeny has taken good care of you ;)

Glad you managed to logged in.
I have asked you a question on Lubuntu Group on Facebook and will ask the same Q here again:

What was the kernel that caused the problem?


Please, don't forget to mark your thread as Solved :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by kayvee on 2013-01-19
I think I have the exact same issue. I was able to fix it though simply by selecting an older kernel during the startup. My question is how long do I have to keep logging into the system using the older kernel? If this new kernel issue is fixed, how would I know of it? 

> **amjjawad said:**
> 
I have asked you a question on Lubuntu Group on Facebook and will ask the same Q here again:

What was the kernel that caused the problem?


In my case, it is 3.5.0-22-generic

---

### Post by amjjawad on 2013-01-19
> **kayvee said:**
> In my case, it is 3.5.0-22-generic

Hi there,

The OP has Lubuntu 12.04 and from your Kernel that caused the problem, I can tell that you are using Lubuntu 12.10.

Luckily, I have Lubuntu 12.10 installed on my Test Laptop so I will upgrade the Kernel and see what is going to happen :)

---

### Post by amjjawad on 2013-01-19
Upgrade done and I'm running now Kernel: 3.5.0.22-generic and everything is fine. Perhaps it got fixed now or perhaps it has a problem with some other hardware. Nothing is prefect :)

---

