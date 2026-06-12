---
title: "libc.so Segmentation fault"
date: 2009-12-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-12-19
During boot I get warning about some error, as much as I managed to rember it states that there is a segmentation fault (libc.so). I have:```
~$ locate libc.so
/lib/libc.so.6
/usr/lib/libc.so
~$ ls -al /lib/libc.so*
lrwxrwxrwx 1 root root 14 2009-12-14 21:16 /lib/libc.so.6 -> libc-2.10.2.so
~$ ls -al /usr/lib/libc.so
-rw-r--r-- 1 root root 247 2009-12-14 19:33 /usr/lib/libc.so
~$ ls -al /lib/libc-2.10.2.so
-rwxr-xr-x 1 root root 1494440 2009-12-14 19:39 /lib/libc-2.10.2.so
~$ dmesg|grep libc
[    2.054585] wait-for-root[278]: segfault at 0 ip 00007f0c73a307c2 sp 00007fff87cfe5b8 error 4 in libc.so.6[7f0c739b1000+166000]

```

---

### Post by arrange on 2009-12-19
I had the same problem, but after I rebooted, it went back to normal.

---

### Post by zika on 2009-12-19
> **arrange said:**
> I had the same problem, but after I rebooted, it went back to normal.That happened when I boot-ed with 2.6.33-999. With 2.6.32-9.13 there is no segmentation fault. I'll investigate 2.6.33 further.
Update: Yes, it happens with 2.6.33-999 only.

---

### Post by Eddie Hung on 2009-12-20
I'm seeing libc segfaults on the default lucid kernel -- 2.6.32.9 on AMD64:

```

dmesg | grep libc
[15429.604544] Xorg[2865]: segfault at 0 ip 00007f13a880de1b sp 00007fff9aef3568 error 4 in libc-2.10.2.so[7f13a87c9000+166000]
[15462.353159] gdm-simple-slav[2884] general protection ip:7f05e4bcda97 sp:7fff98ad5240 error:0 in libc-2.10.2.so[7f05e4b85000+166000]
[15521.192701] gdm-simple-slav[3006] general protection ip:7f04e38d5a97 sp:7fff82c6c4a0 error:0 in libc-2.10.2.so[7f04e388d000+166000]
[15710.321408] gdm-simple-slav[3219] general protection ip:7fe1f1edda97 sp:7fffbf0a9170 error:0 in libc-2.10.2.so[7fe1f1e95000+166000]

```

Whenever I try to switch user or run gdmflexiserver.

Can anyone else confirm?
There also doesn't seem to be a sign of a launchpad report for this yet...

Eddie

---

### Post by zika on 2009-12-20
> **Eddie Hung said:**
> I'm seeing libc segfaults on the default lucid kernel -- 2.6.32.9 on AMD64:

```

dmesg | grep libc
[15429.604544] Xorg[2865]: segfault at 0 ip 00007f13a880de1b sp 00007fff9aef3568 error 4 in libc-2.10.2.so[7f13a87c9000+166000]
[15462.353159] gdm-simple-slav[2884] general protection ip:7f05e4bcda97 sp:7fff98ad5240 error:0 in libc-2.10.2.so[7f05e4b85000+166000]
[15521.192701] gdm-simple-slav[3006] general protection ip:7f04e38d5a97 sp:7fff82c6c4a0 error:0 in libc-2.10.2.so[7f04e388d000+166000]
[15710.321408] gdm-simple-slav[3219] general protection ip:7fe1f1edda97 sp:7fffbf0a9170 error:0 in libc-2.10.2.so[7fe1f1e95000+166000]

```

Whenever I try to switch user or run gdmflexiserver.

Can anyone else confirm?
There also doesn't seem to be a sign of a launchpad report for this yet...

EddieNo, I do not have that. Only:```
[    2.057845] wait-for-root[271]: segfault at 0 ip 00007f80f10da7c2 sp 00007fff87fd7958 error 4 in libc.so.6[7f80f105b000+166000]
```
with```
~$ uname -a
Linux zika 2.6.33-999-generic #200912181148 SMP Fri Dec 18 11:53:32 UTC 2009 x86_64 GNU/Linux
```I think it happens also with 2.6.32-99{6,9} ... but I'll have to recheck, when I reboot.

---

### Post by zika on 2009-12-22
I've found the rule. I get segfault only if I use KMS, no matter what kernel.

---

### Post by xebian on 2009-12-22
I get segfaults frequently also for the last few days.  Mostly when chrome chrashes.

---

### Post by autark on 2009-12-22
I have reported a bug on this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499422](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499422)

---

### Post by zika on 2009-12-22
> **autark said:**
> I have reported a bug on this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499422](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499422)Thank You, I've signed it.

---

