---
title: "Netboot beta 1?"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Psumi on 2010-03-21
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/)

Since it says March 11th, does this mean it's not Beta 1?

---

### Post by jppr on 2010-03-21
when you update system it is beta 1!! Beta 1 is snapshot on the system 19.3!!
[http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/)

---

### Post by Psumi on 2010-03-21
> **jppr said:**
> when you update system it is beta 1!! Beta 1 is snapshot on the system 19.3!!
[http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/)

netbook =/= netboot

Anyway, thanks I guess.

---

### Post by seeker5528 on 2010-03-22
> **Psumi said:**
> [http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/)

Since it says March 11th, does this mean it's not Beta 1?

There may not have been any changes in the installer since then given the small window between then and the beta 1 release.

What you end up with when you install from the netboot will be different than what you get when you install from the beta 1 CD/DVD because it is only including a minimum amount of stuff to boot, run the installer, and access the internet. Everything that is installed will be the current stuff in the repositories, so everything should be at or newer than what was in beta 1. 

I have not tried to do the stuff to get a PXE server working to provide the boot environment to the machine you want to install to, but there are some instructions:

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

: if you need them

Later, Seeker

---

