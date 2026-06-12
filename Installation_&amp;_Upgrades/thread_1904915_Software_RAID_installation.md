---
title: "Software RAID installation"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by adman_9000 on 2012-01-05
Hi

I have a pair of identical 2TB hard drives I am attempting to install Ubuntu 10 onto using the software RAID option on the alternate installation cd. I have tried following the guide at [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) but no joy. I have also tried hardware raid using the mobo onboard RAID and also a PCI-e raid controller which claimed to work with linux but turns out not to. Has anyone out there managed to complete a successfull installation of Ubuntu 10 on a RAID-1 array either using a cheap hardware controller or the software RAID? And if so how??

---

### Post by darkod on 2012-01-05
Do you plan to run one big root partition and one small swap? Or you want a more specific setup?

---

### Post by sgtGarcia on 2012-01-05
I have 2 1TB drives in RAID0 on FakeRAID ( ICH9R that I have on motherboard ).
I don't know if FakeRAID is better or not than SoftRAID, but it's less work to set-up.

Short how to:
1. In BIOS set SATA controller to RAID
2. Reboot
3. After BIOS POST when disks are recognized, there will be text displayed on screen, something like: Press <Ctrl>+<I> to configure RAID
or something similar, Press displayed combination to get in configurator.
4. Join both disks in RAID 1
5. Reboot
6. Start installation of Ubuntu ( from normal CD/DVD not alternate )
7. While partitioning window appears, the drive should be named something like that: /dev/mapper/isw_dcafcjjdig_NAME_WHICH_YOU_GAVE_IN_BIOS_RAID_SETUP

Remeber, that with FakeRAID maximal size of RAID cannot be more than 2TB, if You want to boot from that RAID array

---

### Post by darkod on 2012-01-05
> **sgtGarcia said:**
> I have 2 1TB drives in RAID0 on FakeRAID ( ICH9R that I have on motherboard ).
I don't know if FakeRAID is better or not than SoftRAID, but it's less work to set-up.

Short how to:
1. In BIOS set SATA controller to RAID
2. Reboot
3. After BIOS POST when disks are recognized, there will be text displayed on screen, something like: Press <Ctrl>+<I> to configure RAID
or something similar, Press displayed combination to get in configurator.
4. Join both disks in RAID 1
5. Reboot
6. Start installation of Ubuntu ( from normal CD/DVD not alternate )
7. While partitioning window appears, the drive should be named something like that: /dev/mapper/isw_dcafcjjdig_NAME_WHICH_YOU_GAVE_IN_BIOS_RAID_SETUP

Remeber, that with FakeRAID maximal size of RAID cannot be more than 2TB, if You want to boot from that RAID array

It does need to install from alternate because grub doesn't install correctly in lots of cases when using the normal cd to install on raid. It can work at times, but not always.

SoftRAID would be much better because you could even plug the disk in another computer and still read your data, which you can't do with fakeraid if I'm not mistaken.

---

### Post by sgtGarcia on 2012-01-05
> **darkod said:**
> ...SoftRAID would be much better because you could even plug the disk in another computer and still read your data, which you can't do with fakeraid if I'm not mistaken.

With FakeRAID it is probably similar, just southbridge has to be indentical ( Intel ICH from 5 to 10 & one built in newest Intel chipsets for Sandy/Ivy Bridge are compatible AFAIK but are not compatible with nVidia & ATI controllers ).

As for alternate or normal CD installation, whatever He have should work for FakeRAID, for SoftRAID only alternate CD AFAIK will work.

---

### Post by adman_9000 on 2012-01-09
> **darkod said:**
> Do you plan to run one big root partition and one small swap? Or you want a more specific setup?

Yeah just going for the standard setup, don't need anything fancy in that respect. 

> I have 2 1TB drives in RAID0 on FakeRAID ( ICH9R that I have on motherboard ).
I don't know if FakeRAID is better or not than SoftRAID, but it's less work to set-up.

I tried fakeraid on the mobo first off but didn't get anywhere with it, I can't recall the exact error I had but I'll give it another try and post later..

---

