---
title: "Configuring Kernel Question"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by ububu on 2005-09-07
Hello, 

I am trying to follow instructions I found in this forum about setting up my wireless to work on my laptop.  I am having trouble understanding the following instructions:

enable the CONFIG_NET_RADIO option in the kernel configuration

I have figured out how to get the kernel configuration thingee up using the  xconfig command that brings up the graphical interface.  I just can't find where I'm supposed to enable the CONFIG_NET_RADIO sub-thingee.  I look all around and can't find it.  I used the search thingee and found oodles of files in the "filesystem" that contain the wording CONFIG_NET_RADIO.  It didn't seem right that I should have to open each one of them to find the one that I need to change.  Can someone please explain to me how to do this?  Thank you very much.

---

### Post by pmjdebruijn on 2005-09-07
Hi,

Well I don't know where it's located, but it's there somewhere... Also beware, that the CONFIG_NET_RADIO is the define name in the code, it isn't the exact name displayed in xconfig, there it'll probably be something like Network Radio of something like that.

Anyway there's a fast way around this... Open /usr/src/linux/.config with your favorite text editor, and search for that string, and change the option there. Then don't forget to do a 'make oldconfig' before you start to compile.

Regards,
Pascal de Bruijn

---

### Post by ububu on 2005-09-08
Pascal,

Thank you very much for your reply.

When I open the Linux/.config file, it says at the top of the page that it is automatically generated and not to edit it.  Also, how do you search within a file?  I am using vi.  thanks again.

Richard

---

### Post by Strider on 2005-09-08
If you're using vi, you can type "/" and then whatever you're searching for.  It's much easier to run "make menuconfig" and navigate the tree to turn on wireless...

---

### Post by Strider on 2005-09-08
Don't have my linux system with me but I think what you're looking for is under the Devices section of "make xconfig" or "make menuconfig".

What type of WLAN card you have?  If you're using Ubuntu it should already have wireless enabled... maybe it doesn't see your card.

---

### Post by mlomker on 2005-09-08
You definitely shouldn't need to recompile your kernel to get wireless to work.

To answer your question about searching in vim--just type :/  and then what you want to search for (no spaces).  You can use 'n' to jump to the next item.

---

### Post by curVV on 2007-12-01
Hi, yeah I have a similar problem. I'm using a D-Link DWL-G650 wireless pcmcia device. It works fine, but I cannot use network or monitor tools to descover new wireless networks because those tools all complain that the device is unknown or doesn't exist. So I downloaded the driver from [http://hostap.epitest.fi/](http://hostap.epitest.fi/) . Now when I do a
```
make
```
i get the error
```
Makefile:53: WARNING: Linux wireless extensions, CONFIG_NET_RADIO, not enabled in the kernel
*** Can't build for 2.6 with a non-2.6 source!
```
My kernel version is 2.6.22-14-generic.
How can I now patch my kernel to enable CONFIG_NET_RADIO??

Thanks...

---

