---
title: "Dual boot Grub not finding windows bootmgfw.efi"
date: 2022-06-01
forum: Installation &amp; Upgrades
---

### Post by aimjy on 2022-06-01
Hi,

I recently upgraded my computer to use 2 nvme SSDs, a 970 evo (500GB) and 980 pro (1TB). The idea is to install windows on the 970 evo, and ubuntu on the 980 pro to dual booth. After some trial and error (had lots of issues during installation, more details at the end) I managed to have both systems installed.

However when booting into Grub, I can see proposing me the windows partition, but when chosen I get the following error:
´´´
error: no such device: 4A5D-AB99.
error: file `/efi/Microsoft/Boot/bootmgfw.efi' not found.

Press any key to continue...
´´´

I did create a boot-repair report: [https://pastebin.ubuntu.com/p/tFxhKJ9VDK/](https://pastebin.ubuntu.com/p/tFxhKJ9VDK/) 
And this is the one after I tried to run the recommended repairs: [https://pastebin.ubuntu.com/p/7vdvQxqkkg/](https://pastebin.ubuntu.com/p/7vdvQxqkkg/)

Unfortunately it did not solve the issue. Issuing `sudo os-prober` and `sudo update-grub` does find the windows partition but did not solve the Grub issue. (Both OS's seems to run with an efi bootloader, so I guess it's not a mismatch issue either...)

Now the weird behaviour, is that when I first go into the UEFI set-up, then open Grub, then it detects windows and runs fine. I can also run windows from the UEFI directly as well. So a hypothesis I had, is that the nvme drive, which ubuntu is on, runs twice as fast and thus leaving no time to the other driver to be mounted on time?

Thanks a lot for your help!
Aimjy

*The issues during instalations if it can be relevant to this issue.
- I first installed ubuntu on the big nvme ssd, but the for some reason windows installation kept having issues, error code: 0xc000000e. Again some weird behaviour: it wouldn´t boot (even directly), but after a stop at the UEFI, then it would boot as well.
- I swapped the nvme drives on the motherboard (having read windows can be picky on the apparition order of the drivers), but only let the nvme for windows and installed it on, which worked stably.
- Adding back the other nvme drive, tried to install ubuntu on it. I kept having crashes from the ubuntu installer with segmentation faults. Tried multiple USB sticks, and different versions as well (22.04 and 20.04) with no luck. (Tried multiple parameter in the UEFI-BIOS changing AHCI to RAID, disabling fast-boot, with and without CSM...)
- I decided to update the BIOS of my motherboard (asus z390-a), then the installation did finally succeed with no crash during instalation and no initramfs corrupted at boot. (Which already feels as a weird solution, but yeah...)
- Now we are at this issue, were Grub, which works sometimes..., does not want to boot into windows.

---

### Post by oldfred on 2022-06-01
Have you also updated NVMe firmware?
I had to download bootable ISO from Samsung for my NVMe drive. It was unique to my model.
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is for Windows.

while Ubuntu should be using UUIDs, often changing drive order confuses things.
You normally need ACHI for both Windows (needs driver) and Ubuntu.

Is Windows fast start up off? Windows updates may turn it back on.

---

### Post by aimjy on 2022-06-02
Hi oldfred,

I've noticed the bios magically (or I did) changed the fast boot back again. Disabling it back, fixed the grub issue... I would assume the bios tries to load the boot drive first to get into the OS asap, while the other drives are not properly loaded yet.

Thanks for sharing about the drives' firmware. I did not think about that at all. Even though it was solved, I updated them nonetheless, which hopefully makes the drive more stable as well.

Thanks for your help! :) 

Aimjy

---

