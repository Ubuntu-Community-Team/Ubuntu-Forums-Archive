---
title: "install Grub to Ubuntu partition (/boot/grub), not first (EFI) partition (/boot/efi)?"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by onlinespending on 2013-05-09
I am trying to dual boot Ubuntu 13.04 on my MacBook and despite selecting the same partition as the Ubuntu root partition to install the bootloader, it installs Grub to the EFI partition under /EFI/ubuntu/grubx64.efi. The EFI partition is being mounted by Ubuntu under /boot/efi. This whole way of installing the boatloader is causing issues with rEFIt.

Strangely I successfully did the same dual boot setup with an older MacBook and older version of Ubuntu and it did not install the bootloader on the EFI partition. It instead is under /boot/grub on the Ubuntu root partition.

How can I force Ubuntu to simply install Grub to /boot/grub rather than trying to install it as grubx64.efi on the EFI partition? Thanks!
[B]
UPDATE: Just to clarify I select /dev/sda4 to install the grub bootloader to (the same partition as my Ubuntu 13.04 root directory) and it ignores this. It installs it to the EFI partition instead (/dev/sda1). Is Ubuntu 13.04 broken with grub installation?[/B]

---

### Post by onlinespending on 2013-05-09
My workaround was to install without a bootloader (using LiveCD bootable thumb drive and running 'ubiquity -b'). I then manually installed grub2 by the following:

```
sudo mount /dev/sda4 /mnt
sudo grub-install --force --boot-directory=/mnt/boot /dev/sda4
```

That seems to have worked and rEFIt found the Ubuntu partition just fine.

---

### Post by onlinespending on 2013-05-10
Apparently I spoke too soon. I got the following warning when doing that grub-install from above (fyi: my partition is actually ext4)

```
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
```

Yet this seemed to work the first time I booted, though it's difficult to remember now, because Ubuntu is no longer bootable.

So the question remains the same and simple: how can you install grub2 to the Ubuntu root filesystem and not to the MBR/EFI, so that a program such as rEFIt finds the Ubuntu partition and is selectable to boot?

---

### Post by darkod on 2013-05-10
When you boot the cd/usb in uefi mode, it will install in uefi mode which means it will install grub-efi with the corresponding files in the EFI partition. I haven't heard of a way to avoid that, but haven't looked for it either. What usually refers to as grub2 installation/location, is basically just small part of the code, that in legacy boot systems goes to the MBR usually. Even if you install this code onto a partition, the grubx64.efi will still be copied to the EFI partition since that's part of the uefi installation.

What you could try is to boot the install media in legacy mode, because in that case it installs grub-pc (not grub-efi) which doesn't touch the EFI partition even if there is one.

But since this is Mac I have no idea if you can boot in legacy mode since Macs use gpt and uefi since long time ago I guess.

But what is the reason you are doing all this? Can you boot ubuntu later without a bootloader? Watch out for that.

PS. When installing grub you can also try this variation of the second command:
```
sudo grub-install --force --root-directory=/mnt /dev/sda4
```

Not --boot-directory. There is info you need to use --boot-directory with the latest versions but I'm still not convinced and --root-directory still seems to work (even better).

---

