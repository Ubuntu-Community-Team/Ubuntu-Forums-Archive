---
title: "I get grub shell on startup after installing Ubuntu 22 alongside Ubuntu 20"
date: 2023-08-23
forum: Installation &amp; Upgrades
---

### Post by heirdoyy on 2023-08-23
Hello all,

On my Thinkpad T480s, which originally had Windows installed, I installed Ubuntu 20, erasing all other operating systems and later, alongside the exising Ubuntu installation I installed Ubuntu 22. After installing Ubuntu 22 grub does not work as expected anymore: Instead of seeing the OS-Selection screen, I get the grub shell.

If I enter

```

set prefix=(hd0,msdos6)/boot/grub
set root=(hd0,msdos6)
insmod linux
insmod normal
normal
```

I get the OS-Selection screen, with Ubuntu 22 as the default option, which is exactly what I want to see on startup.

If tried to fix it with boot-repair, but this yielded no improvement. Here are the associated boot-repair reports:
Diagnosis before running boot-repair: [https://paste.ubuntu.com/p/qWwhCDt49P](https://paste.ubuntu.com/p/qWwhCDt49P)
Report from repair attempt: [https://paste.ubuntu.com/p/](https://paste.ubuntu.com/p/)

boot-repair showed me the following message: "Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (nvme0n1p3/efi/ubuntu/grubx64.efi file) !".
However I would like to get some recommendations before I start hampering with my boot setup, as I don't understand it very well. Do I need to use efibootmgr? If so, which partition do I need to specify?

In the UEFI boot priority menu I can see 2 entries for ubuntu, however it does not matter which one I select as top boot prio.

Any help is greatly appreciated :)

---

### Post by ubfan1 on 2023-08-23
I see two ESPs and a legacy boot using sda5 (the Ubuntu 20.04). Only one ESP is allowed per disk, but maybe the first one (sda1) didn't have the right flags/partition type so wasn't recognized.  How are you booting, into legacy or UEFI? It can work both ways, but fixing things might be different.  Check the settings in your BIOS.  Check the EFI/ubuntu/grub.cfg files in the two ESP and confirm that sda1 uses the sda5 UUID to pull in the maintained grub.cfg file (and sda3 uses sda6's UUID). Your disk is msdos partitioned, but that really makes no difference to Ubuntu, and will boot either way. Maybe delete the Windows boot from efibootmgr or BIOS settings if you can -- just confuses things.  I think after a failure, Lenovo will try the fallback EFI/Boot/bootx64.efi before the second item in the bootorder.  I had a w520, booting Win/Ubuntu legacy/gpt off internal disk and UEFI off a disk in the caddy (gpt), so the Lenovo settings allow you to have both, setting a preference of one to boot first (looks like your preference is UEFI, since the boot repair booted UEFI).  Eventually, I did convert the msdos disk to gpt (easy for you without Windows), but really, there's no need for that, unless you decide to start over.  In that case, I'd recommend using gpt partitioning.  Might try the EFI boot menu (F12 ?) at powerup, then select an Ubuntu entry, try both if more than one.  If you get into Ubuntu, you can use efibootmgr to clean up the bootorder.

---

### Post by grahammechanical on 2023-08-23
The boot partition (EFI system partition - ESP) is nvme0n1p3. It contains the necessary boot files. Open the motherboard's BIOS/UEFI settings utility and open the Boot menu and set the boot priority to nvme0n1p3. When you load into Ubuntu 22.04 run this command

```
sudo update-grub
```

That should put Ubuntu 20.04 into the Grub boot menu.

You seem to have the MBR partition table. This will limit the number of partitions to four unless a special partition (Called Extended) is created and then additional partitions can be created inside the extended partition. This is the situation with your setup.

There is a more modern partition table called GPT which allows us to have many more partitions. If you ever decide to wipe everything off and start afresh ... you can use GParted to give the disc a new partition table. Select GPT. When installing Ubuntu select Erase disc and install Ubuntu. The installer will create the partitions including the EFI system boot partition. It will most likely be the first partition. If you install another version of Ubuntu using the Something Else option make sure you direct the installer to put the Grub boot files in the EFI System boot partition.

Use the BIOS/UEFI setting utility to direct the motherboard to boot on the first drive. The boot process will then look in the first partition.

Regards

---

### Post by heirdoyy on 2023-08-24
> **ubfan1 said:**
> ... How are you booting, into legacy or UEFI? ...

Thanks a lot for your suggestions! Im booting in legacy mode. I only turned it off to run boot-repair, as it would show me an error otherwise.

---

### Post by heirdoyy on 2023-08-24
Your suggestions were very helpful! I managed to fix it, by setting fs_uuid in the grub.cfg in nvme0n1p1 (which seems to be checked first during boot) to the UUID of nvme0n1p6, where my new Ubuntu 22 installation is located. Now I get the OS Selection screen again and Ubuntu 22 is the default option.

Thank you all for helping me out. It makes me happy and means a lot to me to get such competent help for free even though I'm a stranger to you.

---

### Post by yancek on 2023-08-24
I reviewed your first boot repair but could not access the second one.  Part of your problem is that you apparently had a Legacy/CSM install at some point since the very beginning of the first boot repair shows Grub in the MBR.  That does not happen with an EFI install.  Another part of the problems which was pointed out above is that you have 2 EFI partitions which is not necessary and confuses things. 

The grub.cfg file in your original boot repair shows the following uuid in the grub.cfg file on partition 1.  If you scroll down to the blkid output on lines 160-167, you will see that that uuid does not exist.  The uuid for partition 6, 22.04 is:  a4f3e245-f58d-4749-8669-c45b19eb0005.  That is the uuid which showed on the EFI partition (partiiton 3) in the grub.cfg file.  Also note that on line 144, you see the * under the Boot column from the fdisk output.  This means it is the EFI boot partition

Apparently, you already had an EFI partition with the original Ubuntu and created a second one which was unnecessary.

---

### Post by heirdoyy on 2023-08-25
I guess that sums it up quite well. I'm fine though with the current situation (see post #5 on this thread) and don't feel competent to further hamper with my boot setup and will just erase the disk, next time I install a new ubuntu version. Thanks for your analysis.

---

### Post by yancek on 2023-08-25
Creating a second EFI partition was likely a big part of the problem.  If you are using just one version of Ubuntu, lot simpler.  If you have a blank disk, you create an EFI partition.   If you have an OS already installed (such as windows) don't create an EFI partition as there already is one and Ubuntu will not modify it except to create a separate ubuntu directory on the partition to boot its files.  It won't have any effect on the windows boot files.

---

