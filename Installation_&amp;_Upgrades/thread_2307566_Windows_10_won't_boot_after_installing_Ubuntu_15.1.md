---
title: "Windows 10 won't boot after installing Ubuntu 15.10"
date: 2015-12-26
forum: Installation &amp; Upgrades
---

### Post by jordan-j on 2015-12-26
Hey guys!

I am in desperate need of booting back into Windows 10.
[B]
The situation:[/B]

1. I had an active Windows 10 installed on my HDD
2. I then installed Ubuntu 15.10 onto my SSD using the install alongside Windows Bootloader Option
[B]
The problem:[/B]
When selecting to boot into Windows Bootloader GRUB fails saying that HD1,GPT2 does not exist. (not found)
[B]
Copy of the GRUB code:[/B]
> insmod part_gpt
insmod fat
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  987F-5185
else
  search --no-floppy --fs-uuid --set=root 987F-5185
fi
chainloader /efi/Microsoft/Boot/bootmgfw.efi

[B]
*Please advise how to resolve this problem?*[/B]

Many thanks,

Jordan.

---

### Post by bapoumba on 2015-12-26
Hello,
I have edited your thread title. We are all volunteers here :)

---

### Post by oldfred on 2015-12-27
Best to see details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

When you plugged in SSD, did you change drive SATA port order? UEFI/BIOS typically sees drives in port order. But boot drive is normally then first drive or hd0 in grub. But that may or may not be sda in Ubuntu.

---

