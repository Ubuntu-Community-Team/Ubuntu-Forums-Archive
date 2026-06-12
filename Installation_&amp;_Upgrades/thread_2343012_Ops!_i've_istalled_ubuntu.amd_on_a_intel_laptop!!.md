---
title: "Ops! i've istalled ubuntu.amd on a intel laptop!!"
date: 2016-11-12
forum: Installation &amp; Upgrades
---

### Post by pascale64 on 2016-11-12
The trouble with us "new to linux" and " once its installed dont touch", is that when we do need to do something new it all goes pear shaped!
I have brought a new laptop Aspire ES 15
And I have installed Ubuntu 16.04 AMD64 on legacy mode using a USB key burnt by Rufus.
The installation boots and runs, But what I would like to Know is, Will everthing be OK or should I download Ubuntu 384i (?)
and install this instead using the method described by debian for preparing a bootable usb key?

ALL help and advice greatly appreiciated.

Regards
Paul

---

### Post by mörgæs on 2016-11-12
The AMD and i (for Intel) in the ISO names are a steady source of confusion. They are a left-over from old times and should be abandoned. 

The only thing that matters is 32 or 64 bit.

---

### Post by pascale64 on 2016-11-12
Hi Thanks for your reply, So the amd and i side pose no problems as the 64 is right, But does the bios boot on Legacy represent a problem (eufi not recognised when usb installed)
regards
paul

---

### Post by Bucky Ball on 2016-11-12
AMD64 for _ANY_ 64bit processor, AMD or Intel. If you have a 64bit processor of either flavour you want the AMD64bit ISO.

In other words, if everything is working as it should, do nothing and enjoy. ;)

---

### Post by oldfred on 2016-11-12
Are you dual booting or only have Ubuntu installed?

There are some minor advantages to UEFI, and if dual booting much better to have all installs in same boot mode.
But if only booting Ubuntu probably not work changing from BIOS to UEFI, unless you want to.
And if drive is gpt partitioned, you may not have to reinstall Ubuntu, but just change boot loader from grub-pc(BIOS) to grub-efi-amd64(UEFI).

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 

I always found the history interesting on why it is AMD64. 
And it goes all the way back to 16 bit chips and customers not wanting single sourced vendor so Intel licensed AMD to make Intel compatible chips. And then licensed 32 bit chips that were 16 bit compatible. And then Intel wanted a total clean sheet 64 bit chip, but AMD created a 64 bit chip that was backwards compatible. Lots of legal wrangling and back & forth, but eventually Intel adopted AMD's version of 64 bit.

 [https://en.wikipedia.org/wiki/X86-64](https://en.wikipedia.org/wiki/X86-64)

---

### Post by pascale64 on 2016-11-12
Hi super moderateur
Thank you for you fantastic reply.
At the moment it is only single boot, but I would like to another linux os so Iwill be reading all your threads to find out more!> **oldfred said:**
> Are you dual booting or only have Ubuntu installed?

There are some minor advantages to UEFI, and if dual booting much better to have all installs in same boot mode.
But if only booting Ubuntu probably not work changing from BIOS to UEFI, unless you want to.
And if drive is gpt partitioned, you may not have to reinstall Ubuntu, but just change boot loader from grub-pc(BIOS) to grub-efi-amd64(UEFI).

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 

I always found the history interesting on why it is AMD64. 
And it goes all the way back to 16 bit chips and customers not wanting single sourced vendor so Intel licensed AMD to make Intel compatible chips. And then licensed 32 bit chips that were 16 bit compatible. And then Intel wanted a total clean sheet 64 bit chip, but AMD created a 64 bit chip that was backwards compatible. Lots of legal wrangling and back & forth, but eventually Intel adopted AMD's version of 64 bit.

 [https://en.wikipedia.org/wiki/X86-64](https://en.wikipedia.org/wiki/X86-64)

Many thanks again to all who have helped
Kind regards
Paul

---

### Post by pascale64 on 2016-11-12
I am sorry for my appalling English but I ome from Essex and now live in France:D

---

