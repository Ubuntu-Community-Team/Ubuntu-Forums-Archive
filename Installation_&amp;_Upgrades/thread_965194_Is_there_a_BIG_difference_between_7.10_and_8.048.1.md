---
title: "Is there a BIG difference between 7.10 and 8.04/8.10 ??,Wont Boot."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by ferty on 2008-10-31
Hi,I have 7.10 running on my system fine,it was a clean install.

I have tried to clean install 8.04 and get a `Busybox` showing the message `initramfs`.

I managed to install 8.04 from update from within 7.10,but on reboot I get the same error message as a clean install.

Now I have tried 8.10 from clean install and its the same result as 8.04.

So is there some big difference from 7.10 to 8.04 and 8.10 which stops the boot.

I have tried booting the clean install of 8.10 with all kinds of boot options but none work,and also the 8.04 update install also would not boot even with lots of options.

Also the same erros when trying to boot from live cd 8.04/8.10.

Any ideas????.

Asrock K7VT4A PRo
1 gb ram
40 gb ide hd ide channel 0  Xp pro on this disc
80 gb ide hd ide channel 0  Ubuntu uses whole disc
4x dvd burner ide channel 1
20x dvd burner ide channel 1
zoom modem
tevion tv card
floppy drive
lan
hp f2290 all-in-one
lekmark x1160
56k hardware serial modem

---

### Post by ferty on 2008-11-01
Bump

---

### Post by ferty on 2008-11-01
Also I don`t know if it makes a difference I am using an old Gefore MX440 agp card.

---

### Post by gjoellee on 2008-11-01
There are many changes between the Ubuntu distros, but most of them you don't notice. However I thing you should try using another distro that is similar to Ubuntu and see what errors you may get.

 I would recommend trying Linux Mint which more or less Ubuntu with theme changes, a few other changes and flash and codecs and java etc... installed by default.

---

### Post by hyperdude111 on 2008-11-01
Your graphics card is not the problem, I too have the Geforce MX 440 and have had no booting problems with 8.04 or 8.10

---

### Post by ferty on 2008-11-02
Well after seeing in another thread that it may be down to ide drive order,I thought I`d check mine and low and behold I was trying to install to the slave ide drive.
So a quick change around and pop in the 8.10 disc and....
Exactly the same as before!,but I then had a thought,I have two DVD drives and I have been trying to boot/install from the slave  DVD,as I did with 7.10,So pop in the disc to the Master IDE DVd,and I have just finished the install,now time to boot and check,but so far so good.

---

### Post by ferty on 2008-11-03
Well thats fixed it!.
So if any one else if have a similar problem check that your booting from a master drive.
Thank all.

---

