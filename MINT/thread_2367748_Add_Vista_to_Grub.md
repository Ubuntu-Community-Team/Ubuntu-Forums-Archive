---
title: "Add Vista to Grub"
date: 2017-08-02
forum: MINT
---

### Post by ManyBeers on 2017-08-02
My Gateway netbook has mint 18.1 installed on a 60gb ssd. Before I put in the ssd Windows Vista (which came on the netbook) was installed on a harddrive. So I removed the
harddrive installed the ssd and then installed Mint. So far so good. I then used Minitool Partition Wizard to clone or copy the Vista partition from the harddrive to the ssd behind Mint 18.1
I did this so I would not have to reinstall and reconfigure Vista (hours of work). I sudo updated Grub and it does offer the Windows bootloader as an option but when I select
Windows it obviously won't boot. Anybody know how to make Vista boot?

---

### Post by wildmanne39 on 2017-08-02
*Thread moved to **MINT**.*

---

### Post by oldfred on 2017-08-02
Generally you have to reinstall Windows.
Internally it has info on partition it is installed into and that info must match partition table. Start sector & size much match. Maybe cloning Windows, then shrinking it to make space after Windows would have been better.

Did you install into a primary NTFS partition with boot flag? You may need chkdsk and make sure it directly boots by temporarily installing the Windows boot loader to MBR. It may need other fixes, or may not be fixable.

Is not Vista obsolete and never was considered a good version of Windows? Users preferred XP or Windows 7.

---

### Post by ManyBeers on 2017-08-03
> **oldfred said:**
> Generally you have to reinstall Windows.
Internally it has info on partition it is installed into and that info must match partition table. Start sector & size much match. Maybe cloning Windows, then shrinking it to make space after Windows would have been better.

Did you install into a primary NTFS partition with boot flag? You may need chkdsk and make sure it directly boots by temporarily installing the Windows boot loader to MBR. It may need other fixes, or may not be fixable.

Is not Vista obsolete and never was considered a good version of Windows? Users preferred XP or Windows 7.

I installed it into unallocated space after Mint no boot flag

---

### Post by yancek on 2017-08-03
Windows won't boot unless it's boot partition is marked active and the partition with the boot files is a primary partition.  If you put windows after Mint, it may not be on a primary.  The only way for use to help on that is if you post the output of:  sudo fdisk -l  (run from Mint).

---

### Post by ManyBeers on 2017-08-03
> **yancek said:**
> Windows won't boot unless it's boot partition is marked active and the partition with the boot files is a primary partition.  If you put windows after Mint, it may not be on a primary.  The only way for use to help on that is if you post the output of:  sudo fdisk -l  (run from Mint).
It is Gpt and I made it a primary partition. The keyboard is currently not working butI will post back with fdisk -l when I get it fixed

---

### Post by oldfred on 2017-08-03
Windows only boots from gpt with UEFI.
Windows only boots from MBR(msdos) with BIOS.
If you converted drive to gpt your Windows will not work at all unless your Vista was one of the extremely few that was UEFI.

---

### Post by ManyBeers on 2017-08-03
> **oldfred said:**
> Windows only boots from gpt with UEFI.
Windows only boots from MBR(msdos) with BIOS.
If you converted drive to gpt your Windows will not work at all unless your Vista was one of the extremely few that was UEFI.
I got confused the netbook is mbr and there is only 4 partitions and all are primary
I was referring to my desktop when referring to GPT ...sorry about that.

---

