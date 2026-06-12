---
title: "Unable to recover grub, after installing windows 7 AGAIN,  help needed ASAP."
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by Ali_Jafri on 2014-08-02
I am kind of new to ubuntu environment. 

Background of problem :
I was having dual boot of windows 7 and ubuntu 13.10 before,  but i need to install Windows 7 again due to some problem. 

Problem :
After installing Windows 7 i lost my dual boot

I tried Boot-Repair-disk but it didnt solve the error

The url which i got was. 
[http://paste.ubuntu.com/7933407/](http://paste.ubuntu.com/7933407/)


May be of any help:
The advance option in boot-repair was showing "GRUB location"  and "GRUB options"  as DISABLED..
[IMG]http://i61.tinypic.com/2mycikk.jpg[/IMG]

---

### Post by Mark Phelps on 2014-08-02
From the info you provided, it looks like you had installed using Wubi -- which installs Ubuntu INSIDE a Windows filesystem partition.  When you reinstalled Windows, you basically wiped out the Wubi installation -- or at least, it looks like that.  Strongly recommend against using Wubi, as it has been discontinued and is no longer supported.

---

### Post by Ali_Jafri on 2014-08-02
You mean to say that theres no way i can get the grub back ?

---

### Post by oldfred on 2014-08-02
It looks like you still have wubi in sda4.
 /ubuntu/disks/root.disk
One of the main reasons for wubi was to avoid adding partitions.

You then may be able to manually add boot entry in your new Windows BCD.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by Mark Phelps on 2014-08-02
> **Ali_Jafri said:**
> You mean to say that theres no way i can get the grub back ?

Wubi doesn't use GRUB; instead, it uses something known as GRUB4DOS -- a special version of GRUB that installs and runs inside Windows.

If you install, or force the install of, you're own GRUB, that will only make matters worse.

What MIGHT work is the following:
1) Copy the root.disk file off to a safe place
2) Reinstall Wubi to the same location you had it before
3) Copy the saved root.disk file over the existing file

Since Wubi is not maintained anymore, the best thing you can do is move away from using it.

---

