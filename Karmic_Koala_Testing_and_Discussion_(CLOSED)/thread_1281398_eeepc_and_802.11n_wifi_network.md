---
title: "eeepc and 802.11n wifi network"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nknico on 2009-10-03
I'm testing Kamic Koala Beta (on a USB stick) on my eeepc901 (this model uses the Ralink RT2860 controler)

I'm unable to connect my 802.11n network.

If I configure my routeur on N mode only, I can't connect at all.

But if I configure it on N+G, I can connect in G mode, at 54 MBits/s (instead of the theorical 300MBits/s on N mode).

Anyboby has the same problem here ??

---

### Post by Gourgi on 2009-10-03
did it used to work before? jaunty for example ?
i own an asus 1000h but since i don't have a 802.11n router i can't really try if it works or not.

---

### Post by nknico on 2009-10-03
I don't know if it works on Jaunty, cause I never try it.

But on my old PC I had a USB dongle with the RT2870 chipset (RT2860 is used on eeepc901) and it worked perfectly with Jaunty (at 300MBits/s). So I suppose it worked.

---

### Post by gaussian on 2009-10-03
If Wikipedia is to be believed, then there is no n-capability in most older EEEPCs, including yours.

See [http://en.wikipedia.org/wiki/ASUS_Eee_PC](http://en.wikipedia.org/wiki/ASUS_Eee_PC)

---

### Post by Gourgi on 2009-10-03
> **gaussian said:**
> If Wikipedia is to be believed, then there is no n-capability in most older EEEPCs, including yours.

See [http://en.wikipedia.org/wiki/ASUS_Eee_PC](http://en.wikipedia.org/wiki/ASUS_Eee_PC)

from the same link you posted 
> Other Eee 90x models

On June 3, 2008 Asus unveiled the Eee 901 at COMPUTEX Taipei, the 901 was a revision of the 900 series with a different chassis. The 901 features an Intel Atom Diamondville CPU clocked at 1.6GHz, an "expanded" battery (listed as 6-cell), and "Super Hybrid Engine" software for power management which will provide a battery life of 4.2 to 7.8 hours. Bluetooth and **802.11n** Wi-Fi are also included.

:-P

on-topic: if 802.11n is not working but used to , then it is a regression and should be reported in laucnhpad
```
ubuntu-bug linux
```

---

### Post by nknico on 2009-10-03
I'm sure my eeepc is n-capable since it works on Windows XP...

I'll post a Bug entry in Launchpad.

---

### Post by gaussian on 2009-10-03
> **Gourgi said:**
> from the same link you posted 

> 
Other Eee 90x models

On June 3, 2008 Asus unveiled the Eee 901 at COMPUTEX Taipei, the 901 was a revision of the 900 series with a different chassis. The 901 features an Intel Atom Diamondville CPU clocked at 1.6GHz, an "expanded" battery (listed as 6-cell), and "Super Hybrid Engine" software for power management which will provide a battery life of 4.2 to 7.8 hours. Bluetooth and 802.11n Wi-Fi are also included. 



I stand corrected. I should have read the article I was linking to, not just relied on the table that gives different information or at least very strong impression that there is no n-capability.

---

### Post by nknico on 2009-10-04
Before posting a bug, I'll try to compile the Ralink's site rt2860_sta driver (the driver included in Karmic is the serialmonkey one, no ?)

And also try with wicd (it seems that network-manager has some problems in Karmic)

---

### Post by HankB on 2009-10-04
I have a wireless-N router and a 901 and it does work. ISTR that it would not associate if I had security set to TKIP+AES but works fine with AES. 
current router settings are WPA2 personal with AES encryption. This was originally with Jaunty and still working with Karmic.

-hank

---

### Post by Gourgi on 2009-10-04
> **nknico said:**
> Before posting a bug, I'll try to compile the Ralink's site rt2860_sta driver (the driver included in Karmic is the serialmonkey one, no ?)

And also try with wicd (it seems that network-manager has some problems in Karmic)

judging from my 1000h EEE , karmic still uses rt2860sta, although it is an older version.
```
modinfo rt2860sta
...
version : 1.8.1.1
...

```
bug is submitted [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376577](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376577), it is confirmed but still we use the old module version in karmic.

i've found a ppa with the newer version but it doesn't install in karmic
[https://edge.launchpad.net/~henrik-hw0/+archive/ppa](https://edge.launchpad.net/~henrik-hw0/+archive/ppa)

serialmonkey's drivers (for 2860 chips) aren't quite ready yet (at least the ones included in karmic)

---

### Post by nknico on 2009-10-04
> **HankB said:**
> I have a wireless-N router and a 901 and it does work. ISTR that it would not associate if I had security set to TKIP+AES but works fine with AES. 
current router settings are WPA2 personal with AES encryption. This was originally with Jaunty and still working with Karmic.

-hank

I can connect, but only in G mode (i'm sure of that because routeur's web interface indicates that). And I am with the config as you : WPA2 AES encryption

I am trying to compile the 2.2.0.0 driver from Ralink webpage and it does't compile...

```
/rt_linux.c:1691: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/ubuntu/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1692: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/ubuntu/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1702: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/ubuntu/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1736: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/ubuntu/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'
make: *** [LINUX] Error 2

```

---

### Post by Gourgi on 2009-10-05
hi again
after searching this a little more it seems that the new ralink drivers can't build in kernel newer than 2.6.30. 
Other people including myself get the same errors when trying to compile the drivers.
But there are some rt2860sta drivers are included already on newer kernels in the staging tree of kernel/drivers that as far as i can understand "follow" ralink's changes.Here is some info about the staging tree [http://www.kroah.com/log/linux/staging-status-09-2009.html](http://www.kroah.com/log/linux/staging-status-09-2009.html) and here is the rt2860 tree's history ([http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=history;f=drivers/staging/rt2860;h=082e4920ac18619cf347ecc76f86f691845c0767;hb=8a0382f6fceaf0c6479e582e1054f36333ea3d24](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=history;f=drivers/staging/rt2860;h=082e4920ac18619cf347ecc76f86f691845c0767;hb=8a0382f6fceaf0c6479e582e1054f36333ea3d24))
> rt* wireless drivers. Bart has done amazing work merging all of these together into something much better than they originally were. And even better, they still work! Great job Bart!

So you could try the newer kernel v2.6.32-rc1 from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc1/)
Here is the changelog [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc1/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc1/CHANGES), search for "rt2860" will list you the changes since 2.6.31.
I hope this helps you.

---

### Post by nknico on 2009-10-07
Thank you !

I will try the 2.6.32 but I don't want to install the RC1, there are allways tons of new things in the RC1...I will wait the RC4-5 ...

---

### Post by Gourgi on 2009-10-07
> **nknico said:**
> Thank you !

I will try the 2.6.32 but I don't want to install the RC1, there are allways tons of new things in the RC1...I will wait the RC4-5 ...

i actually i already tried the mainline kernel and it doesn't include the stagging drivers by default. 
So i guess you have to compile your own kernel for this 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

