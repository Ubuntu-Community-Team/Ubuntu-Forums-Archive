---
title: "can't log into ubuntu 14.04 in a dual boot system with win 8.1"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by pmaini90 on 2015-05-10
Sorry, for I am not very well acquainted with system level details for linux.

I have a dual boot system with ubuntu 14.04 and windows 8.1. I need both. I am not able to access Ubuntu from the boot menu. My system is HP envy 15 j048tx.
The system would directly log into windows. However I can press F9 and select ubuntu which is not what I want to go ahead with. Both the OS are UEFI. Ubuntu was installed with fast boot and secure boot off. I tried fixing the grub with boot-repair.
The pastebin link is: [http://paste.ubuntu.com/11061623/](http://paste.ubuntu.com/11061623/).

Any help would be appreciated.

Please let me know if any other information is needed.

---

### Post by mattharris4 on 2015-05-11
New HP computers are designed to foil any attempt to use an OS other than Windows with it.  However, there is a complicated work-around from moderator oldfred.  Here are the instructions:  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) .  The pertinent instructions are about half-way down the first post.  I wish a moderator would put a sticky up on the main Ubuntu Forums screen about this recommending that people not purchase a new HP computer with the intent of installing any form of Linux on it as well as the page where people can download Ubuntu/Lubuntu/etc. so people know the situation -- preferably before purchasing a new computer.  Maybe that would cost HP enough sales that they rethink their obvious Windows only policy.

---

### Post by oldfred on 2015-05-11
The copy of grub or shim to be bootx64.efi is required for more than HP. Sony many Toshibas and others also required that fix to boot a hard drive entry not the ubuntu entry in UEFI. They modify UEFI to only boot Windows by description.

It seems to be very common and Ubuntu has a position paper.
 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by mattharris4 on 2015-05-11
^  I am aware of the issue cropping up with Sonys and some Toshibas.  Since HP is the worst offender due to the massive number of computers they sell, their wide use of this UEFI and the OP having one I kept my discussion to that brand here.  Fortunately for Linux users Sony didn't sell many computers (and no longer manufactures or sells them).  As for Toshiba I am having trouble ascertaining if the offending UEFI is only on some models being manufactured today, if they only did this for a few months and quit doing this recently or if they started attempting to force Windows use on all of their computer models that started manufacture after some certain date and continue to do so today.  Someone did post here that he bought a new in the box Toshiba without any OS on it whatsoever recently (and successfully installed a Linux OS on it), the only reason you would purchase a computer without any OS is to put Linux on it so them installing a Windows-only UEFI on those computers would be beyond stupid (actually it is beyond stupid anyway, whoever made the decision to attempt to force Windows use at these companies should be drawn and quartered).  As you probably know I have a year old Toshiba laptop that took Lubuntu without this issue cropping up and it does have a UEFI and Win 8.1 from the factory.

---

