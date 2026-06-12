---
title: "usb flash drive stops ubuntu from starting"
date: 2020-07-17
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2020-07-17
If a flash drive is connected the startup fails

New install of Ubuntu MATE version 20

Hardware wakes up, Boot screen comes up. Then the screen goes black, no borders, blinking cursor and no response to keyboard.

Testing with a different flash drive, black screen states 'error loading operating system'. There is no os or boot on either flash drive.

I went into the BIOS and set hard drive to first and usb to last. Well it did go good. Well I never thought it would. Right said Fred ...

---

### Post by ActionParsnip on 2020-07-17
version 20 of what, please? If you mean Ubuntu then there is no "Ubuntu 20". It doesn't exist. There is Ubuntu 20.04 (Codenamed "Focal Fossa") which is the latest LTS and Ubuntu 20.10 (Codenamed "Groovy Gorilla"). Which is it please? If you are unsure then you can open a terminal (You can do this with CTRL + ALT + T) and run:
```

lsb_release -a

```
What is the output please?

---

### Post by triplemaya on 2020-07-17
ubuntu 20.04 LTS
focal

---

### Post by triplemaya on 2020-07-19
I have now discovered this is a hardware issue because the same occurs on a windows boot.
But if anyone knows how to fix it I will of course be very grateful for any assistance.

---

### Post by triplemaya on 2020-07-19
Disabling usb boot solved it. 
I wanted to disable USB Legacy Support which I understand would solve the problem but keep the ability to boot from usb in the boot options. But I can't find this is the BIOS. If anyone knows where it is please let me know.

---

### Post by tea for one on 2020-07-19
Each vendor will have a different BIOS/UEFI Firmware set up pages.

If you can let forum members know the make/model of your PC and the BIOS/UEFI version, then somebody with a similar device may be able to help.

---

### Post by triplemaya on 2020-07-19
Thanks

It is an HP Elitebook 840 G1.

I am hopeful there is a solution as the current identical model I have which I am replacing does not have the problem. It is identical, both are on legacy boot. But the one with the problem has a small dos partition for boot which the older one does not. Just in case that is in some way relevant. On that basis I had the thought that it might be an os issue rather than hardware. Probably just displaying my ignorance at this point!

---

### Post by tea for one on 2020-07-19
> **triplemaya said:**
> Disabling usb boot solved it. 
I wanted to disable USB Legacy Support which I understand would solve the problem but keep the ability to boot from usb in the boot options. But I can't find this is the BIOS. If anyone knows where it is please let me know.

I have a 4 year old HP Stream 11" using UEFI/BIOS Setup Utility InsydeH20

System Configuration > Boot Options > Legacy Support (Enable or Disable)

If that is not the correct path for your device, I suggest you navigate around **carefully** because the Legacy Support setting must be there somewhere.

---

### Post by triplemaya on 2020-07-19
Hi. Thanks

I found that ok. It is USB Legacy Support I am looking for. If I disable legacy support my mbr main drive is not going to boot!

---

### Post by tea for one on 2020-07-19
Ah, I see.

I think that you should consider backing up your data and either converting or reinstalling in UEFI mode.

UEFI mode with gpt partitioning is the modern way.

Here is some info - however, whatever you decide make sure you have **restoreable data backups**.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

