---
title: "Edimax EW-7811Un Ubuntu 13.04"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by fredcarru on 2013-08-20
After upgrading to Ubuntu 13.04 the Edimax EW-7811Un doesn't want to connect.

There are 3 options, BTHub4-HGF6; BTWifi; BTWifi-with-FON. I don't seem to be able to prevent the hub offering these. When I uncheck the "use when available" options in the 2 wifi options it tries to connect to BTHub4-HGF6 but fails, the transmit symbol changes from the transmit symbol to a boxed symbol.

With 12.10 I had to install a separate driver (module?), as it wasn't recognised during installation, when installing 13.04 Ubuntu recognised the dongle automatically. The return from lsusb reports a different chip-set than that used in 120.10. Unfortunately because of the problem I can't report this from Ubuntu and have resorted to  windows. Therefore I can't give the precise chip-sets.

It's working under Ubuntu now the chip-set used in 12.10 was RTL8192CU and in 13.04

fred@fred-desktop:~$ lsusb
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

---

### Post by Herber on 2013-10-23
I am having a similar problem with the Edimax 7811Un, in Ubuntu 13.10.  The device recognizes the network but doesn't seem to be able to establish a connection.  I believe this is a driver issue (and that the Ubuntu driver is out of date) but I don't know how to put in-place the correct driver.

---

### Post by mikewhatever on 2013-10-24
> **Herber said:**
> I am having a similar problem with the Edimax 7811Un, in Ubuntu 13.10.  The device recognizes the network but doesn't seem to be able to establish a connection.  I believe this is a driver issue (and that the Ubuntu driver is out of date) but I don't know how to put in-place the correct driver.

Ubuntu doesn't make drivers for Reaktek chipsets, Realtek does.
What "correct driver" are you talking about? Where did you get it from?

---

### Post by NM5TF on 2013-10-25
had the same problem...the thread below fixed it...go here:

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs)

Tommy

---

### Post by mikewhatever on 2013-10-25
> **NM5TF said:**
> had the same problem...the thread below fixed it...go here:

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs)

Tommy

That doesn't work for 13.04 and later, because the driver is for Linux 3.0.8, which is too old.

It just fails when building the module.

---

### Post by NM5TF on 2013-10-27
> **mikewhatever said:**
> That doesn't work for 13.04 and later, because the driver is for Linux 3.0.8, which is too old.

It just fails when building the module.

works just fine running 3.5.0-42 Linux Mint 14 which is based on Ubuntu 13.04 or 13.10
I believe...I just ran it today after upgrading to new kernel that killed my wifi...ran the
install.sh & now wifi working perfectly...

YMMV

Tommy

---

### Post by mikewhatever on 2013-10-30
> **NM5TF said:**
> works just fine running 3.5.0-42 Linux Mint 14 which is based on Ubuntu 13.04 or 13.10
I believe...I just ran it today after upgrading to new kernel that killed my wifi...ran the
install.sh & now wifi working perfectly...

YMMV

Tommy

Well, first, I am happy it works for you. Second, building the driver from Realtek worked till 12.10 with kernel 3.5, but, reportedly, fails with 13.04 and later. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=2148130") for more info.

Ubuntu 13.04 has 3.8 and 13.10 has 3.11.

---

### Post by NM5TF on 2013-11-02
> **mikewhatever said:**
> Well, first, I am happy it works for you. Second, building the driver from Realtek worked till 12.10 with kernel 3.5, but, reportedly, fails with 13.04 and later. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=2148130") for more info.

Ubuntu 13.04 has 3.8 and 13.10 has 3.11.

you are correct....Mint 14 is based on 12.10 and not 13.04 as I thought...that is why
it worked for me....my bad:oops:

and yes, it didn't work for Ubu 14.04 which is based on 13.10..:(

sorry for the confusion

---

### Post by NM5TF on 2013-11-02
> **mikewhatever said:**
>  Check out [this thread]("http://ubuntuforums.org/showthread.php?t=2148130") for more info.

thanks for the link....that fixed my install of Ubu 14.04 wifi problem for kernel 3.11....
but the upgrade to the 3.12 kernel is broken again....is there a similar fix for 3.12 ??

---

