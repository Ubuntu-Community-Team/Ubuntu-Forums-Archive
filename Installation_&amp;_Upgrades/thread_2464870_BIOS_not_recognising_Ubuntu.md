---
title: "BIOS not recognising Ubuntu"
date: 2021-07-14
forum: Installation &amp; Upgrades
---

### Post by dinoosawruss on 2021-07-14
Hi,

I have recently purchased a new drive and am attempting to setup dual booting, I have tired both Fedora and Ubuntu with no success.

[https://i.imgur.com/CG2OGb8.png](https://i.imgur.com/CG2OGb8.png)
As you can see above the 125GB partition is populated (currently with Ubuntu) 

However, when I attempt to boot into it my BIOS only recognises Windows Boot Loader and gives me no option to boot into Ubuntu
The same happened when I attempted to install Fedora.

To set it all up I:
1. Setup a new partition on my drive
2. Rebooted with an install flash drive plugged in
3. Booted into the flash drive 
4. Went through the normal Ubuntu/Fedora setup menus
5. Waited for the install to complete
6. Rebooted
7. Entered Boot Menu to boot into Ubuntu

My BIOS is American Megatrends R01-A4
Further details in the image below
[https://i.imgur.com/pexNppK.png](https://i.imgur.com/pexNppK.png)

I am fairly new to trying to use a Linux system of any kind seriously so am unsure if I am just doing something wrong

Thanks for any help in advance it would be much appriciated

---

### Post by deadflowr on 2021-07-14
Your partition layout image only shows that the 125GB partition exists and is in a healthy state.
But has no information as to what's going on inside the partition.
I'd recommend running boot-repair: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Run the summary section and post back the paste link it gives.

---

### Post by oldfred on 2021-07-14
In addition to deadflower's suggestion on Boot-Repair.

Acer often needs UEFI firmware update. And if SSD, SSD firmware update.
And then you have to enable "trust" on the "unknown" UEFI boot entry which is for ubuntu.

Most are similar, but some explain it better:
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

---

### Post by dinoosawruss on 2021-07-14
> **deadflowr said:**
> Your partition layout image only shows that the 125GB partition exists and is in a healthy state.
But has no information as to what's going on inside the partition.
I'd recommend running boot-repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Run the summary section and post back the paste link it gives.
I will attempt boot repair now

> **oldfred said:**
> In addition to deadflower's suggestion on Boot-Repair.

Acer often needs UEFI firmware update. And if SSD, SSD firmware update.
And then you have to enable "trust" on the "unknown" UEFI boot entry which is for ubuntu.

Most are similar, but some explain it better:
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
I have looked at these threads before and it seems they have a different BIOS to me, I cannot find an option regarding "trust" anywhere in my BIOS
My only secure boot options are "Enabled" and "Disabled"

---

### Post by dinoosawruss on 2021-07-14
[https://imgur.com/a/oDtJGG5](https://imgur.com/a/oDtJGG5)
Each relevant page of the BIOS

---

### Post by dinoosawruss on 2021-07-14
> **deadflowr said:**
> Your partition layout image only shows that the 125GB partition exists and is in a healthy state.
But has no information as to what's going on inside the partition.
I'd recommend running boot-repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Run the summary section and post back the paste link it gives.

[http://paste.ubuntu.com/p/HBrTcRfqpk/](http://paste.ubuntu.com/p/HBrTcRfqpk/)

---

### Post by oldfred on 2021-07-14
Lets try these two entries & then a check if they are added. Use Ubuntu live installer in live mode.
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/sda -p 1
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 1
sudo efibootmgr -v

for more info on efibootmgr 
man efibootmgr

Have you updated UEFI?
Many with Acer have found that is required.
Quick search show at least two newer UEFI firmware versions available from your screenshot of version you have.

---

### Post by dinoosawruss on 2021-07-14
> **oldfred said:**
> Lets try these two entries & then a check if they are added. Use Ubuntu live installer in live mode.
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/sda -p 1
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 1
sudo efibootmgr -v

for more info on efibootmgr 
man efibootmgr

Have you updated UEFI?
Many with Acer have found that is required.
Quick search show at least two newer UEFI firmware versions available from your screenshot of version you have.

Updated UEFI - still no option for "Trust" - all options are identical

Ran efibootmgr:
```
ubuntu@ubuntu:~$ sudo efibootmgr -c -g -w -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/sda -p 1
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0002,0000,0006,0005,0001,0004
Boot0000* Windows Boot Manager
Boot0001  Fedora
Boot0004  ubuntu
Boot0005* UEFI: USB Flash Disk 1100
Boot0006* UEFI: USB Flash Disk 1100, Partition 1
Boot0002* UEFI hard drive
ubuntu@ubuntu:~$ sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 1
efibootmgr: ** Warning ** : Boot0004 has same label ubuntu
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0003,0002,0000,0006,0005,0001,0004
Boot0000* Windows Boot Manager
Boot0001  Fedora
Boot0002* UEFI hard drive
Boot0004  ubuntu
Boot0005* UEFI: USB Flash Disk 1100
Boot0006* UEFI: USB Flash Disk 1100, Partition 1
Boot0003* ubuntu
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0003,0002,0000,0006,0005,0001,0004
Boot0000* Windows Boot Manager    HD(1,GPT,081fc9ea-ef6c-4d0e-9564-0e75aaba89b7,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3................
Boot0001  Fedora    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002* UEFI hard drive    HD(1,GPT,081fc9ea-ef6c-4d0e-9564-0e75aaba89b7,0x800,0x32000)/File(\EFI\Boot\bootx64.efi)
Boot0003* ubuntu    HD(1,GPT,081fc9ea-ef6c-4d0e-9564-0e75aaba89b7,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* UEFI: USB Flash Disk 1100    PciRoot(0x0)/Pci(0x14,0x0)/USB(7,0)/CDROM(1,0x6a4,0x7d00)..BO
Boot0006* UEFI: USB Flash Disk 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(7,0)/HD(1,MBR,0x38b1c112,0x6a4,0x1f40)..BO

```

Still not in the boot menu

---

### Post by yancek on 2021-07-15
>  Still not in the boot menu 		 

What 'boot menu' are you referring to?  The output of efibootmgr shows one entry for Fedora (0001) as well as 2 for Ubuntu (0003, 00004).  Can you set either (0003 or 0004) to first boot priority from your BIOS?  Try the command below, if that fails replace 0003 with 0004.  You should be able to do this from the install USB.  I don't use Acer but my understanding is that you first need to set a Supervisor password in the BIOS before you can enable Trust, have you done that?

```
sudo efibootmgr -o 0003
```

---

### Post by dinoosawruss on 2021-07-15
> **yancek said:**
> What 'boot menu' are you referring to?
I am refferring to the menu that appears when I press F12 that allows me to select what boot device I'd like to use
See this for an image of said menu: [https://imgur.com/a/iYTvPgz](https://imgur.com/a/iYTvPgz)

> **yancek said:**
> Can you set either (0003 or 0004) to first boot priority from your BIOS?  Try the command below, if that fails replace 0003 with 0004.
This worked until I rebooted...
I rebooted and Ubuntu was there, I was able to boot into it successfully but upon rebooting again Ubuntu was gone and there were 3 Windows Boot Managers remaining 
Here is the full output of that command:
```

ubuntu@ubuntu:~$ sudo efibootmgr -o 0003 
BootCurrent: 0006 
Timeout: 1 seconds 
BootOrder: 0003 
Boot0000* Windows Boot Manager 
Boot0001  Fedora 
Boot0002  UEFI hard drive 
Boot0003  ubuntu 
Boot0004  ubuntu 
Boot0005* UEFI: USB Flash Disk 1100 
Boot0006* UEFI: USB Flash Disk 1100, Partition 1

```

Unsure why there are now 3 Windows Boot Managers and why the Ubuntu option went away after I rebooted the machine

> **yancek said:**
> I don't use Acer but my understanding is that you first need to set a Supervisor password in the BIOS before you can enable Trust, have you done that?
Yes even after setting a supervisor password there are no options for trust see: [https://imgur.com/a/oDtJGG5](https://imgur.com/a/oDtJGG5) (all relevant BIOS pages with Supervisor password setup)

---

### Post by oldfred on 2021-07-15
Have you updated UEFI firmware.
Many with Acer have had that solve various issues.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

You also can use efibootmgr to remove old UEFI entries 0001 & 0004.
sudo efibootmgr -v
Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

You then also should remove /EFI/fedora folder in ESP - efi system partition. Do not remove any other folders.

---

### Post by dinoosawruss on 2021-07-15
Yep I have upgraded my BIOS but still no option for Trust (my BIOS is different to the one in these posts even though they're both made by Acer)

I have also removed old entires and /EFI/fedora


I've managed to get Ubuntu to be bootable once but then after booting into it or Windows the next time I come back it is gone and I have to boot into a USB flash and Try Ubuntu and do the process again
I managed to do this by setting the boot order to boot into 0003 however the next time I reboot my machine it has been reset back to the default - perhaps there is a way to stop it being reset???

---

### Post by oldfred on 2021-07-15
Some have found using efibootmgr only works temporarily.
But then changing boot order in UEFI settings does work.
Can you change order in UEFI settings, not UEFI boot menu?

---

### Post by tea for one on 2021-07-16
Have you disabled TPM support?

---

