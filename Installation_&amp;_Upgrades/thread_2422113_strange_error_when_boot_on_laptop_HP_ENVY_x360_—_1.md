---
title: "strange error when boot on laptop HP ENVY x360 — 15-ds0003ur"
date: 2019-07-02
forum: Installation &amp; Upgrades
---

### Post by goffyara on 2019-07-02
I was trying 18.04.02 and 19.04 images. Error when boot on HP ENVY x360 — 15-ds0003ur (amd ryzen 3700u). This is with using `acpi=off` param (and all other params in menu). What is this? How I can fix this?

[IMG]https://downloader.disk.yandex.ru/preview/70a914f35ebf250ae0a60f434e35378c7182cfe089fcee069f810c438bab9848/5d1bc4bf/vuEZC8O00vobEJnWo073iHUyacigA64y__9AmHIsnNJwBbzigch1sICn6D3i4SFthjhJvNdTWszs5Gijdyw4oQ%3D%3D?uid=0&filename=2019-07-02%2019-52-50.JPG&disposition=inline&hash=&limit=0&content_type=image%2Fjpeg&tknv=v2&size=2048x2048[/IMG]

---

### Post by oldfred on 2019-07-02
Some other HP x360 threads:

       HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
See last post for many boot parameters, still using UEFI, not Legacy
[https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615)&
[https://ubuntuforums.org/showthread.php?t=2406993](https://ubuntuforums.org/showthread.php?t=2406993)

---

### Post by goffyara on 2019-07-02
In [COLOR=Navy]UEFI mode always black screen in various kernel params. Parameters from [/COLOR][https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615) aren't working. All that has been achieved on picture (boot in Legacy mode). Arch with newer kernel show same error...

---

### Post by oldfred on 2019-07-02
As in last link are you using Intel chip graphics to install.

Or you may be able to use nomodeset which is normally required with nVidia cards/chips. But you may need additional parameters also. Updates to kernel, support software & drivers may make some boot parameters obsolete. You may just have to experiment.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by goffyara on 2019-07-03
I have been used  --- acpi=off noapic nolapic nomodeset  iommu=soft idle=nomwait . No any result.

> As in last link are you using Intel chip graphics to install

Lapron hasn't intel card. AMD Ryzen™ 7 3700U Mobile Processor with Radeon™ RX Vega 10 Graphics inside.

---

### Post by CatKiller on 2019-07-03
> **goffyara said:**
> Lapron hasn't intel card. AMD Ryzen™ 7 3700U Mobile Processor with Radeon™ RX Vega 10 Graphics inside.

As far as I can tell, support for Vega 10 got added with the 5.1 kernel. I don't know that it's been backported to earlier kernels, and it won't be in the kernel on the install image.

---

### Post by goffyara on 2019-07-03
> **CatKiller said:**
> As far as I can tell, support for Vega 10 got added with the 5.1 kernel. I don't know that it's been backported to earlier kernels, and it won't be in the kernel on the install image.

Thank you. I have been tried last Arch with kernel 5.1.15. Same error...

---

### Post by goffyara on 2019-08-13
Answer [here]("https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477")

---

### Post by oldfred on 2019-08-13
Also if AMD. 
You may need to update UEFI. Vendors are just now including the fix from AMD in the UEFI updates.

       AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)

---

