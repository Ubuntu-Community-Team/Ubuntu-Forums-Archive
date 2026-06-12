---
title: "install only to USB HDD having GPT"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by aspergerian on 2014-03-25
Perhaps the following will help clarify installation to a GPT USB HDD. My previous posts of a similar topic had intermingled te topic: howto install only to sda. Although I have successfully installed Xubuntu 12.04 to a 320 gb USB HDD, that HDD is not GPT. The 1-TB has its own power and would enable reduced power use by the dv7 when running Xubuntu.

Thus, as a next step, I hope to install Xubuntu 12.04 (or newer, if necessary) to the 1 TB USB HDD which seems to have been converted to GPT (See image).

I intend to redo all major partitions currently on the HDD (See other image), and if the GPT-based installation works, I'd like to have first main partition be /, second main partition to be /home, third main partition to be nfts, fourth main partition to be swap. (25gb, 50gb, 50gb, 12 gb, respectively). I intend at this stage (ie, of installation) to leave as unallocated the rest of the external HDD (if so doing is allowable at this point).

This USB HDD installation will be run usually from an HP dv7, occasionally from an HP G71. Neither is UEFI.

Questions before I use Gparted to alter the USB HDD's current partitions:
-Does my proposed partitioning scheme seem workable?
-If not, what needs be done to correct the GPT- and main-partitions?

---

### Post by fantab on 2014-03-25
I am assuming that by USB HDD you mean internal HDD or is it an External HDD?

Will you be dual booting Windows and Linux?

> This USB HDD installation will be run usually from an HP dv7, occasionally from an HP G71. Neither is UEFI.

This will be tricky because if you install Ubuntu in one system then if the specs of another PC are different then OS on HDD will not boot, especially if Graphics are different on two systems.

If both the Laptops are BIOS and you want to use GPT, then:
1. Windows will only boot from GPT if the machine is equipped with UEFI. So it won't be possible to boot Windows from GPT HDD in a BIOS system.
2. To be able to boot Linux/Ubuntu from GPT HDD in a BIOS system you will need to create a small partition of about 10-20Mb- unformatted- with 'bios_grub' flag. Without this partition linux will not boot on BIOS with GPT.
3. If this is an External HDD then make sure that GRUB (Bootloader) is installed to the USB HDD and not on the internal HDD, which is where Grub will install by default.

Partitioning is a very personal, however the SWAP of 12gb is bit too much if you don't hibernate your OS. If you 'hibernate' then SWAP size should be equal or more than your RAM in GiB and not Gb.
2gb swap should be plenty if not using hibernate function.

---

### Post by ubfan1 on 2014-03-25
If you're going to go gpt, why not just put on a 300M (left empty) partition for future UEFI machines.  I think the bios_grub partition can be smaller, 1M is what I've heard -- core.img is only 27k, and that's the only thing dumped there AFAIK.

---

### Post by aspergerian on 2014-03-26
Background: oldfred and sudodus helped me extensively when the challenges were more complex ([here]("http://ubuntuforums.org/showthread.php?t=2204995") & [here]("http://ubuntuforums.org/showthread.php?t=2208266")). Also helpful is [this]("https://help.ubuntu.com/community/DiskSpace").

My goals (now using an external USB HDD with GPT) is to be able to boot into Xubuntu without modifying the HP dv7's MBR and to reduce power use by the dv7 (since the 1-TB drive has its own power). 

The dv7 boots from USB ports as tested with 3 flash drives from OSDisc (Knoppix, PCLinuxOS, Xubuntu 12.04.4), boots from a 32gb flash onto which 12.04.3 was installed by me using an Acer 1410 netbook with an external HP DVD/CD drive, and most recently boots from a 320 gb USB-powered USB HDD (also installed via 1410).

Yesterday I re-partitioned the 1-TB USB (external) HDD, added a bios_grub partition (see attached image), and seem to have retained GPT (attached image).

Today or tomorrow I'll install Xubuntu 12.04.3 to 1-TB HDD with GPT and see if it boots in 1410 and in dv7.

---

### Post by fantab on 2014-03-26
I don't see the 'bios_grub' flag anywhere in the gparted screenshot... without the said flag it won't work. Also, though 1Mb is enough, it will be good idea to make it 10Mb, after all its a 1Tb disk. We don't want to get into a situation where we run out of space and face boot issues.

And keep the '[nomodest]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option handy when you try the installed xubuntu on different computer... Different graphics can cause 'black screen'.

---

### Post by sudodus on 2014-03-26
I agree with the tips by *fantab* and *ubfan*.

Maybe you get some useful tips from the following link describing how to make a system that boots in UEFI mode as well as in BIOS mode.

[Portable installed system booting from UEFI & BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

---

### Post by oldfred on 2014-03-26
The bios_grub partition must be unformatted and have bios_grub flag if created with gparted or ef02 with gdisk.

Even though I do not have UEFI, I leave space for an efi partition, so in the future I do not have to totally reformat to add an efi at the beginning of the drive:
```
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          976895   477.0 MiB   EF00  EFI System
   2          976896          978943   1024.0 KiB  EF02  
   3          978944        29650943   13.7 GiB    8300  sys
   4        29650944        60532735   14.7 GiB    8300  sys

```

---

### Post by aspergerian on 2014-03-28
Almost solved.

Yesterday, I used Acer 1410 netbook with USB DVD/CD player by HP and installed Xubuntu 12.04.3 to the 1-TB USB HD with GPT. I then reset 1410's bios boot sequence, and the newly installed system booted from the 1-TB HDD. I then installed all ~203 updates that were recommended. Using 1410 this way on a 320gb USB-powered USB-HDD (external) had previously created a system that would USB-boot my HP dv7. Yesterday, I then moved the 1-TB to the dv7 and, by golly, the dv7 booted Xubuntu from the 1-TB HDD with GPT. 6 more updates were offered, including newer kernel ...60. These updates were installed. After restart, the dv7 would not boot from the 1-TB HDD.

Up to this point I had allowed the EFI partition to remain as FAT32, so I used Gparted and removed that formatting. dv7 still would not boot from dv7 (although it had done so earlier). So I used boot repair disk, selecting advanced options because I feared that recommended option might alter my dv7's MBR. Repair proceeded, but dv7 would not boot. 

At this point I re-installed 12.04.3 to the 1-TB HDD and did so using the dv7. Nonetheless, the dv7 still would not boot from the 1-TB drive. So I returned the 1-TB HDD to the 1410 and that computer booted from the 1-TB HDD still having GPT and did so via the Xubuntu the dv7 had installed.

Amidst the aforementioned sequence, I created two boot-repair reports ([here]("http://paste.ubuntu.com/7163634/") & [here]("http://paste.ubuntu.com/7164486/")).

Boot-repair disc offers a number of options I haven't tried and I remain wary of boot-repair's recommended fix because it may alter MBR on dv7 (sda). The fact that the dv7 booted once from the 1-TB GPT HD suggests that there is a solution.

---

### Post by oldfred on 2014-03-28
As long as you tell Boot-Repair it is an external drive, it will only reinstall grub to the MBR of the external drive. If not, it does install grub to all drives which I do not like.

When you said it did not boot, what happened?
Grub menu also shows a Windows boot, but that would not work on other system without some changes.
And you may have different video between systems and need different boot parameters. 
What video chip is on both systems and is it the same.
You also have to boot in BIOS mode if your other system is UEFI.

You actually can configure a system to boot in UEFI or BIOS from one drive. Sudodus posted directions in post #6 above that worked on his system. That was a flash drive but would be the same procedure.

---

### Post by aspergerian on 2014-03-29
The replies are appreciated.

I should have made clear that the HP dv7 laptop with internal CD/DVD boots into Windows 7 when the 1-TB GPT HDD with Xubuntu 12.04.3 installed is connected to a USB port in the dv7. Although and however, the first time the dv7 was booted from the 1-TB GPT HDD, the dv7 booted into Xubuntu, but always since installing Xubuntu updates to the 1-TB HDD, the dv7 boots into Windows.

Remarkably, when the 1-TB HDD is connected to the Acer 1410, the Xubuntu on the 1-TB GPT HDD boots appropriately. Seems that MBR/bios_grub are no longer functioning properly when the 1-TB HDD is connected to the dv7.

In contrast, the dv7 USB-boots into Xubuntu 12.04.3 via a 32 gb flash and via a 320 gb USB-HDD (both installed via the 1410). Also, a Xubuntu 12.04.4 flash from OSDisc boots the dv7. Thus, Xubuntu 12.04 versions have appropriate video drivers for the dv7.

There is at least one more option I dare try with disc-repair CD run from the dv7's internal CD/DVD while the 1-TB GPT HDD is connected.

Is it possible that a /boot partition should be added to the 1-TB GPT HDD, then a re-install? If so, what size should that partition be? Or with a bios_grub partition already present, would adding a /boot partition be problematic?

---

### Post by oldfred on 2014-03-30
Some old computers need /boot due to BIOS limits. Also systems with RAID or encrypted LVM may need a /boot. Otherwise most systems do not need a /boot partition and it just adds another partition to keep track of how full it is.

Did you change default boot order on dv7?

Run a BootInfo report with external drive on dv7. If you cannot boot use live installer to run the BootInfo report.

---

