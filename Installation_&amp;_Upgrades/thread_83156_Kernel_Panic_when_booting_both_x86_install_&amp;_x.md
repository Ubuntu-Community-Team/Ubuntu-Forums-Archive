---
title: "Kernel Panic when booting both x86 install &amp; x86 live CDs on ThinkPad 390E"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by sundae1888 on 2005-10-28
I was trying to install Breezy on an old ThinkPad 390E laptop (PII-330, 128MB RAM, 20GB HD, chipset i440BX). Unfortunately, I've ran through 3 different x86 install CD (downloaded separately, md5sum verified) as well as x86 live CD, but all of them produce a kernel panic. Below is the content of the last screen:

```
e0800 c01e4594
[4294671.040000]         c03856e0 00000001 c03856e0 c02e8900 0000000 c01e4886 
c02e8900 c7e0800
[4294671.040000] Call Trace:
[4294671.040000]  [<c01e9c9a>] serial8250_config_port+0x47/0x83
[4294671.040000]  [<c01e4594>] uart_configure_port+0x48/0x109
[4294671.040000]  [<c01e4886>] uarg_ad-one_port+0x62/0x9f
[4294671.040000]  [<c01ea471>] serial8250_register_port+0x92/0xaf
[4294671.040000]  [<c01ea760>] serial_pnp_probe+0x6f/0x8a
[4294671.040000]  [<c01c8e0e>] pnp_device_probe+0x63/0x82
[4294671.040000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4294671.040000]  [<c01ec0be>] driver_attach+0x36/0x54
[4294671.040000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4294671.040000]  [<c01ec7a5>] driver_register+0x23/0x25
[4294671.040000]  [<c01c8ea0>] pnp_register_driver+0x28/0x4a
[4294671.040000]  [<c0339e81>] serial8250_pnp_init+0xa/0xc
[4294671.040000]  [<c03246c2>] do_initcalls+0x4b/0x90
[4294671.040000]  [<c0100272>] init+0x0/0xd2
[4294671.040000]  [<c010029e>] init+0x2c/0xd2
[4294671.040000]  [<c0101245>] kernel_thread_helper+0x5/0xb
[4294671.040000] Code: 20 0f b6 43 01 d0 8b 13 48 ee 42 eb 15 03 53 04 c6 02
00 eb 10 03 53 04 c7 02 00 00 00 00 eb 05 03 13 31 c0 ee ff 74 24 0c 9d <83> c4
14 5b 5e 5f 5d c3 55 57 31 ff 56 53 83 ec 0c 8b 5c 24 20
[4294671.040000]  <0>Kernel panic - not syncing: Attempted to kill init!
[4294671.042000]

```

Is there any special boot param I should use? I remember using 2.4 kernel Knoppix on this machine before, so there's no reason why Ubuntu should fail, right? *Right?* 

Thanks!

---

### Post by stuporglue on 2005-10-28
When you see the initial CD boot screen, hit some of the F-keys and see if there isn't some special parameter you can pass for your computer. I think there were some codes for some types of thinkpads. 

Hope that helps,

Stuporglue

---

### Post by sundae1888 on 2005-10-31
There's a special parameter for some Thinkpad floppy, which I tried, but it didn't solve the problem.

The call trace indicated the kernel was balking at the serial driver, correct? Is there any boot parameter I can set to disable serial, since I don't use it anyway?

---

### Post by sappman2 on 2005-11-05
I have the same problem on my HP Pavillion Pent III 850 MHz. I have a clean hard-drive, nothing on it at all. I tried partitioning manually, tried installing without partitions on the drive, both the live CD and the install CD fail exactly like this, or they hang up saying "Segmentation Fault" over and over again.

I got it to install once, but I didn't have the network connected to it. That hosed up some other settings that didn't allow me to alter ANYTHING (not even the etc/host file, administrator settings, users, nothing.) so I tried another install and I'm back at square one. Any help for us both would be appreciated. I REALLY want Ubuntu or Kubuntu to work on my machine, but I'm getting frustrated.

---

### Post by sappman2 on 2005-11-08
I found the likely problem on my causing install to fail. I talked to one of my work-mates, who is far more computer-savvy than I. He suggested that I could be having a problem with my RAM. I insisted that the box ran fine on Windows, to which he replied that Windows, which "leaks" memory anyway, has  built-in redundancies that cover over RAM problems. Linux, however, does not.

BINGO! I ran "MEMTEST" from the install CD and only about 12% (Average) of my "brand-new" 512Mb RAM passed, even though my BIOS boot RAM test passed it w/no problems. I sincerely appreciate the UBUNTU community for their attempts at helping. I hope that, as I grow in knowledge, I'll be able to give back and help others and promote the benefits of Linux and Ubuntu. Now... Any ideas on a place to find decent, cheap RAM for a 6 year old Pentium III?      Thanks............... -Chris

---

