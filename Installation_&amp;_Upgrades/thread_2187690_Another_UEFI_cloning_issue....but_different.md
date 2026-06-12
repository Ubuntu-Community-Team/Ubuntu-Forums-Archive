---
title: "Another UEFI cloning issue....but different"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by applerock79 on 2013-11-13
To finish an earlier post:
Managed to clone my UEFI motherboard (to same hardware) with Ubuntu 12.04 using Clonezilla.
FYI: Trick was I needed newest version of Clonezilla and needed to boot the clonezilla CD with UEFI, in BOTH source & destination PCs. Also needed to Install Ubuntu with boot CD in UEFI mode.
Worked like a charm.....several times. :P

BUT......

Now I wish to use that same clone file and put in on a slightly older PC **without** UEFI. 
Tried several scenarios on booting Clonezilla, re-cloning without UEFI, and so on. It just won't boot on destination PC. Even tried Boot Repair CD afterwards with no luck.

Starting to think this isn't even possible, and may have to redo an entire PC, from scratch, starting with a fresh install of Ubuntu 12.04 and modify (to make like Source PC). This would be a royal pain, but may be the only way to go.

My initial though was the older PC wouldn't even care about the UEFI clone file, and just restore as usual, obviously incorrect.

So, any way to clone a new UEFI PC (with UEFI enabled......it was the only way Ubuntu would install) to and older BIOS PC?

---

### Post by oldfred on 2013-11-13
When you have a UEFI system it only boots in UEFI mode, not BIOS mode.

Windows only boots from a gpt drive with UEFI, but Ubuntu will boot from a gpt drive with either UEFI or BIOS. So it may be possible to convert your UEFI clone to BIOS boot by adding a tiny 1 or 2MB unformatted partition with the bios_grub flag. That is required for grub to correctly install to the MBR of a gpt drive. Then use Boot-Repair to convert install from UEFI to BIOS by un-installing grub-efi(UEFI) and installing grub-pc(BIOS).

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

I am not a fan of cloning to a new system. I really think it is easier just to install. You can copy your /home before hand if a separate partition or afterwards to have all your settings. Only a few hardware settings are in /etc and most of those are unique to each install. You may want to extract a list of installed appliations and reinstall, if slow Internet and lots of apps that may be the only real disadvantage of a new install.

---

### Post by applerock79 on 2013-11-13
Yes, that worked! 
thank you. Saved me a lot of work rebuilding and reconfiguring for a public kiosk PC. (several)

---

