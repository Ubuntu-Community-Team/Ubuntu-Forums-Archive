---
title: "Ubuntu randomly not booting after installing a new sdd"
date: 2021-12-28
forum: Installation &amp; Upgrades
---

### Post by matteo-dagord on 2021-12-28
Hello,
I have a Toshiba Satellite L50B notebook.
Recently I installed the sdd in place of the hdd, and the hdd in the place of the optical drive (keeping the partition table).
My goal was to install the os (Ubuntu 18.04) on the sdd, and to mount the old home partition on the hdd; somehow, the installer maintained the old EFI boot partition. Anyway, the whole process went fine and the system is now working pretty good.
So the current setup is:
- sda1: Ubuntu root (fresh installation)
- sdb1: EFI partition
- sdb2: empty partition (old root partition, now formatted and empty)
- sdb3: old home partition
- sdb4: swap
- sdb5: Windows 10


The problem is that after turing on my pc:
- most of the time, I see the grub menu as usual and I can run Ubuntu/Windows correctly
- randomly, I get a "unexpected return from initial read" message, then the pc boots directly to Windows
- randomly again, I get a "device is not bootable error", then the boot process hangs.


In case of error, I simply need to reboot the pc with CTRL-ALT-CANC in order to load grub correctly.


I tried to modify the boot order from my bios menu, witout luck.


Anyway the whole thing is quite erratic, so I cannot reproduce it.


Any suggestion?

---

### Post by MAFoElffen on 2021-12-28
I have a few questions and suggestions...

Your laptop came out between 2014-2015... Have you updated to the latest UEFI BIOS firmware updates? That may cause it to be intermittent...

I replaced my DVD device on the Toshiba Laptop I am writing this to an option bay, and now went SSD, SSD, mSata... So I have some experience with that upgrade. I know from that upgrade, that I shopped for one that was not universal, but that was made for my brand and model of laptop. That the universals, sometimes have a bad fit/connection, with intermittent problems. My Laptop also has a screw hole. that if a drive bay "is used" to hold it in solidly. Not familiar if your model has that... So that is one question. The next would be if the optional drive bay was specifically made for your brand/model, or was it a universal?

Next would be if it is a named brand, recent model SSD and what generation of SSD. Gen 3?

Next would be, during a successful boot, to post the output of:
```

efibootmgr -v

```
Which will display the information on the efi boot files, and the boot order. The setting of boot order in the UEFI Settings menu will change the order of which device is serached first, but the order of preferred boot files are still set within the boot menu of the EFI partition.

---

### Post by matteo-dagord on 2021-12-28
> **MAFoElffen said:**
> I have a few questions and suggestions...


Your laptop came out between 2014-2015... Have you updated to the latest UEFI BIOS firmware updates? That may cause it to be intermittent...


I replaced my DVD device on the Toshiba Laptop I am writing this to an option bay, and now went SSD, SSD, mSata... So I have some experience with that upgrade. I know from that upgrade, that I shopped for one that was not universal, but that was made for my brand and model of laptop.
Next would be if it is a named brand, recent model SSD and what generation of SSD. Gen 3?



Hello
first of all, thank you for your answer and your suggestions.
More precisely, my model is a Toshiba Satellite l50-b-24x: I already checked for a bios update but I can't find any official download source.
Anyway, I installed the sdd as primary drive, then I put the old hdd into the caddy: I bought an universal model, but I'm pretty sure it isn't an hardware issue, since after booting the notebook works normally for hours, without errors, freezing or whatever. Moreover, I double checked the connections.


As for the sdd itself, I opted for a Crucial BX500 240 GB CT240BX500SSD1 after reading some reviews on the web, but I couldn't say which generation it is. 


By the way, this is the output of efibootmgr:


```

matt@Saturnus:~$ efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0000,0003,2003,2001,2002
Boot0000* Windows Boot Manager    HD(1,GPT,fa4bdd7d-b002-4bb6-81db-0987fa809ec9,0x800,0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c3655ac,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* Realtek PXE    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x0)/MAC(2c600c3655ac,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* ubuntu    HD(1,GPT,fa4bdd7d-b002-4bb6-81db-0987fa809ec9,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0004* Windows Boot Manager    HD(1,GPT,fa4bdd7d-b002-4bb6-81db-0987fa809ec9,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

Hope this is useful...

---

### Post by MAFoElffen on 2021-12-28
BIOS updates: [https://support.dynabook.com/support/modelHome?freeText=PSKTAU-0EV088&osId=3333785](https://support.dynabook.com/support/modelHome?freeText=PSKTAU-0EV088&osId=3333785)

Your UEFI boot order is currently:
Windows Boot Manager, Windows Boot Manager, Ubuntu, EFI Network, EFI USB Device, EFI DVD/CDROM

I'm thinking you are booting Ubuntu Via the EFI Boot menu, then Grub? But the primary/default boot is still going to Windows(?)

Your SSD is SATA 3 (6GB/s interface).

When it does have an error booting... what do you do to get it to boot? If you then do a reboot, does it successfully boot? Because you said this is an intermittent problem...

---

### Post by ubfan1 on 2021-12-28
From your efibootmgr output, I'd expect the Windows entries should have HD(2..., not HD(1 like the ubuntu entry on sda.  Suppose both the first two entries (Windows) are invalid, maybe the device or fallback bootloader is invoked at some point.  Check the size of the default /boot/efi/EFI/Boot/bootx64.efi against the shimx64.efi, grubx64.efi, and bootmgfw.efi to see which bootloader it is. Reorder the bootorder to put ubuntu first, and fix(?) the Windows entries.

---

### Post by tea for one on 2021-12-29
> **matteo-dagord said:**
> Anyway the whole thing is quite erratic, so I cannot reproduce it.
Any suggestion?

Not really wanting to throw a spanner into the works, I have to mention:-

Two disks and two operating systems is ideal when each OS is installed on its own disk.
Boot and Grub problems are eliminated when you choose the OS via the UEFI menu.

Dual booting is not a trivial exercise and your position is more complicated by using different disks for Ubuntu system files and Ubuntu user files.

---

### Post by oldfred on 2021-12-29
You show two Windows entries, one really Windows & the other grub.
```
BootOrder: 0004,0000,0003,2003,2001,2002
Boot0000* Windows Boot Manager    HD(1,GPT,fa4bdd7d-b002-4bb6-81db-0987fa809ec9,0x800,0x100000)/File(\EFI\Microsoft\Boot\[COLOR=#ff0000]bootmgfw.efi[/COLOR])RC
Boot0004* Windows Boot Manager    HD(1,GPT,fa4bdd7d-b002-4bb6-81db-0987fa809ec9,0x800,0x100000)/File(\EFI\ubuntu\[COLOR=#ff0000]grubx64.efi[/COLOR])WINDOWS.


```

Years ago for systems with defective UEFI, we would change Windows entry to grub like you have. But we may only do that now if single booting Ubuntu. Issue was Windows updates would overwrite grub entry & then you could not boot Ubuntu.
Since you also have ubuntu entry, I would delete 0004 in UEFI with efibootmgr.

Ubuntu's Ubiquity installer only installs boot files to first drive in system. Not sure why it would see HDD as first, but that depends on UEFI/BIOS.

With two drives usually best to manually partition so you have ESP - efi system partition on Ubuntu drive.
And then as per tea for one's suggestion, you can then have grub/shim installed to Ubuntu drive.

---

### Post by matteo-dagord on 2022-01-03
Hello again, and sorry for the late reply.
I can't understand what messed up the EFI partition: I started with a Windows 10/Ubuntu 18.04 dual boot on the "old" hdd, then I installed Ubuntu 18.04 on the ssd, simply following the graphical installer steps.
Since I'm the 99.9% of the time on the linux environment, I can easily give up Windows 10, if this can help.
By the way, in the last few days the notebook booted up regularly... I'm wondering what's going on.


> **MAFoElffen said:**
> BIOS updates: [https://support.dynabook.com/support/modelHome?freeText=PSKTAU-0EV088&osId=3333785](https://support.dynabook.com/support/modelHome?freeText=PSKTAU-0EV088&osId=3333785)


Thank you: I already saw that page but I didn't understand it was an official source. I'll give it a try.

> **MAFoElffen said:**
> 
When it does have an error booting... what do you do to get it to boot? If you then do a reboot, does it successfully boot? Because you said this is an intermittent problem...

When the error occours, I hit CTRL-ALT-DEL, then the notebook successfully boots.

---

