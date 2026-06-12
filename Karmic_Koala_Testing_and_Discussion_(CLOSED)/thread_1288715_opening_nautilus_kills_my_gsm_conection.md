---
title: "opening nautilus kills my gsm conection"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Whise on 2009-10-11
After i boot  i connect to the internet using NM in my gsm internet.

When i open nautilus the connection gets closed and i cannot connect again until i reboot

this is very frustrating and happends 10 out of 10 times (always)

help please?

---

### Post by Whise on 2009-10-11
this is driving me crazy can someone help me please

---

### Post by GeorgeVita on 2009-10-11
Hi **Whise**,
there are some 'new' problems with kernels 2.6.31-12 and -13
(see [http://ubuntuforums.org/showthread.php?p=8068801](http://ubuntuforums.org/showthread.php?p=8068801))

Can you check: ```
uname -a
``` and if possible boot a previous kernel?
(2.6.31-11 preferred) 

Regards,
George

---

### Post by Whise on 2009-10-11
im using .13 i dont have any other kernel installed , this is very bad , hope it gets fixed

---

### Post by GeorgeVita on 2009-10-11
Following: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)
you can find a 'patch' but my opinion is: just wait!
Also we are not sure that this bug is really your problem.

I also tried 2.6.**32**-rc3 with the problem still there.

Other more complicate option (working on my ZTE MF636 but NOT on Huawei E169) is to stop network manager, killall modem-manager and then use wvdial or pppd.

Regards,
George

---

### Post by Whise on 2009-10-12
i think this is my problem , i reverted to the jaunty kernel and it works but i have other problems with that kernel now... intel gfx card

is it possible for you to send me the 2.31.11 kernel?

---

### Post by Whise on 2009-10-12
is it possible for you to send me the 2.31.11 kernel?


also using another browser other then nautilus also doesnt cause the problem , nautilus tries to load the usb modem like an usb drive

---

### Post by GeorgeVita on 2009-10-12
> Benjamin Herrenschmidt  wrote on 2009-10-11:  	  #9
We identified the bug upstream, it's a **2.6.31.1** - >2.6.31.2 regression. Still looking for a proper fix (yeah, I have one of these critters too)...

To get kernel 2.6.31-1 for **i386** (32bit intel) you must download and install the following (1-2-3):

1. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101_2.6.31-02063101_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101_2.6.31-02063101_all.deb)

2. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101-generic_2.6.31-02063101_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-headers-2.6.31-02063101-generic_2.6.31-02063101_i386.deb)

3. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-image-2.6.31-02063101-generic_2.6.31-02063101_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.1/linux-image-2.6.31-02063101-generic_2.6.31-02063101_i386.deb)

If you get them using other PC, copy them to desktop and double click 1st to install. After completing continue with the 2nd and finally the 3rd.

To use it you must hold down **shift key** at boot time and then choose it from grub menu. This will give you at least the 'knowledge' as the 'real correction' will come after some days.

EDIT: >>> other kernel versions: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
You must install **headers...all**, **headers...i386** and **image...i386**

**NEW EDIT:** >>> and a PATCH came from the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146"):
[http://people.canonical.com/~apw/lp446146-karmic/](http://people.canonical.com/~apw/lp446146-karmic/)

Regards,
George

---

### Post by Whise on 2009-10-12
thank you using this i fixed my problem, looks like nautilus wasnt the only one killing my connection other programs like rithmbox and others to..
i really hope developers fix this

---

