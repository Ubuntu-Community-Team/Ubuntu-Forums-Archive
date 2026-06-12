---
title: "Grub does not boot Windows 8"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by abstractmind0 on 2013-12-08
Greetings! Recently i've installed Ubuntu on my laptop with pre-installed Windows 8. Initially grub couldn't see windows at all, so i uset guide from this thread ([http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)) posted by oldfred. Now windows 8 appears at grub os selection list, but when i choose it, grub screen reloads and nothing happens. Whei i tried to run the same command from grub terminal, i got this message: ([https://www.dropbox.com/s/prl2338wo64416q/IMAG0461.jpg](https://www.dropbox.com/s/prl2338wo64416q/IMAG0461.jpg)). Can comeone tell me what's the problem with, and how to solve it? Thanks.

p.s. Sorry for bad English, it's not my native language.

---

### Post by fantab on 2013-12-08
Use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") from Ubuntu DVD/USB to generate '**BootInfo Summary**', note down the LINK it creates and post the link here.

Also share more details of your machine.. like hardware specs.

---

### Post by abstractmind0 on 2013-12-08
Here is the summary [http://paste.ubuntu.com/6540409/](http://paste.ubuntu.com/6540409/).

What exactly specs are needed? The laptop is Samsung NP530U3C, the motherboard model is NP530U3C-A0FRU, CPU is Intel Core i3 1.8gHz, 500gb sata HDD, I don't think, other specs are needed in this case.

---

### Post by fantab on 2013-12-08
> Recommended-Repair
This setting would reinstall the grub-efi-amd64-signed of sda5, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   **fix-windows-boot**

Run the 'Recommended option' in Boot-repair, that should fix the windows booting issue for you.

---

### Post by abstractmind0 on 2013-12-08
That indeed has fixed the issue. Thanks a lot!

---

### Post by fantab on 2013-12-08
Great.
You can additionally download [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), run it and save the boot-info file (like bootinfo-summary from Boot-Repair)o file safely. 
If something were to go wrong you will have boot information for working ubuntu boot and you can use to fix issues with boot in future.

---

