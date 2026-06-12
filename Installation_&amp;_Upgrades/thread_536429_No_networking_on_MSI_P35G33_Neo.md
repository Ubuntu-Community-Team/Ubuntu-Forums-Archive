---
title: "No networking on MSI P35/G33 Neo"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by oznelig on 2007-08-27
Hi,

After using Linux for a few years, I never had so many problems as this time installing it.
My system :
Core Duo E6850 3 GHz
MB MSI P35/G33 Neo
Lite On DVDRW
2 GB 800MHz DDR2
Xpert Vision 8500GT video card
320 Gbyte HD Sata II
Monitor 24 " 1920x1200

The system also has winxp that works perfectly.
First I tried Fedora 7 and it wouldn't recognize the DVD. After installing it through a USB
driver, it still didn't see the DVD (a known problem apparently) and no networking.
Ah, and Fedora changed the boot so that I could no longer use winxp!!

I then tried Ubuntu 7.04 with no much extra success (graphics was wrong as well).
I then found this post : [http://ubuntuforums.org/showthread.php?t=490874](http://ubuntuforums.org/showthread.php?t=490874)
Using Gutsy Tribe 4 x64 and by setting generic.all_generic_ide=1 I can now do almost
everything except networking.
During booting, using nosplash, I can see that everything is marked ok, including networking.
There's only something going funny, but it's too fast for me to see and I can't find the boot
log in /var/log. I see a lot of other logs saying that the driver for eth0 has been loaded,
but not the one showing me the screen at boot time.

If I open the Network tools the network device that appears is loopback !
I can select eth0 but, if I do,  there's no information at all : all not available.
I can also select eth0:avahi (what is it ?). This is better as there is the HW
address as well as other parameters. However, if I click on Configure,
I get "the interface does not exist" !

Also, /sbinifconfig /all returns :
/all: error fetching interface information : Device not found

I also tried Gutsy Tribe 5, same problem. Maybe x64 is no good for CoreDuo ?

Any ideas ? Please help.

Enzo

---

### Post by Pumalite on 2007-08-27
It's your motherboard. Do a search on it.

---

### Post by oznelig on 2007-08-27
I searched "msi p35 g33 linux network problem"
and similar but there are too many non specific results. If you know of any
link, please post.
If you can suggest a motherboard that you know works well and
supports the 3 GHz Core Duo, please post that too : I just
bought the PC and I can change the MB.

Thanks,

Enzo

---

### Post by Pumalite on 2007-08-27
[http://ubuntuforums.org/showthread.php?t=536409](http://ubuntuforums.org/showthread.php?t=536409)

I'm writing to you from a Tribe 4 installed on a Core 2 Duo with Intel D975XBX

---

### Post by oznelig on 2007-08-27
Thanks, I searched all the links you posted for P35 and only one mentioned it,
with no reference to networking.
Most of these posts seem to be related to the Jmicro chipset and the not
recognized DVD/CD driver : I no longer have those issues, I have worked around
them.
The issue I have is networking. The MB uses the Realtek RTL8111B.
I can see the kernel loading this driver and, in any case, it's even available on
the Realtek site, so it should be supported.

Enzo

---

### Post by Pumalite on 2007-08-27
Might help; I don't know. Hope it does.

[http://ubuntuforums.org/showthread.php?t=459459&page=2](http://ubuntuforums.org/showthread.php?t=459459&page=2)

---

### Post by oznelig on 2007-08-27
YES!! It id help, on page two of the link you sent me,
there's the following :
-------------------------------------------------------------------------------------
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.
-------------------------------------------------------------------
Done that in winxp, rebooted and now networking is ON!

Thanks,

Enzo

---

### Post by Pumalite on 2007-08-27
Glad it worked! It will help others too, I'm sure.

---

