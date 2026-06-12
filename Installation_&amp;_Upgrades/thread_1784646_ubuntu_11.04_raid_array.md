---
title: "ubuntu 11.04 raid array"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by luigibmth on 2011-06-17
can you please point me to a guide/walk through etc in setting up a solution to reading a RAID (software raid) array which i have created in windows

my system is windows 7/Ubunto 11.04 both 64bit 

im guessing it would be easier to create the array in windows [as there are no linux drivers for my motherboard (Asrock 890FX Deluxe5)  than the other way around if possible at all]

---

### Post by YesWeCan on 2011-06-18
Hi there.
Have a read of this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

When Windows makes a RAID device (aka fake RAID) it requires some hardware on the motherboard and some special drivers.

When linux makes a RAID device it doesn't need any special hardware or drivers. There will be no problem at all making a linux RAID using your hardware.

Linux can read and write a Windows RAID device. Windows cannot read nor write a linux RAID device.


So if you need Windows to be able to use this RAID device you will have to use fake RAID and the appropriate linux commands to mount it. I think you have to install 'dmraid' and then do 'sudo dmraid -ay' and then mount the device. But check the guide as I have never done this.

If you do not need Windows to use the RAID you are much better off using linux' mdadm.

---

