---
title: "Blackscreen during startup"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by kuv02 on 2016-01-23
When I reboot my uncles laptop, from time to time (like 20-30% of the time) it will hang in boot on a black screen.

I still can enter into Ctrl-ALT-F1 but executing startx from there will result in another blackscreen (this time with disabled backlight). I could switch to the next console, but I'm unable to start the grafic UI.

After such an event I started the OS sucessfully and imediatly checked the system log for errors. This is what I found when searching for "error" in KSystemLog:
```
23.01.2016 22:47:51    rf-acer    kernel    [    4.747169] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
23.01.2016 22:47:51    rf-acer    whoopsie[825]    [22:47:51] GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
23.01.2016 22:47:53    rf-acer    NetworkManager[834]    <error> [1453585673.412844] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
23.01.2016 22:47:57    rf-acer    org.kde.kded5[1189]    Qt: Session management error: networkIdsList argument is NULL
23.01.2016 22:47:57    rf-acer    org.kde.kded5[1189]    Qt: Session management error: networkIdsList argument is NULL
23.01.2016 22:48:07    rf-acer    kernel    [   21.176439] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.460476] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.488526] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.512572] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.604686] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:09    rf-acer    kernel    [   22.650318] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:09    rf-acer    kernel    [   22.674300] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!

```
Do you think one of those messages could be the reason for the blackscreen? And what can I do about it?

---

### Post by matt_symes on 2016-01-23
Hi

> **kuv02 said:**
> 
After such an event I started the OS sucessfully and imediatly checked the system log for errors. This is what I found when searching for "error" in KSystemLog:
```
23.01.2016 22:47:51    rf-acer    kernel    [    4.747169] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
23.01.2016 22:47:51    rf-acer    whoopsie[825]    [22:47:51] GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
23.01.2016 22:47:53    rf-acer    NetworkManager[834]    <error> [1453585673.412844] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
23.01.2016 22:47:57    rf-acer    org.kde.kded5[1189]    Qt: Session management error: networkIdsList argument is NULL
23.01.2016 22:47:57    rf-acer    org.kde.kded5[1189]    Qt: Session management error: networkIdsList argument is NULL
23.01.2016 22:48:07    rf-acer    kernel    [   21.176439] [B][drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.460476] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.488526] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.512572] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:07    rf-acer    kernel    [   21.604686] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:09    rf-acer    kernel    [   22.650318] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
23.01.2016 22:48:09    rf-acer    kernel    [   22.674300] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)![/B]

```
Do you think one of those messages could be the reason for the blackscreen? And what can I do about it?

I would say it's almost definitely due to the last errors i highlighted above.

This may be a known bug and may be fixed by a kernel update.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520040)

Can you post the output of

```
cat /etc/lsb-release
```

What kernel are you booted into ?

```
uname -a
```

```
sudo lshw -C display
```

Kind regards

---

### Post by kuv02 on 2016-01-23
Here it is:```
 ~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=15.04 
DISTRIB_CODENAME=vivid 
DISTRIB_DESCRIPTION="Ubuntu 15.04" 
~$ uname -a 
Linux rf-acer 3.19.0-47-generic #53-Ubuntu SMP Mon Jan 18 14:02:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 
~$ sudo lshw -C display 
[sudo] password for user:  
  *-display                
       Beschreibung: VGA compatible controller 
       Produkt: Broadwell-U Integrated Graphics 
       Hersteller: Intel Corporation 
       Physische ID: 2 
       Bus-Informationen: pci@0000:00:02.0 
       Version: 09 
       Breite: 64 bits 
       Takt: 33MHz 
       Fähigkeiten: msi pm vga_controller bus_master cap_list rom 
       Konfiguration: driver=i915_bpo latency=0 
       Ressourcen: irq:53 memory:c2000000-c2ffffff memory:d0000000-dfffffff ioport:5000(Größe=64) 
  *-display 
       Beschreibung: 3D controller 
       Produkt: GM108M [GeForce 840M] 
       Hersteller: NVIDIA Corporation 
       Physische ID: 0 
       Bus-Informationen: pci@0000:04:00.0 
       Version: a2 
       Breite: 64 bits 
       Takt: 33MHz 
       Fähigkeiten: pm msi pciexpress bus_master cap_list 
       Konfiguration: driver=nvidia latency=0 
       Ressourcen: irq:55 memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:3000(Größe=128)



```

---

### Post by matt_symes on 2016-01-23
Hi

> Produkt: Broadwell-U Integrated Graphics

There looks to be a bug in the broadwell chip and some of the kernels.

My advice would be to read the bug report i linked to above and this one.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1488719](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1488719)

Then you need to either upgrade or downgrade to a different kernel version until you find one that works as the 3.19 kernels seem to be a problem.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Maybe try this version first 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/)

If you need instruction on how to update your kernel then please post back.

Do you have an external monitor connected ? 

**EDIT:**

Apparently the 3.13 series of kernel may not suffer from this bug as you may want to roll back to that one.

Kind regards

---

### Post by kuv02 on 2016-01-23
There was an external monitor (TV) connected. I tried the boot with TV connected, because I thought, maybe the output is redirtected to the HDMI port.

Maybe I can get my uncle (owner of that laptop) to hold out until 16.04 comes out (it will have Kernel 4.4)

But I've read in one bug that the bug prevailed, in another I've read it was fixed. So not sure, if Kernel 4.4 will fix the problem.

How hard is it to switch back to an older kernel? And would this mean security problems?

---

### Post by matt_symes on 2016-01-24
Hi

> **kuv02 said:**
> How hard is it to switch back to an older kernel?

No just reinstall the the linux genric kernel metapackge and the latest kernel from that kernel series. 

You'll lose the benefits of newer kernels such as better support for new hardware though.

> and would this mean security problems?

Not if you still use a supported kernel series and you keep that kernel updated. You are currently using the Vivid hardware enablement stack.

I can really only suggest you try kernels and see which ones work and update to 16.04 when you can.

Kind regards

---

### Post by kuv02 on 2016-01-27
Thanks
When I install an older Kernel, can I make it the default in grub, or will it only appear as one of the "alternative boot options"?

---

### Post by matt_symes on 2016-01-30
Hi

> **kuv02 said:**
> Thanks
When I install an older Kernel, can I make it the default in grub, or will it only appear as one of the "alternative boot options"?

Sorry for the late reply.

When you install an older kernel, it should update grub and appear as the first (default) entry in your gub menu.

You can double check by booting into the grub's default entry, opening a terminal and typing

```
uname -r
```

I'm not sure who long the 1.13 series of kernels are going to be supported for though. It may be for the lifetime of Trusty, i'm not sure.

Kind regards

---

