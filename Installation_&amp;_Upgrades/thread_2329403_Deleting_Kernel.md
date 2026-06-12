---
title: "Deleting Kernel"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by S.User on 2016-07-01
Hello,

My newest Kernel 4.4.0-21 is causing errors, the machine got no mouse and eth0 isn't found ([http://ubuntuforums.org/showthread.php?t=2329340](http://ubuntuforums.org/showthread.php?t=2329340)).
When booting the previous one 3.13.0-91 it's all fine.

So I wanted to delete 4.4.0-21.

But ```
sudo apt-get remove linux-image-4.4.0-21-generic
``` (or dpkg --purge....) returns that 4.4.0-21 is not found!
It's the same whether I include "generic" or leave it out.
However 4.4.0-21 is on the list of kernels one can boot from and it's the newest.

I've done upgrade / update under 3.13.0-91 and all seems to be up to date.

How would one handle this best? I like to have the most recent kernel... but it must work. So a more recent one might help or I will need to get rid of 4.4.0-21 after all- but how?

Stephan

---

### Post by CharlesA on 2016-07-01
Check dpkg to see what the name of the package for that kernel is:

```
dpkg -l | grep linux-image
```

Can you post the exact output you get if you try to purge it from apt-get?

---

### Post by Impavidus on 2016-07-01
Kernel 4.4.0-28 was distributed this week on 16.04. If you install all updates, it should have been installed, but apparently it hasn't. It may solve your issues though.

Which version of Ubuntu do you run? I expect 16.04 based on the 4.4 kernel, but can you confirm?

---

### Post by S.User on 2016-07-02
> **CharlesA said:**
> Check dpkg to see what the name of the package for that kernel is:

```
dpkg -l | grep linux-image
```

Can you post the exact output you get if you try to purge it from apt-get?

Sure... 


Boooted on 4.4.0-21 as well as 3.13.0-91 it returns exactly the same (well that makes me suspicious...):

```
dpkg -l | grep linux-image
ii linux-image 3.13.0-91-generic    3.13.0-91.138
    i386    Linux kernel image for version 3.13.0 on 32 bit x86 SMP

ii linux-image-extra-3.13.0-91-generic    3.13.0-91.138
    i386    Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP

ii linux-image-generic    3.13.0-91.97
    i386    Generic Linux kernel image
```

> **Impavidus said:**
> Kernel 4.4.0-28 was distributed this week on 16.04. If you install all updates, it should have been installed, but apparently it hasn't. It may solve your issues though.

Which version of Ubuntu do you run? I expect 16.04 based on the 4.4 kernel, but can you confirm?

Yes it is 16.04.
I also ran

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

It tells me that everything is up to date.
An issue with the repositories? They are ... as main, restricted, iniverse, multiverse as below (example):

```
deb http://ch.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty universe
deb http://security.ubuntu.com/ubuntu/ trusty-security universe
```

So can't see anything wrong with that either.

---

### Post by S.User on 2016-07-02
Now this seems to have been solved:

I had to add kernel 4.4.0-28 manually.
It did not come though an upgrade. But it was shown on the list in the Synaptic GUI.
So I selected it manually, installed and I'm now getting:

```
dpkg -l | grep linux-image
ii  linux-image-3.13.0-91-generic         3.13.0-91.138                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-28-generic          4.4.0-28.47~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic   3.13.0-91.138                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic    4.4.0-28.47~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-generic                   3.13.0.91.97                                        i386         Generic Linux kernel image


```

The machine now boots straight into the newest kernel and mouse as well as eth0 are found.

Why it didn't come with the update (which I would have expected with an automatic security update) I cannot tell.

But maybe that's something to be aware of...

Stephan

---

### Post by Impavidus on 2016-07-02
You must get the package linux-image-generic upgraded to version 4.4.0-28. I think the way to do that is by upgrading the package linux-generic to that version, which will automatically upgrade the former to that version as it's a dependency of the latter.

---

### Post by deadflowr on 2016-07-02
> An issue with the repositories? They are ... as main, restricted, iniverse, multiverse as below (example):

```
deb http://ch.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ trusty universe
deb http://security.ubuntu.com/ubuntu/ trusty-security universe
```
So can't see anything wrong with that either.

Nothing at all wrong with that, if you are running 14.04.

You can help figure out what's really going on by posting the full sources.list:
Easy way is to just open with gedit and copy and paste here:
```
gedit /etc/apt/sources.list
```

---

### Post by S.User on 2016-07-09
> **deadflowr said:**
> Nothing at all wrong with that, if you are running 14.04.

You can help figure out what's really going on by posting the full sources.list:
Easy way is to just open with gedit and copy and paste here:
```
gedit /etc/apt/sources.list
```

Well, after I now added and selected kernel 4.4.0-28 manually, it all works.
Guess that's just something to keep in mind.
The kernel was there so it was part of the repositories but it didn't get recognised as the most recent one and wasn't installed, hence I had to do it manually.
No idea why but it's ok as long as one knows...

Stephan

---

