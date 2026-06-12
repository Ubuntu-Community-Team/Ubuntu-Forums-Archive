---
title: "Feisty Beta Live CD: &quot;can't access tty&quot;"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by patis on 2007-03-30
```
/bin/sh: can't access tty; job control turned off
(initramfs) [34.464746] ata2.00: failed to set xfermode (err_mask=0x04)
```

These are the first two lines of what I get when trying to install Feisty from the current beta live CD (the ata2.00 message keeps repeating forever with changing numbers in brakets). I'm **not** upgrading this PC from one Ubuntu to another. The hard drive has an old MS Windows version that I want to wipe out.

I've read other threads with this problem but with no definitive solution that I can apply to my case. acpi=off at the boot prompt doesn't help. I'd be frustrated if upon the official release this problem is still present (at least for my PC).

I wanted to start one thread specific to the Feisty live CD about this problem. This seems like a bug to me given the fact that the Ubuntu live CDs 6.06 and 6.10 work well in this PC. Any suggestions?

Thanks.

---

### Post by truck87bp on 2007-03-30
I had this same problem and tried Gparted to redo the drive...the live 7.10 disk worked after that...don't know why but it did.

Gparted is a nice program and not to hard to use...just don't forget to format your new setup before leaving Gparted.  I have Gparted on a seperate disk and love it.

---

### Post by patis on 2007-03-30
Thanks, but reformatting the hard drive didn't help. I just installed LTS server on this PC, no problems at all. And this I did with a full reformatting of the hard drive. But still the Feisty live CD fails to boot with exactly the same error. Now that I have LTS and just for reference, this is my hardware (nothing fancy):

```
$ sudo lshw -short
Password:
H/W path                Device     Class       Description
==========================================================
                                   system      Computer
/0                                 bus         D875PBZ
/0/0                               memory      BIOS
/0/4                               processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
/0/4/5                             memory      L1 cache
/0/4/6                             memory      L2 cache
/0/4/7                             memory      L3 cache
/0/4/1.1                           processor   Logical CPU
/0/4/1.2                           processor   Logical CPU
/0/37                              memory      System Memory
/0/37/0                            memory      PartNum1
/0/37/1                            memory      PartNum2
/0/37/2                            memory      PartNum3
/0/37/3                            memory      PartNum4
/0/1                               processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
/0/1/1.1                           processor   Logical CPU
/0/1/1.2                           processor   Logical CPU
/0/1/0                             memory      L1 cache
/0/1/1                             memory      L2 cache
/0/f8000000                        bridge      82875P/E7210 Memory Controller Hub
/0/f8000000/1                      bridge      82875P Processor to AGP Controller
/0/f8000000/1/0                    display     NV34 [GeForce FX 5200]
/0/f8000000/3                      bridge      82875P/E7210 Processor to PCI to CSA Bridge
/0/f8000000/3/1         eth0       network     82547EI Gigabit Ethernet Controller (LOM)
/0/f8000000/1d                     bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
/0/f8000000/1d/1        usb1       bus         UHCI Host Controller
/0/f8000000/1d.1                   bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
/0/f8000000/1d.1/1      usb2       bus         UHCI Host Controller
/0/f8000000/1d.1/1/2               input       Optical USB Mouse
/0/f8000000/1d.2                   bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
/0/f8000000/1d.2/1      usb3       bus         UHCI Host Controller
/0/f8000000/1d.3                   bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
/0/f8000000/1d.3/1      usb4       bus         UHCI Host Controller
/0/f8000000/1d.7                   bus         82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
/0/f8000000/1d.7/1      usb5       bus         EHCI Host Controller
/0/f8000000/1e                     bridge      82801 PCI Bridge
/0/f8000000/1e/2                   multimedia  CM8738
/0/f8000000/1f                     bridge      82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
/0/f8000000/1f.1                   storage     82801EB/ER (ICH5/ICH5R) IDE Controller
/0/f8000000/1f.1/0      ide0       bus         IDE Channel 0
/0/f8000000/1f.1/0/0    /dev/hda   disk        MAXTOR 6L040J2
/0/f8000000/1f.1/0/0/1  /dev/hda1  disk        Linux filesystem partition
/0/f8000000/1f.1/0/0/2  /dev/hda2  disk        Extended partition
/0/f8000000/1f.1/1      ide1       bus         IDE Channel 1
/0/f8000000/1f.1/1/0    /dev/hdc   disk        CR-48XGTE
/0/f8000000/1f.1/1/0/0  /dev/hdc   disk        
/0/f8000000/1f.2        scsi0      storage     82801EB (ICH5) SATA Controller
/0/f8000000/1f.3                   bus         82801EB/ER (ICH5/ICH5R) SMBus Controller
```

... still in the dark.

---

### Post by revoltism on 2007-04-09
had the same problem whit my dvd-rom.. luckily i got a second..a dvd-rw and when i booted the livecd 'with that   it worked.. no problems..

---

