---
title: "Issues with Booting from HDD"
date: 2016-06-09
forum: Installation &amp; Upgrades
---

### Post by brian130 on 2016-06-09
Hi All,

Just tried to do a clean install of Ubuntu on a HDD that used to have windows. I was able to successfully use Ubuntu through the USB but every time I try to boot from the HDD it never works. 

Just a black screen that says "failed to open \EFI\BOOT\grubx64.edi - Not Found." and "failed to open \EFI\BOOT\MokManager.efi -Not Found."

I tried repairing with boot-repair and the pastebin can be found here: [http://paste2.org/bOtjm8jv](http://paste2.org/bOtjm8jv). Any ideas of what I could do to fix this problem? Any help would be greatly appreciated.

Thanks,
Brian

---

### Post by ubfan1 on 2016-06-09
Which version are you trying to install?  Your install media looks a little strange, like missing the default bootloader in /EFO/Boot/bootx64.efi.  Are you running with secure boot enabled?  Does it boot after you made the boot-repair?

---

### Post by oldfred on 2016-06-09
You are missing the ubuntu entry in UEFI.

What brand/model. Says video is Lenovo?

 The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

