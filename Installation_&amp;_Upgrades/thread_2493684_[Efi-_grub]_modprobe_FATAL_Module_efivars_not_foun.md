---
title: "[Efi- grub] modprobe: FATAL: Module efivars not found"
date: 2023-12-21
forum: Installation &amp; Upgrades
---

### Post by rounrounroun on 2023-12-21
Hello everyone,

I used rufus and unetbootin with different version of ubuntu. I installed it but I am not able to boot. I used a live usb key to see the problem with boot-repair but even while looking at the reasons, I am not able to find a solution on Internet :
[https://pastebin.ubuntu.com/p/mNKMGKZ9bD/](https://pastebin.ubuntu.com/p/mNKMGKZ9bD/)

Can someone help me ?

Kind regards,

Roun

---

### Post by tea for one on 2023-12-21
In your UEFI settings, do you have other Lenovo security options e.g.
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard or OS Optimised Defaults
If enabled, I suggest disable them.

---

### Post by MAFoElffen on 2023-12-21
What I tell people to do when they first boot  LiveUSB, open a terminal and do:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
That will tell you what boot mode it booted as. If not what you expected, go into the BIOS settings and change the boot mode. 

Or, ensure that the LiveUSB was created with a GPT partition table, so that it forces the booting of it towards an UEFI boot...

With Some Brands/Vendors, that requires a few different things, based on that vendor. Hinted at, by the last post.

I can see that the system was installed as UEFI. The LiveUSB just didn't boot in that mode. 

Note: In my contributions to 'boot-repair', I have recommended that we already check for that in the code, that we should indicate that to the user in a prompt (visually) to clear some of that confusion. I have suggested a patch for that. I just haven't gotten any word back on that yet.

---

