---
title: "Installed on USB disk, but GRUB got installend in internal"
date: 2021-04-17
forum: Installation &amp; Upgrades
---

### Post by enboig on 2021-04-17
I have a windows laptop without admin privileges. In order to use linux I booted with a pendrive, and installed ubuntu on a second usb disk.
During install I checked grub install to the USB disk (I am pretty sure), and in bios set first boot to USB.

Now when I boot with the USB everything works as expected, but if I remove the USB I get a grub error.

So my question is: how to remove grub from windows disk (without windows administrative rights).

After fixing this I hope ubuntu will boot correctly, if not any hint to fix it is welcome.

Thanks

---

### Post by The Cog on 2021-04-17
There was a long thread about this recently, but I can't find it now. The upshot is that there is a long-standing (years) bug in the Ubuntu installer in that it completely ignores the drop-down setting that asks where to install the bootloader, and always installs it on the hard drive. Apparently, the only way to make it put the bootloader elsewhere is to use a partition editor to deactivate the EFI partition on the hard drive at the right place in the install process (when it asks for your username perhaps but I don't remember for sure), and manually create and activate an EFI partition on the pendrive before continuing the install. Then re-activate the hard drive EFI partition when the installation is finished.

I suspect you will have to use windows tools to undo the damage it's done.

---

### Post by enboig on 2021-04-17
Ok, thanks.

I have changed boot options in bios, and *eventually* some windows upgrade will remove ubuntu from harddisk

Second option will be a liveUSB with persisten partition

---

### Post by CelticWarrior on 2021-04-17
> [COLOR=#000000]I have changed boot options in bios[/COLOR]
Correct, except that what you call BIOS is actually UEFI.

> *eventually some windows upgrade will remove ubuntu from harddisk*
It won't.
With BIOS/MBR in the past some Windows feature updates, due to an "optimization", didn't consider Linux partitions and even re-wrote the Grub bootloader back to Windows bootloader.
This never happened with UEFI/GPT. And in UEFI bootloaders co-exist in the EFI partition.

So, unless you want your Ubuntu installed in the external USB drive to be "portable", the result of what The Cog commented is perfectly usable as long as you change the OS selection in UEFI accordingly: Leave it as "Windows Bootloader manager" whenever the USB drive isn't connected and when you want to run Ubuntu simply connect its drive and use the OS selection "Ubuntu" that will give you the Grub menu. As long as you keep the drive connected you'll be able to boot Ubuntu or Windows from Grub menu. Disconnect the drive then change it back to "Windows". 

You don't need to complicate things that are simple. Using a live session with persistence is a worse option for no reason at all.

Now, if you need that USB installed Ubuntu to run on other UEFI computers, then you need it to have a) an EFI partition and b) install the bootloader. It can be done easily with Boot Repair (advanced options). If you want it to boot in BIOS mode you also need a small unformatted bios_grub partition (in lieu of MBR) and install the old bootloader as well.

---

### Post by ubfan1 on 2021-04-17
Do add yourself to the launchpad bug 1396379 to turn up the heat and maybe get this fixed.  The USB case is even older, 1173457, but got supersetted by 1396379, losing all the affected users in the process. Setting up the external disk for booting is simply a matter of copying all the internal disk EFI files to the USB disk EFI -- they should work and boot the device or Windows (but probably not windows if moved to another machine).  Then remove the 'ubuntu" entry in the UEFI boot entries, change the device bootloader (EFI/Boot/bootx64.efi) back to the saved windows one (bckbootx64.efi (?), and put the USB first in bootorder.  You will then have a device which boots Windows without the USB, and boots grub with a choice of Ubuntu or Windows when the USB is attached.

---

### Post by ajgreeny on 2021-04-17
I believe, though I have never done this, that Lubuntu, which now uses the calamares installer instead of ubiquity will allow the installer to choose where to put the grub bootloader and then actually carries out those instructions, unlike ubiquity which asks the question but then ignores what you have told it to do.

As I say, I have not tried this personally, as I've tried Lubuntu only as a VM using KVM/QEMU, never on a separate disk, USB or internal, so my information could be incorrect, and eventually I decided that LXQt DE was not for me anyway so that VM has now gone.

---

### Post by kurt18947 on 2021-04-18
> **enboig said:**
> I have a windows laptop without admin privileges. In order to use linux I booted with a pendrive, and installed ubuntu on a second usb disk.
During install I checked grub install to the USB disk (I am pretty sure), and in bios set first boot to USB.

Now when I boot with the USB everything works as expected, but if I remove the USB I get a grub error.

So my question is: how to remove grub from windows disk (without windows administrative rights).

After fixing this I hope ubuntu will boot correctly, if not any hint to fix it is welcome.

Thanks

I've created full installs on flash drives and had problems similar to yours. I took the blunt force tack and removed the hard drive. On my laptops (older Thinkpads) that's pretty easy. On newer machines it may not be easy or even possible. Remove/unplug the hard drive, plug a live USB in and boot from that. Plug a target USB drive and install to that. Replace the hard drive and use the "select the boot device" f key to select the desired O.S. Not elegant but it works. I also have a dual boot laptop and desktop. I've found that as long as I have Windows installed before Ubuntu that machines dual boot with no issues. Maybe I'm just lucky but that would be out of character for me.

---

