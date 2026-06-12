---
title: "boot/grub/x86_64-efi missing on install"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by mjobrien on 2018-04-29
Hi All,

I am trying to manually encrypt my full system ([https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)) and am having trouble with the ```
refreshgrub
``` script from [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpBoot](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpBoot).  

I have followed the guide (with the additional data mount) precisely, afaik.  In the script, there is a line that fails:

```
[COLOR=#333333][FONT=UbuntuMono]cp --recursive /boot/grub/x86_64-efi /boot/efi/EFI/ubuntu/[/FONT][/COLOR]
```

This step fails as my /boot/grub/ directory only has:

```
ls /boot/grub/
gfxblacklist.txt unicode.pf2
```

I do not know how to continue.

Thanks for any insights!

---

