---
title: "Installing Ubuntu via USB drive."
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by HpPavilion on 2011-05-29
Hello,

I am trying to download Ubuntu on my HP Pavilion because it says I need a "boot device" so I want to put ubuntu as my set OS and when I get to the menu I press enter for installation. So I when I try to do it, it comes to a black screen and it has all this stuff about timers and what not.

Then it says:

" Kernel panic - not syncing: IO-APIC + Timer doesn't work! Try booting with the 'noapic' option."

Now I really don't know what to do.

So if anyone could help me I would really  appreciate it.

---

### Post by dummy910 on 2011-05-29
[http://**ubuntuforums.org**/showthread.php?t=1646473](http://**ubuntuforums.org**/showthread.php?t=1646473)

---

### Post by oldfred on 2011-05-29
Some more links:

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by HpPavilion on 2011-05-30
> **dummy910 said:**
> [http://**ubuntuforums.org**/showthread.php?t=1646473](http://**ubuntuforums.org**/showthread.php?t=1646473)

Thanks I'll see what I can do.

---

