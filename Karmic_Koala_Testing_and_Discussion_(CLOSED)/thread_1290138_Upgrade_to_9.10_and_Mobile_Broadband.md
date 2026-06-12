---
title: "Upgrade to 9.10 and Mobile Broadband"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by simone.tosti on 2009-10-13
Hello,
two week ago I updated to the beta version of ubuntu 9.10 from 9.04. All fine and awsome, but Mobile Broadband in the Network manager menù doesn't appear anymore.

I keep updating the system every hours but nothing change.

My mobile phone is connected trough an usb cable and is detected from the system

```
Bus 002 Device 007: ID 22b8:6402 Motorola PCS 
```and even my usbpen modem

```
Bus 001 Device 017: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
```If I try to add manually none device appear.

Before in ubuntu 9.04 both of them work fine. Under windows work fine. On other computers with ubuntu/windows work fine. My kernel is 2.6.31-13-generic and my pc is a sony vaio pcg-7r1m.

Any suggestion?
bye
thanks anticipatly

PS: this is kernel output when i connect my mobile phone with usb.

```

Oct 13 12:33:10 vaio kernel: [ 3046.477386] cdc_acm 2-2:1.0: ttyACM0: USB ACM device
Oct 13 12:33:10 vaio kernel: [ 3130.424121] usb 2-2: USB disconnect, address 9
Oct 13 12:33:10 vaio kernel: [ 3144.424067] usb 2-1: new full speed USB device using uhci_hcd and address 10
Oct 13 12:33:10 vaio kernel: [ 3144.590248] usb 2-1: configuration #1 chosen from 1 choice
Oct 13 12:33:10 vaio kernel: [ 3144.601194] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
Oct 13 12:33:10 vaio kernel: [ 3193.912128] usb 2-1: USB disconnect, address 10
Oct 13 12:33:10 vaio kernel: [ 3198.804063] usb 2-2: new full speed USB device using uhci_hcd and address 11

```

---

### Post by marcozambi on 2009-10-14
I have the same problem with Huawei E220 and I've just opened a thread about it.
I can tell you for sure that with the kernel included in the 9.10 vanilla beta img file the E220 works flawlessly.
Some of the latter kernel updates has messed up something, and now I am not able to connect anymore :(
Let's hope it'll be fixed.

---

### Post by Stefan Arsovski on 2009-10-20
I also upgraded from 9.04 to 9.10.
 But the Mobile Broandband is not working fine any more. I'm useing it to conect the laptop with 3G. I manage to conn 2-3 times out of 20 :P 
Also the Wireless is not respondig well, I've to restart from time to time. 
I hope it will be fixed soon, coz I love the KK :P

---

### Post by GeorgeVita on 2009-10-20
possibly your problem is:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

Till the patch come with an update, you can use a previous kernel (like 2.6.31-11-generic #38 if you already have it), or get the 'patched' from: [http://people.canonical.com/~apw/lp446146-karmic/](http://people.canonical.com/~apw/lp446146-karmic/)

You have to install:
1 ...headers...all
2 ...headers... i386 (for 32bit intel)
3 ...image...i386

Regards,
George

---

### Post by simone.tosti on 2009-10-21
Thanks George, I tried to install all the i386 deb found in the address you give me, but nothing change (at least if I try to connect with my mobile,  for usb dongle I will know in the evening cause I leave it at home).

What if I try to reinstall 2.6.28 from 9.04? There is a risk to mess up the system?

> **GeorgeVita said:**
> possibly your problem is:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

Till the patch come with an update, you can use a previous kernel (like 2.6.31-11-generic #38 if you already have it), or get the 'patched' from: [http://people.canonical.com/~apw/lp446146-karmic/]("http://people.canonical.com/%7Eapw/lp446146-karmic/")

You have to install:
1 ...headers...all
2 ...headers... i386 (for 32bit intel)
3 ...image...i386

Regards,
George

---

### Post by GeorgeVita on 2009-10-21
Hi **simone.tosti**,
when booting you must hold pressed **shift** key and choose the 'patched' kernel from grub menu.

**uname -a** will confirm the 'running' kernel.

Do not try previous kernels, just wait for the fixes.

Regards,
George

---

