---
title: "Cannot install lts (or any distro) due to firmware bugs"
date: 2021-09-26
forum: Installation &amp; Upgrades
---

### Post by patrickherren on 2021-09-26
I have an Asus notebook x541ua that seems to start the install process fine then will eventually freeze at a very early stage. During Ubuntu install it was freeze after choosing normal install settings. 
If however I choose to try Ubuntu without installing, it will immediately bring a failure log page up saying: 
No firmware region selected can cover this RMRR .... Contact bios vender for fixes
And Acpi region does not cover this response buffer

I have updated the bios and checked all the settings that can be changed in Bios. Fast boot and secure boot have been disabled

Any ideas? Or is it really that this motherboard isn't possible to run Linux?

---

### Post by ubfan1 on 2021-09-26
Keep checking for firmware updates, they may be quite frequent.  Try the kernel param acpi=0  and if that boots, (maybe in a severely degraded mode with only only CPU core), try refining the acpi=xx.  Google linux kernel params, there are many possibilities, like acpi=ht as the next step.

---

### Post by tea for one on 2021-09-26
> **patrickherren said:**
> No firmware region selected can cover this RMRR .... Contact bios vender for fixes
And Acpi region does not cover this response buffer

I've never seen this [COLOR="#FF0000"]RMRR[/COLOR] message before but I found this [https://askubuntu.com/questions/1331090/dmar-firmware-bug-broken-bios](https://askubuntu.com/questions/1331090/dmar-firmware-bug-broken-bios)

The thread suggests adding Grub parameters (similar to the advice from [COLOR="#0000FF"]ubfan1[/COLOR])

```
intremap=no_x2apic_optout nox2apic
```
```
acpi=off
```

Perhaps try these to see if you can boot a live session?

---

### Post by patrickherren on 2021-09-28
Thanks for the replies, I will definitely try these out. I did try a bunch of acpi= options with no luck so far including 0, 'Windows 2019', 'Linux' but will try a few more here. I will let you know if anything works

---

### Post by ubfan1 on 2021-09-28
Another thing to try is to use the Beta of 21.10 with the latest kernel.

---

### Post by oldfred on 2021-09-28
Some older threads with same model. May have a hint on solving issues.
Newer Ubuntu should be easier/better. 

Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)
Asus X541UV [SOLVED] How to partition my ssd in order to install ubuntu 17.10 / 16.04.4
[https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)

---

### Post by ActionParsnip on 2021-10-01
Make sure that you have the latest BIOS too. May help

---

