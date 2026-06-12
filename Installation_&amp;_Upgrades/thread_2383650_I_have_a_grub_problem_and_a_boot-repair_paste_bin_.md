---
title: "I have a grub problem and a boot-repair paste bin link"
date: 2018-01-28
forum: Installation &amp; Upgrades
---

### Post by Hat-trick on 2018-01-28
So I did a fresh install of the latest LTS.  I have done this about 4 or 5 times dual booting windows 8.0 over the past 6 years.  I have always had to use boot-repair to get grub back the way it should and it has always worked except for this time.  I did everything the same way I always have and booted up ubuntu and played around with it then I rebooted, logged in, and it just hung with a purple screen.  After three more attempts with the same results I just decided to re-install.  It only takes me like 10 - 15 minutes.  I think this is where it all started going downhill.  I'm not sure, but I think the bootloader has always been installing in DEV/SDA but I put for whatever reason I may have put it in some partition called mmcblk0. It was 4 in the morning on a saturday.  Now ubuntu works fine as long as I only use ubuntu.  If I ever try to use windows I will never see the grub again.

Any help?  Here's the link. 

[http://paste.ubuntu.com/26474676](http://paste.ubuntu.com/26474676)

---

### Post by managerceo1 on 2018-01-28
1.run a live-cd, precise pangolin is probably the best option
2.mount the partition where Ubuntu is and take note of the mount point
3.run this sudo grub-install --root-directory=/mount/point /dev/sdX

Hope it helps

---

### Post by oldfred on 2018-01-28
Boot-Repair did reinstall grub. 
And now you have an UEFI entry for ubuntu in UEFI boot menu.
But your UEFI is not even showing a separate entry for Windows.

I see mention of Sony. 
Sony has always needed work arounds and Boot-Repair now does one of those automatically.
Boot-Repair copies shimx64.efi to /EFI/Boot/bootx64.efi and backs up current bootx64.efi which may be copy of Windows boot file.
And since no Windows specific entry, it looks like your system just uses the bootx64.efi entry to boot, even Windows.

From report & this command
sudo efibootmgr -v
      ```
 BootOrder: 0001,2001,2002,2003
Boot0000* EFI USB Device (KingstonDataTraveler 3.0)	PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(1,0)/HD(1,MBR,0x4294967287,0x800,0x1dd7800)RC
Boot0001* ubuntu	HD(3,GPT,91dba67f-7cc6-417e-bc9a-cf1c49068569,0x363800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC 


```

You still have no Windows entry and no hard drive entry. Can you boot ubuntu entry 0001?

---

### Post by Hat-trick on 2018-01-29
> **oldfred said:**
> Can you boot ubuntu entry 0001?

Using grub I can boot into Ubuntu as often as I want.  But if I ever boot into windows for the first time I will lose grub forever.  So when I boot up the machine it just goes straight into windows each time.  If I want to get into ubuntu again I need to use a live cd and run boot-repair.  Then I'll have grub back and I will then be able to choose Ubuntu to boot.

---

### Post by oldfred on 2018-01-29
If we add a Windows entry, does it work?

Your ESP is sda3, so you need to use second example.
 This should create a new entry, if ESP is sda1, uses defaults:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
if ESP sda3, you have to specify drive & partition with -d & -p options:
sudo efibootmgr -c -d /dev/sda -p 3 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

More details on efibootmgr and parameters:
man efibootmgr

---

### Post by Hat-trick on 2018-02-03
it shows this

** Warning ** : Boot0002 has same label Windows Boot Manager
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0001,0003,0002,2001,2002,2003
Boot0000* EFI USB Device (KingstonDataTraveler 3.0)
Boot0001* ubuntu
Boot0002* Windows Boot Manager
Boot0003* Ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0004* Windows Boot Manager

I don't know if that fixed anything.  I'm currently backing up my laptop so I can't check.  If it doesn't work then I'm going to do a windows system recovery using VIAO care.  If it wipes my machine clean then I'll just set it back up again, I don't mind.

---

### Post by oldfred on 2018-02-03
You show two Windows entries & two Ubuntu entries.
Do they work?

Best to use this to see if entries are really the same or not.
sudo efibootmgr -v

---

### Post by Hat-trick on 2018-02-03
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0003,0001,2001,2002,2003
Boot0000* ubuntu	HD(3,GPT,91dba67f-7cc6-417e-bc9a-cf1c49068569,0x363800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager	HD(3,GPT,91dba67f-7cc6-417e-bc9a-cf1c49068569,0x363800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0002* EFI USB Device (KingstonDataTraveler 3.0)	PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(0,0)/HD(1,MBR,0x4294967287,0x800,0x1dd7800)RC
Boot0003* Ubuntu	HD(3,GPT,91dba67f-7cc6-417e-bc9a-cf1c49068569,0x363800,0x82000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

---

### Post by oldfred on 2018-02-04
Your detailed report is different that first version.
You now only have one Windows boot option. The two Ubuntus are one is grub - 0003 and the other shim -0000. Grub only works with Secure boot off. Shim entry should work whether UEFI Secure Boot is on or off, if you have Secure boot versions of kernel and no proprietary drivers.

---

### Post by Hat-trick on 2018-02-05
> **oldfred said:**
> Your detailed report is different that first version.

I reinstalled Ubuntu with the boot loader at dev/sda.

> **oldfred said:**
> Grub only works with Secure boot off. Shim entry should work whether UEFI Secure Boot is on or off, if you have Secure boot versions of kernel and no proprietary drivers.

Are you saying I should turn secure boot off?

---

### Post by oldfred on 2018-02-05
Generally for now, UEFI Secure Boot off is better.
If you need proprietary drivers for video or WiFi then you must have Secure Boot off, for now.

---

### Post by Hat-trick on 2018-02-13
closing this thread as I may have changed too many things since the original problem

---

