---
title: "Can't install Qualcomm Atheros QCA9565/ AR9565 drivers in Kubuntu"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by yamil2 on 2015-09-25
I just installed Kubuntu 14.04 and I can't access to internet wireless, so I searcher (with an ethernet cable) and it was drivers issues, so I searched for them and I found a solution for someone that had the same issue, the post is here:

[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)

But I'm having an error in one of the steps but I don't know what is happening. Here is what I'm doing:

First of all I'm getting the prerequisites to compile:

```
sudo apt-get install linux-headers-generic build-essential
```

Then I'm following the steps that are in that post:

```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2
tar xvf compat*
cd compat-wireless-3.6.6-1-snpc
sudo su
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit

```

When I'm at *./scripts/driver-select ath9k *this is the result in the Terminal:
```
[Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: drivers/net/wireless/ath/Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/bcma/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk

```

I don't know if it has something to do with this, but when I continue with *make* I'm having the error:

```

make -C /lib/modules/3.19.0-25-generic/build M=/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-25-generic'
  CC [M]  /home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/debug.o
/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/debug.c: In function ‘write_file_tx_chainmask’:
/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/debug.c:117:2: error: implicit declaration of function ‘strict_strtoul’ [-Werror=implicit-function-declaration]
  if (strict_strtoul(buf, 0, &mask))
  ^
cc1: some warnings being treated as errors
make[5]: *** [/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/debug.o] Error 1
make[4]: *** [/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k] Error 2
make[3]: *** [/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath] Error 2
make[2]: *** [/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/atgdev/Desktop/compat-drivers-3.9-rc4-2-s] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-25-generic'
make: *** [modules] Error 2


```

So I just can't continue with the other steps, anyone knows what is happening? I could use a lot your help guys.
My Computer is a Lenovo G50-30 with 4 GB Ram, 1 TB HDD and an  **Intel Celeron** N2830 processor.

Thanks for reading :)

---

### Post by mara6 on 2015-10-15
I have the exact same problem, is there really no one who can help out? :)

---

