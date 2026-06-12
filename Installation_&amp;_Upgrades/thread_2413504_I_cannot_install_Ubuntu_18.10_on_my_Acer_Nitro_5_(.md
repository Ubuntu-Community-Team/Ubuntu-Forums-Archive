---
title: "I cannot install Ubuntu 18.10 on my Acer Nitro 5 (with Ryzen 7 2700U, RX 560X)"
date: 2019-02-26
forum: Installation &amp; Upgrades
---

### Post by peachjy on 2019-02-26
I bought this laptop several weeks ago and I tried to install Ubuntu 18.10 last week, but I could not install yet. I disabled secure boot and fast boot as the guide(on ubuntu forums) and also tried nomodeset, but it failed. I could see some error messages below:
```
[    0.000000] [Firmware Bug]: AMD-Vi: IOAPIC[4] not in IVRS table
[    0.000000] [Firmware Bug]: AMD-Vi: IOAPIC[5] not in IVRS table
[    0.000000] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found
[    0.000000] AMD-Vi: Disabling interrupt remapping
[    0.082856] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.LPC0.EC0._Q46], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.082869] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.082874] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.082883] ACPI BIOS Error (bug): could not resolve [\_SB.PCI0.GPP2.BCM5], AE_NOT_FOUND (20180531/dswload2-160)
[    0.082889] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20180531/psobject-221)
[    0.082893] ACPI Error: Ignore error and continue table load (20180531/psobject-604)
[    0.082896] ACPI Error: Skip parsing opcode Scope (20180531/psloop-542)
[    0.083741] ACPI BIOS Error (bug): Failure creating [\_SB.MAC0], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.083746] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    6.113846] AMD-Vi: Unable to write to IOMMU perf counter
[   32.040000] watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [migration/0:12]
[   32.044000] watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [migration/2:23]
[   32.044000] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [migration/1:17]
[   32.048000] watchdog: BUG: soft lockup - CPU#3 stuck for 22s! [migration/3:29]
[   32.052006] watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [migration/5:41]
[   31.119066] watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [swapper/4:0]
[   32.056000] watchdog: BUG: soft lockup - CPU#6 stuck for 22s! [migration/6:47]
[   32.060000] watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [migration/7:53]
```

What does it mean and what can I do for it? I even tried to install Ubuntu using VMWare on my desktop and it also failed and I still only could see the messages above. I saw similar problems of another guy(almost same model except of specs), but that guy didn't have problems like this. Please notice me if there's a same problem with how to solve. Thank you.

Ps. I typed all of the message because I don't know how to capture the log, so there can be mistyping.
Pps. English is not my first language. If you can't understand what I'm saying, please notice me.

---

### Post by Vasu_Muppalla on 2019-02-26
You know, buddy, you can take a picture of the screen if you have  a smartphone or camera. Next time it will save you time.

---

### Post by oldfred on 2019-02-26
Have you updated UEFI from Acer.
Most Acer systems we have seen have been Intel, so I would expect those issues to not be the same.
But often issues by brand are similar if same chip, and some by chip vendor across multiple brands have similar issues.

Here they updated UEFI and used boot parameters:
acpi=off or pci=noacpi
[https://www.cnx-software.com/2018/08/19/acer-aspire-3-a315-41g-amd-ryzen-7-2700u-laptop-ubuntu-18-04-m-2-ssd/](https://www.cnx-software.com/2018/08/19/acer-aspire-3-a315-41g-amd-ryzen-7-2700u-laptop-ubuntu-18-04-m-2-ssd/)

General UEFI info in link in my signature below.

---

### Post by peachjy on 2019-02-26
.

---

### Post by peachjy on 2019-02-26
> **Vasu_Muppalla said:**
> You know, buddy, you can take a picture of the screen if you have  a smartphone or camera. Next time it will save you time.
[COLOR=#333333][FONT=Helvetica]Omg I didn't know this forum supports photo uploads because I didn't see any photos lol. Thx, bro[/FONT][/COLOR]

---

### Post by oldfred on 2019-02-26
Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by peachjy on 2019-02-26
> **oldfred said:**
> Have you updated UEFI from Acer.
Most Acer systems we have seen have been Intel, so I would expect those issues to not be the same.
But often issues by brand are similar if same chip, and some by chip vendor across multiple brands have similar issues.

Here they updated UEFI and used boot parameters:
acpi=off or pci=noacpi
[https://www.cnx-software.com/2018/08/19/acer-aspire-3-a315-41g-amd-ryzen-7-2700u-laptop-ubuntu-18-04-m-2-ssd/](https://www.cnx-software.com/2018/08/19/acer-aspire-3-a315-41g-amd-ryzen-7-2700u-laptop-ubuntu-18-04-m-2-ssd/)

General UEFI info in link in my signature below.

After adding pci=noacpi, it finally worked! Thank you so much :)

---

