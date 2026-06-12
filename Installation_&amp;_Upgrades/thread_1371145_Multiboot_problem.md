---
title: "Multiboot problem"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by crabhunter on 2010-01-03
Hi everyone,
I have just cleaned out my pc and replaced vista with 7, Ubuntu 9.? with 9.10 and Suse 11.1 with 11.2

I used to boot them all by installing each bootloader on their own /root partition and then using easybcd in windows set up neogrub to choose first windows or other os, then Ubuntu or Suse.

I have installed neogrub and edited my old entries best I can but when I choose neogrub at boot up all I get is Grub and a flashing cursor. I did expect to have problems after selecting a linux os but I can't even get my two choices up.
here are my entries


```
default 1
timeout 5

title OpenSuse 11.2
root (hd1,2)  
chainloader +1




title Ubuntu Linux 9.10
root (hd1,1)  
chainloader +1
```

Any help would be appreciated, I have tried the easybcd forum but the person best to help seems to be away.
I will also mention I can successfully add entries to each linux os without neogrub,it is when I try to configure neogrub with both entries I get problems.
Mike

---

