---
title: "DWA-552 Works!!! Finally"
date: 2009-05-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-05-18
My wireless finally works 

```

*-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@
       logical name: wmaster0
       version: 01
       serial: 
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip= latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```Now please, don't change a thing with it.

---

### Post by Progressive on 2009-05-19
I was literally looking at one of these cards today, but decided against it because of flaky linux support.

---

### Post by tad1073 on 2009-05-19
I had it working with 8.10 64 bit but, I can't remember how I got it to work.

The updates for 8.10 started causing connection problems though.

I tried 9.04 but couldn't get it to work and no suggestions on how to get to work.

So, I figured, might as well try 9.10 alpha 1 and it connected with no problems.

---

### Post by cl333r on 2009-05-19
> Now please, don't change a thing with it.
Pretty funny :)

---

### Post by tad1073 on 2009-05-19
Thanks cl333r. 

The card works out of the box and I don't drop signal strength like it did in 8.10, but the are some issues that I am having, such as, pages time-out alot, rate is only 1Mb/s etc.

I was messing around with the rates and page time-out constant, but I am still connected.

---

