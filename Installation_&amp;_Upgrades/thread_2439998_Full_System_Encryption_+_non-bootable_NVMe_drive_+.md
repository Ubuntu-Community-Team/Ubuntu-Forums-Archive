---
title: "Full System Encryption + non-bootable NVMe drive + bootable USB drive"
date: 2020-04-04
forum: Installation &amp; Upgrades
---

### Post by krisztian_andre on 2020-04-04
Hi Everyone,

I have system that is unable to boot from NVMe drive and am trying to install 18.04 on the NVMe drive with full disk encryption using a USB drive to boot from following the Manual Full System Encryption guide at [https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption).

I created GPT partition tables on both drives, an EFI partition on the USB drive and a system partition on the NVMe drive and installed Ubuntu on this setup following the guide.

When the system boots the USB drive shows up as a UEFI boot source in the boot menu, grub loads then I get the following error message:

error: no such cryptodisk found
error: no such device: SOMEUID
error: no server is specified
error: you need to load the kernel first.

The grub ubuntu boot script consists of the following:

setparams: 'Ubuntu'

  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
  insmod part_gpt
  insmod cryptodisk
  insmod luks
  insmod gcry_rijndael
  insmod gcry_rijndael
  insmod gcry_sha512
  insmod lvm
  insmod ext2
  cryptomount -u SOMEUID
  set root='lvmid/SOMEUIDPATH/SOMEOTHERUID'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint='lvmid/SOMEUIDPATH/SOMEOTHERUID'
  else
    search --no-floppy --fs-uuid --set=root SOMEUID
  fi

How can I diagnose this issue?

Best regards,
Kris

---

### Post by krisztian_andre on 2020-04-05
Hi Everyone,

I managed to solve it. The problem was that the nvme modules were not loaded by grub nor present in the EFI partition. With /boot being created on the NVMe drive, it the initrd image couldn't be loaded. 

Since I don't know how to add modules to an EFI setup I modified the script in the original guide to be able to create /boot on a separate physical partition which I placed on the USB drive as well.

I will contact the author of the guide and will ask him to include my version of the script. I have also attached the file to this thread. Please note that my version requires you to label and name the separate boot partition as "boot" and it does not allow for separate per physical partition passphrases. This can be changed easily if needed.

Please note that the drives will only work if they have GPT partition tables. Otherwise you won't be able to properly name and label them which is required by the script.

Best regards,
Kris

---

