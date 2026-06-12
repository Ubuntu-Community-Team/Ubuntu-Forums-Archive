---
title: "Ubuntu 18.04 Dual Boot, Automatic Repair Loop with Windows"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by gaupeng on 2019-12-20
Hi!
I recently dual-booted my laptop to have both Ubuntu 18.04 and Windows 10 on separate partitions on my only SSD drive on my laptop.
However, after a few days, while trying to boot Windows, the system would go into a loop of Automatic Repair, and would get stuck there. I am still able to access Ubuntu from the GRUB menu, but Windows always loops into the Automatic Repair-Restart cycle.

Things I have tried:
boot-repair: Output here: [https://pastebin.com/84UreJSK](https://pastebin.com/84UreJSK)
Disbaled Fast-bootup and Secure-bootup
Tried system recovery, but loops back to the same error.

Any help on this issue, would be gladly appreciated.

---

### Post by yancek on 2019-12-20
I this an upgrade from windows 7?  Your bootinfo output shows windows 7 boot code in the MBR.  Windows 10 generally does not do that as it uses UEFI and on a GPT disk such as you have, windows must be UEFI.  You have the windows EFI boot files in the appropriate partition.  I would suggest as a first step, you access the BIOS firmware and disable Legacy/CSM boot since both Ubuntu and windows EFI files are present.

Do you get any message from windows when it goes to the Automatic Repair?  Did you try running chkdsk from windows?

---

### Post by oldfred on 2019-12-20
Grub only boots working Windows.
That is then fast start up which sets hibernation flag must be off and NTFS cannot need chkdsk.

But most can still directly boot Windows from UEFI boot menu.

Windows turns fast start up back on with updates, so even if you originally turned it off, it may be back on.

---

### Post by gaupeng on 2020-01-01
I tried multple ways to fix this, including going through chkdsk, boot-repair and system recovery. Disabling fast startup after the issue occured was of no help. I instead reinstalled a fresh copy of Windows on its partition, but this time with fast startup disabled. Seems to work fine right now.
Thanks for the help!

---

