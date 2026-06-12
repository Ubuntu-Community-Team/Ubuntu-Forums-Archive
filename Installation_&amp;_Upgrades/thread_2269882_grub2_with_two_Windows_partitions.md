---
title: "grub2 with two Windows partitions"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by AyJJ7fd on 2015-03-18
Hello.
I have two hard drives in my computer – one with Ubuntu installed and one that is partitioned with two Windows 7 installs (one 32bit, one 64bit). Initially, I had just one Windows 7 partition and grub2 worked great for booting into Ubuntu and Windows. Now with two Windows partitions, I cannot get grub2 to boot into the second Windows install. The grub2 entry points to /dev/sda1, which is the Windows System partition, my 32-bit Windows install is on /dev/sda2, and my 64-bit Windows install is on /dev/sda3. How can I have both Windows partitions bootable?

Thank you!

---

### Post by grahammechanical on 2015-03-18
Does Grub know about this second Windows 7 installation? If we install another OS, windows or Linux it makes no difference, after installing Ubuntu we need to load into Ubuntu and run

```
sudo update-grub
```

Watch the printout to the screen. It should reveal that Grub has detected 2 Windows boot loaders. Please confirm that update-grub is not detecting both Windows boot loaders.

Another question. when the second version of Windows was installed where did it put it boot loader? Into sda1? If the boot loader for the first Windows was in sda1 and the second Windows put its boot loader there as well, then it would have over written the first boot loader. And that could be the cause of the problem.

Regards.

---

### Post by oldfred on 2015-03-19
Windows only has boot files in one NTFS primary partition with the boot flag. So a second install of Windows will copy its boot files into the first install and update BCD for both Windows.
But second install then has no boot files for grub2's os-prober to find.
Only if second install is also in a primary partition, can you easily repair it to add back/repair its boot files. Just move boot flag to second install and then run standard Windows repairs.
But if you installed to a logical partition, you cannot repair it as it is not directly bootable with Windows.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[URL="http://www.multibooters.co.uk/articles/windows_seven.html"]http://www.multibooters.co.uk/articles/windows_seven.html

[/URL] Vista and win7 boot files, with Windows 7 first two are in separate Boot partition but do not have to be:
  Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

Grub2's os-prober specifically looks for bootmgr & BCD to know that is a bootable partition. Grub2 does not use boot flag like Windows does, so grub can directly chain load to both Windows installs.

[URL="http://www.multibooters.co.uk/articles/windows_seven.html"]
[/URL]

---

