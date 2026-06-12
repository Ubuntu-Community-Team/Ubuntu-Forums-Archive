---
title: "Tmobile (easy) 3G configuration for Intrepid Ibex requested"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by djrakun on 2008-10-22
Hi all,

One of the advertised new features for 8.10 is that it has support for 3g mobile broadband.  The network interfaces configuration gui has a wizard that has three Tmobile configurations ( web (wap?) internet ( 3g?) and vpn).  The configuration windows are pretty bare after you choose which one you want, the only real difference is the address you are pointed to.  I've also tried this card on 64bit kubuntu and the configuration window is more or less the same, just without the 'wizard'. I'm using a Sony Ericsson CG89 PCMCIA card from Tmobile, and I would have expected a HOWTO doc for configuration of the most standard mobile broadband equipment per carrier, but I've been unable to find any 8.10 whitepapers on how to do so.

I found a link on how to connect with this card the 'hard' way, but the author admits that dl speed is poor and I have to believe that there is an improved method to connecting with this device on Intrepid Ibex.  

[http://erikstambaugh.com/gprshowto.html](http://erikstambaugh.com/gprshowto.html)

If there is a doc available on basic configuration of devices, please point me in the right direction, otherwise if one could be written, I'd be much obliged.

Thanks!

---

### Post by Rocket2DMn on 2008-10-22
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by plun on 2008-10-22
This is Ubuntus wiki for this..

[https://wiki.ubuntu.com/%20NetworkManager/Hardware/3G](https://wiki.ubuntu.com/%20NetworkManager/Hardware/3G)

Many "unkown"... within my country a lot is corrected and works.:)

---

### Post by djrakun on 2008-10-23
thanks, Plun.  This link is very helpful for a starting point ( and hopefully an end )

I was unable to locate my device with the prescribed method in the probing networks link embedded within, however i was able to get at least this info.  Without the hardware address I'm not sure how to proceed.


info for the sony ericsson gc89

lspci

```
02:00.1 Serial controller: Broadcom Corporation EDGE/GPRS data and 802.11b/g combo cardbus [GC89] (rev 03)
```



from my kern.log, I'm fairly confident that my node for this device is  ttyS1 ( either that or /devices/virtual/input/input22) 

extract after inputting my cg89:

```
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.130519] b43-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.131285] b43-pci-bridge 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.131317] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.136200] b43-phy10: Broadcom 4306 WLAN found
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.186242] phy10: Selected rate control algorithm 'pid'
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.189351] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.190974] serial 0000:02:00.1: enabling device (0000 -> 0001)
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.192284] serial 0000:02:00.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 23 09:16:26 wksadmin-laptop kernel: [87490.195004] 0000:02:00.1: ttyS1 at I/O 0xe000 (irq = 11) is a 16550A
Oct 23 09:16:31 wksadmin-laptop kernel: [87494.791003] input: b43-phy10 as /devices/virtual/input/input22
Oct 23 09:16:31 wksadmin-laptop kernel: [87494.856096] firmware: requesting b43/ucode5.fw
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.015724] firmware: requesting b43/pcm5.fw
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.036038] firmware: requesting b43/b0g0initvals5.fw
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.043572] firmware: requesting b43/b0g0bsinitvals5.fw
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.168054] b43-phy10: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.325771] Registered led device: b43-phy10::tx
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.326465] Registered led device: b43-phy10::rx
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.326924] Registered led device: b43-phy10::radio
Oct 23 09:16:31 wksadmin-laptop kernel: [87495.348285] ADDRCONF(NETDEV_UP): wlan1: link is not ready
```

I will submit this info to the wiki.ubuntu 3g intrepid testing to get the ball rolling.  Didn't see Broadcom in any of the exiting hardware reports

---

