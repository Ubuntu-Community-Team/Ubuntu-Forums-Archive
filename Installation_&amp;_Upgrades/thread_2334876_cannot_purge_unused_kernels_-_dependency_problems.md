---
title: "cannot purge unused kernels - dependency problems"
date: 2016-08-23
forum: Installation &amp; Upgrades
---

### Post by nebukadnezzar2 on 2016-08-23
Hello,

I've repeatedly been receiving error warnings saying that /boot has not enough disk space remaining.
I tried to purge unused kernels. First I identified them using:
$ uname -r

and

```
$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
```

then I tried to purge the oldest one using:

```
$ sudo dpkg --purge
```

Following the instructions on this site [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

I finally got to a point I do not know what to do next: I have dependency problems when purging the kernels, but I do not know of which kind and how to solve them. Furthermore, it seemed like I deleted the header for the older kernels.
Here's what I got:

```
annika@nebukadnezzar:~$ uname -r
4.2.0-38-generic
annika@nebukadnezzar:~$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
pi  linux-image-4.2.0-34-generic                          4.2.0-34.39~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-35-generic                          4.2.0-35.40~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                          4.2.0-36.42~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
annika@nebukadnezzar:~$ sudo dpkg --purge linux-image-4.2.0-34-generic
dpkg: dependency problems prevent removal of linux-image-4.2.0-34-generic:
 linux-image-extra-4.2.0-34-generic depends on linux-image-4.2.0-34-generic.

dpkg: error processing package linux-image-4.2.0-34-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.2.0-34-generic
annika@nebukadnezzar:~$ sudo dpkg --purge linux-headers-4.2.0-34-generic
dpkg: warning: ignoring request to remove linux-headers-4.2.0-34-generic which isn't installed
annika@nebukadnezzar:~$ sudo dpkg --purge linux-image-4.2.0-34-generic
dpkg: dependency problems prevent removal of linux-image-4.2.0-34-generic:
 linux-image-extra-4.2.0-34-generic depends on linux-image-4.2.0-34-generic.

dpkg: error processing package linux-image-4.2.0-34-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.2.0-34-generic
```

Would be great if you could help me!
Thank you!

---

### Post by Impavidus on 2016-08-23
You should also remove the linux-image-extra-... packages. The old headers are safe to remove too. To get a decent list of the packages you can remove, use```
dpkg -l | grep linux-
```The packages with a long and old version number embedded in their name can be removed. Typically, that would be```
linux-headers-4.4.0-31
linux-headers-4.4.0-31-generic
linux-image-4.4.0-31-generic
linux-image-extra-4.4.0-31-generic
```and similar for other versions, but depending on what you installed exactly, there may be a lowlatency or signed-image among them. You cannot uninstall the linux-image-4.4.0-... package while keeping the linux-image-extra-4.4.0-... package, so you have to reverse the order or simply uninstall them simultaneously:```
sudo dpkg --purge linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34
```

---

### Post by nebukadnezzar2 on 2016-08-28
Thank you for your advice.
However, I did not succeed following your instructions. Using the command
dpkg -l | linux-

I get an error:
annika@nebukadnezzar:~$ dpkg -l | linux-
No command 'linux-' found, did you mean:
 Command 'linux' from package 'user-mode-linux' (universe)
linux-: command not found

Do I need to install this program first?
Thank you!

---

### Post by howefield on 2016-08-28
> **nebukadnezzar2 said:**
> 

```
annika@nebukadnezzar:~$ dpkg -l | linux-
No command 'linux-' found, did you mean:
 Command 'linux' from package 'user-mode-linux' (universe)
linux-: command not found
```

Try..

```
dpkg -l | grep linux-
```

---

### Post by Impavidus on 2016-08-28
Thanks. I fixed the command above.

---

