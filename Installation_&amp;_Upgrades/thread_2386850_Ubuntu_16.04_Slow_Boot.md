---
title: "Ubuntu 16.04: Slow Boot"
date: 2018-03-11
forum: Installation &amp; Upgrades
---

### Post by anspectrum on 2018-03-11
I've Ubuntu installed at SSD drive and I expected boot time to be around 6-7 seconds but that is not happening. Even Win-7 (yes, its dual boot) is booting faster than Ubuntu :(. 

I've searched forums and found some posts reflecting multiple workarounds like disabling acpi, setting GRUB boot parameters, forcing clocksource etc but none of them helped. Since these forums have always been helpful, I thought about posting about this problem so that someone else might also get benefited from it. Here is dmesg output:

[https://paste.ubuntu.com/p/9nVWBzsRP9/](https://paste.ubuntu.com/p/9nVWBzsRP9/)

The problem I can spot are two points: one at line 268-269 and second at line 709-710,  which if we can fix will reduce the boot time by approximately 8 seconds which would then be ideal boot time.

Thanks in advance.

---

### Post by anspectrum on 2018-03-11
Further research brought me to this (which has been referred in couple of different forums):

[https://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/acpi-error-with-linux/td-p/6021489](https://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/acpi-error-with-linux/td-p/6021489)

I also have HP notebook. But to be honest, I've always been able to fix Linux related issues even though HP showed their inability to be of any help. Even if we can't get rid of acpi error, may be we still can fix second one.

---

### Post by anspectrum on 2018-03-21
Update...

Last night I was again searching forums for similar issues and came across ureadahead process which kinda reads files and services so that they can be run faster. Someone had mentioned that in /var/lib/ureadahead/ there would be a file named "pack" that can be deleted and rebuilt. I did that, removed "pack" file and also removed and reinstalled ureadahead but even after couple of boots situation remained same. Then I installed bootchart and again reboot the system.

Interestingly after installing bootchart (to diagnose boot problems) system booted faster, how ironic. lol. I removed the bootchart but system boot time has improved and that second delay as I had indicated in my OP is not there any more. I've removed bootchart but system boot is still good. Don't know how installing bootchart fixed the issue, though once you install bootchart, system updates initramfs. May be somebody can point out that how initramfs rebuild could improve boot times. Latest Dmesg output is attached for reference.

[https://paste.ubuntu.com/p/97zG4Ty9JC/](https://paste.ubuntu.com/p/97zG4Ty9JC/)

---

