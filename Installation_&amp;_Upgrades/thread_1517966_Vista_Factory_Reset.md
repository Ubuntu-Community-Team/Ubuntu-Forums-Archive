---
title: "Vista Factory Reset"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by ruppalapati on 2010-06-25
Hi,
I installed Ubuntu  to dual boot with Vista that came with my Dell Inspiron 1420.
Dell had a partition where the Vista install could be restored to factory state when the laptop was purchased.

After installing Ubuntu, I see:
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31.14-generic (recovery mode)
Memory test (memtest86+)
Windows Vista (loader) (on /dev/sda3)
Microsoft Windows XP Embedded (on /dev/sda5)

I think the /dev/sda5 partition was the one that contains the Vista system restore information. And according to Dell documentation, I need to the F8 key at BIOS load time to make the laptop boot the restore partition.

However after the Ubuntu install, I cannot get the Factory Restore to start by pressing the F8. It worked before the Ubuntu install.

Can the gurus on this forum help me get to my state before I installed Vista. I want to be able to restore the laptop to the state before I installed Ubuntu.

Thanks for your time.

_raju

---

### Post by darkod on 2010-06-25
What happens if you try to boot the entry for /dev/sda5 from the grub boot menu?

---

### Post by ruppalapati on 2010-06-25
> **darkod said:**
> What happens if you try to boot the entry for /dev/sda5 from the grub boot menu?

I get a black/white screen with the title "Windows Boot Manager"
with a message: 

Windows Boot Manager has experienced a problem
File: \Boot\BCD
Status: 0xc0000098
Info: The Windows Boot Configuration Data file does not contain a valid OS entry

This before the Ubuntu install would boot up an embedded WinXP what would allow the Factory Reset Reinstall of Vista by hitting the F8 key at boot time.

---

### Post by darkod on 2010-06-26
If you want to go back to factory restore, you can remove grub2 from the MBR and install generic mbr there with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be warnings after the first command, just ignore them and run the second.

But this will make booting ubuntu impossible, grub2 will be deleted from the MBR. It should boot your system as it was before installing ubuntu and you should be able to use the F8 function again.

If you want to boot ubuntu again don't reinstall it whole. You just need to reinstall grub2 back. And you should have ubuntu cd at hand for troubleshooting if it doesn't work as expected.

---

