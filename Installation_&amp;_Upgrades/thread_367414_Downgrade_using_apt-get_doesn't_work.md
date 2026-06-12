---
title: "Downgrade using apt-get doesn't work"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by adaniels on 2007-02-22
Hi,

I'm not able to downgrade packages with apt-get. I get an error saying that the version was not found, though even if the version is no longer available in the ubuntu repository, it's still cached.

Can anyone tell me what might be wrong?

```

arnold@arnold-laptop:~$ ls /var/cache/apt/archives/php5_*
/var/cache/apt/archives/php5_5.1.6-1ubuntu2.1_all.deb  
/var/cache/apt/archives/php5_5.1.6-1ubuntu2.2_all.deb

arnold@arnold-laptop:~$ sudo apt-get install php5=5.1.6-1ubuntu2.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '5.1.6-1ubuntu2.1' for 'php5' was not found

arnold@arnold-laptop:~$ sudo apt-get install php5=5.1.6-1ubuntu2.1 --no-download --ignore-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '5.1.6-1ubuntu2.1' for 'php5' was not found

```

Thanks,
Arnold

---

