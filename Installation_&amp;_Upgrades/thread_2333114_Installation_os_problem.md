---
title: "Installation os problem"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by sbshaikh on 2016-08-07
On showing availability of 16.04 LTS operating system, I tried to install but due to electricity problem it could not be completed. Now my laptop is not started and screen showing message as 'Kerenal System  disabled' "Unknown block.."

What I should do ...so as to resolve the problem..

---

### Post by oldfred on 2016-08-07
Probably easiest just to reinstall.

You will have to get into UEFI or BIOS to select boot. 

And flash drive or hard drive in system may also need chkdsk for NTFS, or fsck for ext4 partitions as abnormal shutdown often corrupts system. 

If dual booting with Windows, use your Windows repair/recovery disk to run chkdsk and make other repairs to Windows.

For Ubuntu the live installer will also work as live system to make repairs.

---

