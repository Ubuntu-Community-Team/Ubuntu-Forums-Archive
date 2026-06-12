---
title: "DWA-140 Wireless USB Adapter"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-02-26
I always run from the cable because the wireless stuff just never works on my desktop. Funnily enough, the only time wireless doesn't give me hassle is with notebooks.

Anyway, I have the DWA-140 USB adapter (which i bought as it was on the compatibility list). It doesn't work (AGAIN) in Lucid now.

After a lot of wasted time with Karmic i stumbled across someone who got it working installing the backports modules. Well i've done this for Lucid and it's still not getting the adapter to work.

DMESG brings up nothing that's obviously useful to me

[  142.650078] #
[  147.647101] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 969
[  147.647336] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  148.270083] #
[  149.270073] #
[  149.330103] #
[  150.270062] #
[  150.350101] #
[  151.270054] #
[  151.300067] #

Anyone got any ideas?

---

### Post by labinnsw on 2010-02-27
> **sonicb00m said:**
> After a lot of wasted time with Karmic i stumbled across someone who got it working installing the backports modules. Well i've done this for Lucid and it's still not getting the adapter to work.

Was this an article/post on the web? Could you post the link or instructions you followed.

---

### Post by sonicb00m on 2010-02-27
[http://ilostmynotes.blogspot.com/2009/12/wireless-problems-on-karmic-no-probe.html](http://ilostmynotes.blogspot.com/2009/12/wireless-problems-on-karmic-no-probe.html)

After scouring the DWA-140 fixes this was the only thing that got it running in Karmic (albeit in 54g mode only, despite having n capabilities).

---

### Post by labinnsw on 2010-02-28
I made a small partition and installed Lucid in an attempt to replicate your problem. My adapter is DWA-110 which I don't think would be that different from your DWA-140. Once configured and plugged in, it just worked. I am using it now. Did you set up yours using ndiswrapper?

---

### Post by sonicb00m on 2010-02-28
No NDIS wrapper never works for it. I've had this problem on all the computers i've tried. 

The only way i finally got it working on Karmic was to install backports. But that's not working now on Lucid.

The adapter is always identified and finds the networks but it just never connects (without backports).

---

### Post by labinnsw on 2010-02-28
Would you mind giving ndiswrapper another go. What happens when you use ndiswrapper? List error messages if any.

---

### Post by spod on 2010-03-29
Hi, I ran into the same problem. I had previously got my DWA-140 working under Karmic by following [these instructions]("http://sudosys.be/?q=D-Link_DWA_140_ubuntu") to build the ralink driver.

The driver linked from those instructions no longer compiles due to kernel changes in 2.6.31.

Download the newer Ralink driver from their [Linux driver page]("http://www.ralinktech.com/support.php?s=2") (RT2870USB(RT2870/RT2770)) and follow the instructions linked above. This worked for me, hopefully it will be of some use to others out there upgrading to Lucid and running into the same problem.

---

