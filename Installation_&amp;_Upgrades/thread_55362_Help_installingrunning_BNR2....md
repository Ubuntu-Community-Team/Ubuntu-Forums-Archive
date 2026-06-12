---
title: "Help installing/running BNR2..."
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by [Cyanide] on 2005-08-08
I've followed the instructions on BNR2's (Binary News Reaper) website, using both the tar method & the BNR2-install script method, and when I try to run BNR2 it gives me this error message:

```
cyanide@Cyanide-Laptop:~/Desktop/Internet Downloads$ sudo /usr/local/BNR2/bin/BN R2
libborqt-6.9-qt2.3.so: cannot open shared object file: No such file or directory
```

And this is the output I get when I installed libborqt:

```
cyanide@Cyanide-Laptop:~/Desktop/Internet Downloads$ sudo ./BNR2-install libborq t-6.9.0-qt2.3.so.tgz
libborqt string.
BNR2/
BNR2/lib/
BNR2/lib/libborqt-6.9.0-qt2.3.so
BNR2/lib/libborqt-6.9-qt2.3.so
```

Help anyone?

---

### Post by [Cyanide] on 2005-08-10
[QUOTE='[Cyanide]']I've followed the instructions on BNR2's (Binary News Reaper) website, using both the tar method & the BNR2-install script method, and when I try to run BNR2 it gives me this error message:

```
cyanide@Cyanide-Laptop:~/Desktop/Internet Downloads$ sudo /usr/local/BNR2/bin/BN R2
libborqt-6.9-qt2.3.so: cannot open shared object file: No such file or directory
```

And this is the output I get when I installed libborqt:

```
cyanide@Cyanide-Laptop:~/Desktop/Internet Downloads$ sudo ./BNR2-install libborq t-6.9.0-qt2.3.so.tgz
libborqt string.
BNR2/
BNR2/lib/
BNR2/lib/libborqt-6.9.0-qt2.3.so
BNR2/lib/libborqt-6.9-qt2.3.so
```

Help anyone?[/QUOTE]
 Anyone?

---

### Post by SinZero on 2006-02-03
I had the same problem to start with but it seemed to work if I use /usr/local/BNR2/bin/bnr2 (note the lowercase bnr2 at the end)

---

