---
title: "GNOME terminal doesn't differents upper/lower cases ?"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2007-06-29
```

me@host:~$ mv Util.m util.m
mv: `Util.m' and `util.m' are the same file


```

So, it seems GNOME terminal does not differentiate upper and lower cases in the file names, is it?

I need to work on various platforms like Solaris, Ubuntu Linux, Windows XP, Windows XP. In order to keep the best compatibility, should I always name my files using only lower cases ? What is the best practice here ?

Thanks. 

//bow

---

### Post by srt4play on 2007-06-29
I just did

```
> Test.txt
mv Test.txt test.txt
```

and it worked as expected.  Not sure what could cause your problem.

---

### Post by Physicist on 2007-06-29
Yes, I can too, if I am doing it in a "normal" path:
```

usr@host:~$ touch test
usr@host:~$ mv test Test

```

But I cannot do it here:

```

usr@host:/media/sdb7$ mv test Test
mv: `test' and `Test' are the same file

```

Then I found sdb7 is a little bit different:
```

usr@host:/media$ ls -la
drwxrwxrwx  1 root root    12288 2007-06-29 09:34 sda1
drwxrwxrwx  1 root root     4096 2007-06-27 10:51 sda5
drwxrwx---  3 root plugdev 16384 1969-12-31 19:00 sdb1
drwxrwx---  4 root plugdev  4096 1969-12-31 19:00 sdb10
drwxrwxrwx  1 root root     4096 2007-06-27 10:51 sdb2
drwxrwx--- 11 root plugdev  4096 1969-12-31 19:00 sdb3
drwxrwxrwx  1 root root     8192 2007-06-27 10:51 sdb5
drwxrwxrwx  1 root root     8192 2007-06-27 10:51 sdb6
drwxrwx--- 14 root plugdev  4096 2007-06-29 16:57 sdb7
drwxrwxrwx  1 root root    57344 2007-06-27 10:51 sdb8
drwxrwx---  6 root plugdev  4096 1969-12-31 19:00 sdb9

```

But I cannot change the ownership:
```

usr@host:/media$ sudo chown root:root sdb7
chown: changing ownership of `sdb7': Operation not permitted
usr@host:/media$ 

```

So, what's wrong?

---

### Post by Physicist on 2007-07-02
So does this problem have to do with the ownership of the file ? What is plugdev after all ?

---

