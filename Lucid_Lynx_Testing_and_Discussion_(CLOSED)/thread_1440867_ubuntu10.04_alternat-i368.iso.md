---
title: "ubuntu10.04 alternat-i368.iso"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 1991sudarshan on 2010-03-28
i downloaded the beta version of ubuntu 10.04 alternatei386!!
my question is can i use this alternate386 to install ubuntu in my laptop? or else do i have to download the desktop version??

---

### Post by ikt on 2010-03-28
> **1991sudarshan said:**
> i downloaded the beta version of ubuntu 10.04 alternatei386!!
my question is can i use this alternate386 to install ubuntu in my laptop? or else do i have to download the desktop version??

The Desktop CD boots to a live version of ubuntu so you can try it out without touching your hard drive. If you like it you can then run the installer from it.

The alternate installer is just a text based version of the installer, which gives you a little more control over the installation, but you don't get to test it live.

Yes you can use this alternate 386 to install ubuntu on your laptop.

---

### Post by 1991sudarshan on 2010-03-28
but i found that there is now wubi along withit!! i want to install it inside the windows!!!!!!!!!!!!

---

### Post by stlsaint on 2010-03-28
Than boot into windows and go explore the cd to find the wubi.exe to do a wubi installation from a livecd.

---

### Post by 1991sudarshan on 2010-03-28
there is no wubi.exe file in it!!!! then how to install inside the windows???

---

### Post by ankspo71 on 2010-03-28
Hi,
You can get wubi.exe from here 
[http://wubi-installer.org/](http://wubi-installer.org/)
I never tried this though.

---

### Post by 1991sudarshan on 2010-03-28
ya i tried it already!! that wubi is installing the ubuntu 9.10 but not the iso file which i have burnt it in the cd!!!!:-K

---

### Post by Paqman on 2010-03-28
> **1991sudarshan said:**
> ya i tried it already!! that wubi is installing the ubuntu 9.10 but not the iso file which i have burnt it in the cd!!!!:-K

Make sure the ISO is in the same folder you're launching Wubi from. If that still doesn't work, try a regular desktop image instead of the alternate one.

---

### Post by 1991sudarshan on 2010-03-28
ya i will let you know and thanks

---

### Post by ikt on 2010-03-28
> **1991sudarshan said:**
> ya i will let you know and thanks

wubi doesn't currently work properly with 10.04.

[http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)

> Wubi as included on the ISO images is unable to enter its second stage of installation, so you will not be able to install inside Windows using just an ISO image in this beta release. As a workaround, users who are installing the Ubuntu Desktop Edition can download the stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe) which includes the fix for this bug. This bug will be fully addressed for 10.04 LTS Beta 2. (541607)

---

### Post by 1991sudarshan on 2010-03-28
so i wont be able to install inside the windows???

---

### Post by ikt on 2010-03-28
> **1991sudarshan said:**
> so i wont be able to install inside the windows???

Probably not, I would just install 9.10 desktop, as 10.04 is still in testing.

---

### Post by 3rdalbum on 2010-03-28
You've been with us since last year, so I'm assuming you have used Ubuntu in the past. Install Ubuntu as a real dual-boot, there are fewer problems with it.

Wubi is just a Windows-based Ubuntu installer, that installs Ubuntu within a file. Ubuntu still runs directly on the hardware; it's not virtualisation. But the "run Ubuntu within a file" method does mean that if Windows won't boot up, then Ubuntu won't either.

---

### Post by 3rdalbum on 2010-03-28
> **ikt said:**
> Probably not, I would just install 9.10 desktop, as 10.04 is still in testing.

There's not much point to testing, if the only people who test are developers. I've submitted some bug reports (not many, Ubuntu 10.04 is very solid) and I encourage everyone to do the same.

Remember, Ubuntu 9.10 was considered to be "not adequately tested"... you don't want a repeat of 9.10 do you?

---

### Post by 1991sudarshan on 2010-03-28
so you guys are asking me not to proceed with the beta version?
but i had enough of ubuntu9.10!! i am eagerly waiting for the lts version and the new features!!!!!!!!!!!!

---

### Post by 3rdalbum on 2010-03-28
> **1991sudarshan said:**
> so you guys are asking me not to proceed with the beta version?
but i had enough of ubuntu9.10!! i am eagerly waiting for the lts version and the new features!!!!!!!!!!!!

Proceed with the beta version of Ubuntu 10.04; just don't use Wubi. Install Ubuntu by booting up the alternate CD (or the Desktop CD if you have it) and overwrite the Ubuntu 9.10 partition.

---

### Post by ikt on 2010-03-28
> **3rdalbum said:**
> Proceed with the beta version of Ubuntu 10.04; just don't use Wubi. Install Ubuntu by booting up the alternate CD (or the Desktop CD if you have it) and overwrite the Ubuntu 9.10 partition.

^ This.

> **3rdalbum said:**
> There's not much point to testing, if the only people who test are developers. I've submitted some bug reports (not many, Ubuntu 10.04 is very solid) and I encourage everyone to do the same.

Remember, Ubuntu 9.10 was considered to be "not adequately tested"... you don't want a repeat of 9.10 do you?

It entirely depends on who is doing the testing, do I want only developers doing the testing? no, do I want people who are actually interested in testing to be testing? yes.

---

### Post by 1991sudarshan on 2010-03-28
when i tried to install the lucid lynx beta it asked for the host name!! what shall i give for the host name????

---

