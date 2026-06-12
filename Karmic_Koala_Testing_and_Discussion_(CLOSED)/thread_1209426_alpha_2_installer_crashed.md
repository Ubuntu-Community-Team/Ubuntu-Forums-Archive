---
title: "alpha 2 installer crashed"
date: 2009-07-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-07-10
Hi all i installed Alpha 2 although the installer crashed and wouldn't let me send a bug report it boots up fine. Should i be worried at all?

Also grub isn't listing my windows partition, is there a quick fix for that?

---

### Post by Craigy90 on 2009-07-10
> **ELD said:**
> Hi all i installed Alpha 2 although the installer crashed and wouldn't let me send a bug report it boots up fine. Should i be worried at all?

I think that is a known issue with alpha 2 (although I am having trouble finding the bug report). Ubiquity crashed at the end of the install for me as well, but my system was installed correctly.

> **ELD said:**
> Also grub isn't listing my windows partition, is there a quick fix for that?

Try running

```
sudo update-grub2
```

which should detect your windows install and add it to grub. Also, look around these forums at the threads on grub 2.

Welcome to Karmic! ):P

---

### Post by ELD on 2009-07-10
I ran the grub update and it doesn't seem to detect my XP install :(
```

]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.30-8-generic
Found initrd image: /boot/initrd.img-2.6.30-8-generic
Warning: update-grub_lib is deprecated, use grub-mkconfig_lib instead
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by Craigy90 on 2009-07-10
Hmm. I think that is a problem with the alpha 2 version of grub 2. You could try running

```
sudo apt-get update
sudo apt-get dist-upgrade
```

but if you don't want to break other things, try running 

```
sudo os-prober
```

and post the output here.

EDIT:

Then run 

```
update-grub2
```

which should add your windows install (if os-prober finds it).

This is the thread on grub 2 that I was referring to:
[http://ubuntuforums.org/showthread.php?t=1186045](http://ubuntuforums.org/showthread.php?t=1186045)

---

### Post by tjeremiah on 2009-07-10
Ubiquity crashed for me too when installing. Is it important to have?

---

### Post by dino99 on 2009-07-10
is it alpha 2 or the daily version

 (better, grub2 have been updated 1 or 2 times since a2)

---

### Post by ELD on 2009-07-10
I did the os probe and got this:
```

mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory

```

I installed the latest grub updates before doing this so i have the latest packages for it.

It is the alpha 2 cd not daily.

---

### Post by dino99 on 2009-07-10
i've installed:

libdebian-installer4  &  libdebian-installer-extra4

---

### Post by Craigy90 on 2009-07-10
> **dino99 said:**
> i've installed:

libdebian-installer4  &  libdebian-installer-extra4

Yeah, what he said. People had this problem here: [http://ubuntuforums.org/showthread.php?t=1182199&page=9](http://ubuntuforums.org/showthread.php?t=1182199&page=9)

The fix was

```

sudo apt-get install --reinstall libdebian-installer4
sudo os-prober
sudo update-grub
```

EDIT: the libdebian-installer-extra4 seems to be unnecessary, sorry. also, this page has a lot of good info: [https://wiki.ubuntu.com/Grub2#Dual-booting](https://wiki.ubuntu.com/Grub2#Dual-booting).

---

### Post by ELD on 2009-07-10
I managed to do it following this i found via google:

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

Works like a charm.

---

### Post by Craigy90 on 2009-07-10
Glad you got it working. I am curious if you can get os-prober to work, because I think that is the automated way to do it.

Also, just curious, is your system completely up-to-date?

---

### Post by ELD on 2009-07-10
I got the os-prober to work after installing the debian file someone said they had ealier.

Not fully up to date, only updated small packages for the moment so i don't break the system lol.

---

### Post by tjeremiah on 2009-07-10
> **ELD said:**
> I got the os-prober to work after installing the debian file someone said they had ealier.

Not fully up to date, only updated small packages for the moment so i don't break the system lol.

updating everything broke my system. I dont know what to ignore to avoid this.I also downloaded the daily updates and errors are all over the place.

---

