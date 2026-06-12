---
title: "Unable to boot from USB after unsuccesful duel boot install"
date: 2019-11-03
forum: Installation &amp; Upgrades
---

### Post by silver-fog on 2019-11-03
On a HP laptop with 256 SSD and windows 10 installed. I was able to successfully create a live usb of Ubuntu 18.04.3 using Lili and boot up from said usb. Decided to partition the hard drive to install permanently. Setup seemed to complete gracefully and suggested I reboot. Upon reboot Windows immediately ran a diagnostic tool and "fixed a fragmented hard drive" or something similar. Now Windows programs occasionally crash due to memory write errors, and I am unable to boot from usb. Any attempt to do so results in several error messages "Failed to open \EFI\BOOT\mmx64 - Not Found; Failed to load image \EFI\BOOT\mmx.64.efi: Not found; Failed to start MokManager: Not Found; Something has gone seriously wrong: import-mok_state() failed; : Not Found"

BIOS settings are secure boot disabled, UEFI(IPv4 and IPv6) enabled. 

I did find some info suggesting to copy or rename grub.64 to grub.efi however I couldn't find any such file on my live usb and am not sure how I managed to boot up from it before and not able to now if that was the case so I felt that that was a red herring. 

Any help would be appreciated, keeping Windows would be ideal however I am not completely opposed to an Ubuntu only system. I've tried to include any relevant details but if additional info is needed I'd be happy to provide whatever I can.

---

### Post by oldfred on 2019-11-03
If you have installed you have mmx64.efi in /EFI/Boot & /EFI/ubuntu folders.

Many with that issue in flash drive, just copy grubx64.efi to /EFI/Boot and rename to mmx64.efi. 

If secure boot off file is not used. 
It is to manage keys which only are required if you have secure boot on, and have proprietary drivers which require you to use your own key.

---

### Post by silver-fog on 2019-11-04
Thanks for the info! Got it running again after I renamed it.

---

