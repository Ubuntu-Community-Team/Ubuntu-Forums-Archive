---
title: "swap &quot;file&quot; vs. &quot;partition&quot;"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2010-07-18
I have loads of RAM so I tried to install without a swap "partition". SLEEP and HIBERNATE would not work -- I guess that they use swap to store system state details. I created a swap "file". Nothing changed -- I guess because the "file" was not available early enough in the boot-wake processing.

If I must have a swap "partition" why don't I get a warning from the installer?

If SLEEP and HIBERNATE require a swap "partition", why don't I get a warning from either "... Can't proceed. Swap partition missing..." or similar rather than spin down to a garbage state?

How do I launch SLEEP and HIBERNATE from the command line or otherwise configure so that I can watch the spin-down processing and discover the troubles that I need to fix?

~~~ 0;-Dan

---

### Post by Rubi1200 on 2010-07-18
Not sure if this will answer all your questions, but it might be useful:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by maestrobwh1 on 2010-07-18
Also post 5 of this might help:

[http://newyork.ubuntuforums.org/showthread.php?t=857565](http://newyork.ubuntuforums.org/showthread.php?t=857565)

Your swap UUID in fstab must match in the listed file SO I am thinking hibernate will not work easily from swap file because I think booting asks for ubuntu to look in a listed partition for hibernation evidence.

---

### Post by SaintDanBert on 2010-07-19
> **maestrobwh1 said:**
> 
...
I think booting asks for ubuntu to look in a listed partition for hibernation evidence.

Since I have /boot on a partition, does this mean I need to put a swap file on /boot so it is visible during wake-processing?

Are there boot-time options that tell the system where to look for suspend evidence?

Can I configure the suspend commands, that tell it where to write its state details -- so that they are found during wake processing?

~~~ );-Dan

---

### Post by pbrane on 2010-07-19
You shouldn't need a swap file/partition to suspend. But Ubuntu may implement that differently. But you will need one to hibernate, minimum size would be equal to RAM. 

If you read the Swap FAQ it tells you how to setup a swap file. I think it can be anywhere you have enough disk space. You have to get it mounted to use it.

---

### Post by Nplotnick on 2010-07-30
Does the SWAP partition require formatting? On my newly setup 10.04 system, the disk utility shows the following information:

device /dev/sda5
partition type Linux Swap (0x82)

The partition does not appear to be mounted or formatted.

Thanks for the guidance.

Neil

---

### Post by SaintDanBert on 2010-08-02
You must have an entry in **/etc/fstab** for your swap partition.

Mine looks like this:
```

# swap was on /dev/sda11 during installation
#..... actual UUID obfucated ...
UUID=017 ... e86b      none     swap    sw     0     0


```

There is a different dance if you use a swap "file".  Take a look at **mkswap** command for details.

~~~ 0;-Dan

---

