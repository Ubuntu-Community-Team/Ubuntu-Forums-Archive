---
title: "infiniband ulp srp Makefile no such file or directory - make clean fails"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2008-04-02
Hi,
on a 2.6.15-51 kernel I tried to build the nvidia module ( NVIDIA-Linux-x86-169.12-pkg1) but that fails because scripts/genkeysyms/genkeysyms isn't built.

So I thought building the entire kernel, downloaded

apt-get install linux-headers-2-6-15-51 

```
cd /usr/src
ln -s  linux-headers-2-6-15-51 linux
cd linux
cp /boot/config-2.6.15-51-686 .config
make clean
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.15-51-386/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.15-51-386/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/ulp/srp] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2
```

I already searched the web for occurences of this error but couldn't find a solution.

---

