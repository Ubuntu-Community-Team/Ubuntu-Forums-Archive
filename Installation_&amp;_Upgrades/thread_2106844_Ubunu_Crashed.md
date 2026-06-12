---
title: "Ubunu Crashed"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by Ibrahim mufeed on 2013-01-20
Hi,

Last night I was trying to install a software and it gives error about conflicting packages. I read on some forum to make:

```
sudo apt-get -f install
```

Once I issued this command it asked me (Yes, do as I want!). And I typed it and it started removing too many packages including some basic packages! I stopped the command before finishing by closing the terminal.

The system is crashed now, I can not access my Ubuntu. When I select it in boot menu I only see the pink window with the word Ubuntu and the dots under it.

Any idea how to fix it?

Regards,

---

### Post by grahammechanical on 2013-01-20
That command is the correct one to use to fix broken packages or if a package has unmet dependences. The command may have been removing basic packages that relied upon libraries that would have been in conflict with the libraries used by the new software. The mistake was to stop it while it was working.

Can you access the Grub menu? You can try selecting an older kernel and see if that get you to a desktop. Other than that I suggest a bit more complicated method.

1) Select Recovery method.
2) At the Recovery menu select Failsafe.
3) Press Esc to back out of Failsafe.
4) Select Root. That will bring you to a root shell prompt.

Selecting Root will get you to a root prompt but the file system will be in write only mode. By going into failsafe the file system gets put into read/write mode. which is what you need to make changes (update) the file system. This is why I suggest go into failsafe first.

At the root shell prompt run these commands one after the other and re-boot and see what happens.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Regards.

---

### Post by Ibrahim mufeed on 2013-01-20
Thanks for your reply. I found out that I can not access the shell. When I select recovery mode, it start printing some stuff on the screen and the it stops and I can not do anything.

How can I access a shell. I tried ctl+alt+F1 does not work either.

---

### Post by Bucky Ball on 2013-01-20
> **Ibrahim mufeed said:**
>  I tried ctl+alt+F1 does not work either.

... is required from a desktop. Won't get you far in this situation ...

Try hitting F5 up. You need 'Alt' with that anyhow, from memory.

---

### Post by Ibrahim mufeed on 2013-01-20
Guys, I tried eveything.. still can not access the shell!!! I tried everything, but nothing is working.

---

### Post by Bucky Ball on 2013-01-20
Maybe try booting from the LiveCD, or whatever you installed with. That should give you full access. You will find a terminal there and we can dig deeper ...

---

### Post by Ibrahim mufeed on 2013-01-20
> **Bucky Ball said:**
> Maybe try booting from the LiveCD, or whatever you installed with. That should give you full access. You will find a terminal there and we can dig deeper ...

I booted using sub. now i am using ubuntu from usb and can access the hard drive but i don't know what to do fix my system. Any suggestion?

---

### Post by Ibrahim mufeed on 2013-01-20
How can I change root chroot into the installed system?

---

### Post by Ibrahim mufeed on 2013-01-20
I am following the steps in this blog:
> [http://www.tuxgarage.com/2011/07/creating-chroot-ubuntu.html](http://www.tuxgarage.com/2011/07/creating-chroot-ubuntu.html)
but when I issue:
> sudo chroot /mnt/temp
I got:
> chroot: failed to run command `/bin/bash': No such file or directory

Any idea?

---

### Post by Ibrahim mufeed on 2013-01-20
I made the chroot command by after this command:
> cp -r /bin /lib /mnt/temp
and it worked.
Now when I do anything with apt-get, I get:
> apt-get: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/lib/x86_64-linux-gnu/libstdc++.so.6)


Ideas?!

---

### Post by tgalati4 on 2013-01-20
What was the package that you were trying to install?

```
apt-cache depends packagethatyouaretryingtoinstall
```

We need to know what dependencies were being replaced during the installion process.

We need to know what parts of your system are intact and what parts got destroyed.

---

### Post by Ibrahim mufeed on 2013-01-21
The thing is that all the system is crashed GLIBC is a very basic package used by all the tools in Ubuntu. apt-get itself is not working.

---

### Post by tgalati4 on 2013-01-21
You are correct.  Glibc is used everywhere!  Sounds like your system is messed up.  As a general rule, don't abort an installation.  Let it run its course.  Sometimes many packages get replaced during an installation.  It looks scary, but that is how linux works.

Boot a Live CD/DVD or USB and mount the drive and back up any important data to a flash drive.  Then reinstall.  I don't think you will be able to recover from this damaged state.  Even if you do recover, how long would you trust the system?

---

### Post by Ibrahim mufeed on 2013-01-22
Yes tgalati4, This what I started doing last night.

Thank you guys.

---

### Post by Bucky Ball on 2013-01-22
... where are you up to? If this particular problem is solved, or at least *re*solved to your satisfaction, could you please mark it that way from Thread Tools to help others and start a new thread for any further issues. Cheers. ;)

---

### Post by Ibrahim mufeed on 2013-01-22
Yeah I know I should, but I was waiting until I'm done with the new installation and then I will consider the issue done :) .

---

