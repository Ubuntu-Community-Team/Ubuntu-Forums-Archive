---
title: "Install integrated graphic card Radeon HD 6470M on Ubuntu 15.10"
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by andrea105 on 2016-04-14
I've got a new computer (ASUS X54h, 64bit system), with a graphic card integrated and running Ubuntu 15.10. 
So, I'm trying to install the Radeon graphics card but seems that something don't work. Afterthe first try, I can't my run pc because it stopped at a black screen before to let me login, so I reinstalled Ubuntu.
 

Graphic card specifications: RADEON HD 6470M 1GB

  System specifications: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz width 64 bits

  

Thanks for help

---

### Post by grahammechanical on 2016-04-14
When you first installed Ubuntu it would have installed a video driver appropriate to the integrated video adapter which most likely was incompatible with the Radeon video adapter. When you re-installed Ubuntu was the machine using the new Radeon video adapter?

Regards.

---

### Post by mastablasta on 2016-04-15
if you also have intel GPU (hybrid) then you need to initialize the device before reboot.

see more here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

also if possible it would be better to use 14.04 (if possible better the original one, not the point releases). AMD support for this chip will be dropped in 16.04. after that only open source will be available.

14.04 is supported until 2019. however so far it is still not known what will happen with 14.04 point releases that get new kernels (HWE stack).

---

### Post by mörgæs on 2016-04-15
> **mastablasta said:**
> AMD support for this chip will be dropped in 16.04. after that only open source will be available.


I prefer to say that AMD drop their closed-source drivers and go all-in supporting open-source ones.

---

### Post by andrea105 on 2016-04-15
> **grahammechanical said:**
> When you first installed Ubuntu it would have installed a video driver appropriate to the integrated video adapter which most likely was incompatible with the Radeon video adapter. When you re-installed Ubuntu was the machine using the new Radeon video adapter?Regards.

Mumble mumble...
So, I checked graphic card name and chipset with ```
sudo lspci -nn | grep VGA
```
It seems to me that Radeon video adapter is in use, but I don't found anywhere on pc any Radeon or AMD setting
Here there's the result of the previous interrogation

```
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
pcilib: sysfs_read_vpd: read failed: Connection timed out
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
```



> **mastablasta said:**
> if you also have intel GPU (hybrid) then you need to initialize the device before reboot.

see more here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

I don't really understand why this

> **mastablasta said:**
>  also if possible it would be better to use 14.04 (if possible better the  original one, not the point releases). AMD support for this chip will  be dropped in 16.04. after that only open source will be available.

I don't understand why.
Commands and drivers for ubuntu 14.04 doesn't work on 15.10?

Thanks

---

### Post by mörgæs on 2016-04-18
> **andrea105 said:**
> Commands and drivers for ubuntu 14.04 doesn't work on 15.10?


Some continue to work, some don't.
Better to try a fresh install of 16.04 and see if you need any commands at all.

---

