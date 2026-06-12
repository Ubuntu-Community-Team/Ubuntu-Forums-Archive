---
title: "Install with UEFI?"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Koffeehaus on 2012-11-13
I have an X-series Asus laptop which I just bough about a month ago. I want to dualboot Ubuntu - Windows.

I can easily access LiveUSB with both UEFI enabled and disabled. I heard that there were problems with UEFI, so I disabled it. After I've installed the system I couldn't access it. It just boots to Windows straight.

Another unusual thing, that never happened to me before was that the partition editor wanted me to create a BIOS reserved area, which I did, but not at the beginning of the table.

Any ideas how to access the Ubuntu partition?

As far as I can guess both Windows and Ubuntu have to be both of the same type of boot, either Legacy or EFI. This is not the case of what I have now. So, if I reinstall Ubuntu in UEFI mode that correlates with my Windows type, will I then be able to boot into it?

I have a constraint, my laptop doesn't have a CD ROM, so I cannot reinstall WIndows, nor can I move around the Windows recovery partition.

This is the boot-repair report :

[http://paste.ubuntu.com/1354254/]("http://paste.ubuntu.com/1354254/")

---

### Post by darkod on 2012-11-13
I am not using uefi and staying away from it, but from what has been mentioned here, most uefi issues happen exactly the way you did it, by installing ubuntu in legacy mode.

You should have booted the stick in uefi mode and install, it would have been fine (in most cases).

The bios_grub partition it asked for is because of the gpt partition table. In gpt the MBR is smaller than in msdos so grub2 needs a bit of extra space and it needs the bios_grub partition.

---

### Post by oldfred on 2012-11-13
You have to have either both systems in BIOS mode or both in UEFI mode to dual boot. Windows only boots from gpt partitioned drives with UEFI, so you need to have Ubuntu in UEFI mode.

The install CD or flash drive has two modes to boot one UEFI and the other legacy/BIOS/AHCI or .. How you boot installer is how it will install. So you need to boot installer from UEFI menu in efi mode to do a UEFI install.

But Boot-Repair has a function to uninstall grub-pc (BIOS) and install grub-efi. It then updates fstab and runs the updates to get grub installed to efi partition. Grub2's os-prober also has a bug that finds the Windows, but creates the BIOS chain entry not an efi entry. Boot-Repair will also add a correct efi chain entry for Windows. So Boot liveCD in UEFI mode and run Boot-Repair.

---

### Post by Koffeehaus on 2012-11-16
> **oldfred said:**
> You have to have either both systems in BIOS mode or both in UEFI mode to dual boot. Windows only boots from gpt partitioned drives with UEFI, so you need to have Ubuntu in UEFI mode.

The install CD or flash drive has two modes to boot one UEFI and the other legacy/BIOS/AHCI or .. How you boot installer is how it will install. So you need to boot installer from UEFI menu in efi mode to do a UEFI install.

But Boot-Repair has a function to uninstall grub-pc (BIOS) and install grub-efi. It then updates fstab and runs the updates to get grub installed to efi partition. Grub2's os-prober also has a bug that finds the Windows, but creates the BIOS chain entry not an efi entry. Boot-Repair will also add a correct efi chain entry for Windows. So Boot liveCD in UEFI mode and run Boot-Repair.

I've installed Ubuntu in UEFI mode and it works fine now. Now I can select the partition I want to use by pressing ESC at computer startup (I would say BIOS, but I am not sure anymore).

But now, when I boot Ubuntu, I still have the GRUB, and if I choose Windows from the GRUB menu, it doesn't work. Do I need this GRUB at all if I use UEFI?

---

### Post by darkod on 2012-11-16
I don't think so. UEFI should have its own "boot manager", probably what you are seeing when pressing Esc.

I think ubuntu's os-prober still has a bug and tries to create entry for win7 like the old legacy way, even though UEFI boots differently.

Check the uefi boot manager and if it can boot both win7 and ubuntu without problems, you can consider disabling os-prober in ubuntu. That will remove the win7 wntry from grub2. You can disable it with:
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

That should leave only ubuntu in the menu effectively hiding the menu because it doesn't show when there is only one OS.

---

### Post by YannBuntu on 2012-11-16
Hello

> **Koffeehaus said:**
> This is the boot-repair report :

[http://paste.ubuntu.com/1354254/]("http://paste.ubuntu.com/1354254/")

blkid bugs with your configuration, and this makes Boot-Repair unable to work.
I created a bug report: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1078635](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1078635)

---

### Post by oldfred on 2012-11-16
If you are using UEFI/BIOS or one time boot key to choose you can hide or reduce time grub menu is shown, but you have to have grub to boot Ubuntu.

But you can add the Windows efi entry to the menu and then just boot Ubutu and choose which system to boot from the grub menu.

If booting Windows most of the time you may want it first in menu, or leave it last if you do not care.

Since grub is till creating incorrect entries with its os-prober we will turn it off also, you can turn it on again when they fix bug or if you add other operating systems, but otherwise would not need it.

In /etc/default/grub I added this, change to false to run it again or delete line:
gksudo gedit /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=true
```or turn off executeable bit +x to turn back on
sudo chmod a-x /etc/grub.d/30_os-prober

Copy entry below into 40_custom.
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

```

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```If you want Windows first in grub menu you can copy 40_custom to 06_custom before editing and then edit 06_custom with the Windows boot stanza. Be sure you have included the few lines at the top of 40_custom.

sudo cp  /etc/grub.d/40_custom  /etc/grub.d/06_custom
Then edit like above to add boot stanza.

Boot-Repair is a lot easier. :)

---

