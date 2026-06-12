---
title: "PB EasyNote LJ65 : not possible to install on any supported version"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by j2k15 on 2016-03-13
Hi there,

I own a Packard Bell EasyNote LJ65 running Vista.
I'd like to move to Ubuntu. I tried without success. When I start the live-cd, I get a black screen.

After some research it's due to the GMA4500M not being supported anymore.

I've tried the following ones :

Ubuntu :
- 14.04
- 15.10
Xubuntu :
- 14.04

I've even tested the latest version of Mint without success.

After some reading, I come to know that the latest version of Ubuntu running on this machine would be 10.04 or 10.10 which are now out of support.

So my question is : is it possible to get this version running on supported version of Ubuntu ? Or am I condamned to run outdated and unsupported versions ?

Thanks in advance for your help.

---

### Post by grahammechanical on 2016-03-13
When you install do you tick the box "Install third party software?" Ticking that box will bring in some third party audio & video codecs and also a proprietary video driver. And as you say, the video adapter is no longer supported by the proprietary video driver.

If you have not yet tried installing without ticking that box, then please try it.

Regards.

---

### Post by j2k15 on 2016-03-13
Hi,

The thing is that I can't even see the install wizard. Since after boot I've a black screen.
I'm trying to do some research and it seems that's a regression from Kernel > 2.6.38_rc8. After this version, the kernel is not managing the backlight of the screen anymore.

---

### Post by gordintoronto on 2016-03-14
This might help you:
[http://unix.stackexchange.com/questions/93799/how-can-i-install-arch-linux-on-a-laptop-with-intel-gma-4500-mhd](http://unix.stackexchange.com/questions/93799/how-can-i-install-arch-linux-on-a-laptop-with-intel-gma-4500-mhd)

---

### Post by j2k15 on 2016-03-16
It helps, thanks.
In Mint I'm indeed able to start in compatibility mode.
I've a permanent live USB of it. I'll try this and if it works I'll install it.
Thanks.
Anyway, I filled a bug on launchpad for this.

---

### Post by mörgæs on 2016-03-16
Please post the link.

---

### Post by j2k15 on 2016-03-17
Hi,

Here you go :
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/1556699](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/1556699)

And here's the link (in French) explaining the workaround step by step.
[https://doc.ubuntu-fr.org/intel_graphics#gma_4500](https://doc.ubuntu-fr.org/intel_graphics#gma_4500)

---

