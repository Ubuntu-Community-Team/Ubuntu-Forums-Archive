---
title: "Problems with grub2"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by peverix on 2010-01-15
Hello

I'm using ubuntu 10.4 on a embedded system ( i need to use already 10.4 because with 9.10 i have the blank screen problem ). Everything working fine except a booting problem with grub2.

Because this system is embedded , the user doesn't do a usual shutdown but just put off the power supply.
After powering up again , its startup normal with detecting a bad shutdown and do a disk check. After fixing bad disk it reboots again.

And now it is waiting in the grub menu until you select a menu point with a keyboard.

I never noticed this with legacy grub , how to change this ?

Peter Everix

---

### Post by kansasnoob on 2010-01-15
It sounds like you have more technical knowledge than I do so maybe you can make use of this HowTo I wrote:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by peverix on 2010-01-15
Thanks for this clear how-to

I followed it and now i'm back to the old grub.
Everything working as expected again.

Regards
Peter

---

### Post by meierfra. on 2010-01-16
Just for anybody reading this. The  problem of the OP can  be solved very easily without reverting to Legacy Grub:

Open the file  00_header via

```
gksudo gedit /etc/grub.d/00_header 
```

Look for 

```
if [ \${recordfail} = 1 ]; then
   set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi

```

Change it to


```
[COLOR="Red"]#[/COLOR]if [ \${recordfail} = 1 ]; then
[COLOR="Red"]# [/COLOR] set timeout=-1
[COLOR="Red"]#[/COLOR]else
  set timeout=${GRUB_TIMEOUT}
[COLOR="Red"]#[/COLOR]fi

```

Save the file and run 

```
sudo update-grub

```

Now Grub2 will always use the default timeout

---

