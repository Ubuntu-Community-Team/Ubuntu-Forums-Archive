---
title: "ACPI Boot Error On Toshiba Qosmio X775"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2011-09-04
I am having trouble getting Ubuntu 11.04 to boot on my new Qosmio X775 laptop. I had to select "Enable ACPI Workarounds" to get the installation to start, and while that worked well, whenever I try to boot into Ubuntu, I see a bunch of text flying by the screen, and it eventually ends with the message: "Bluetooth: SCO Socket Layer Initialized", and then nothing happens. What should I do?

---

### Post by YannBuntu on 2011-09-05
Hello
Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), go to the "Advanced Options", tick the "Add a kernel option", choose "acpi=off" in the list, then click "Apply".

[IMG]http://pix.toile-libre.org/upload/img/1312988983.png[/IMG]

Reboot without the CD to check if it works. If not, retry with each option of the list.

---

### Post by amtur_poet on 2011-10-13
I tried that, but didn't have any luck. I tried out the new 11.10 release, but that leaves me even worse off; it just displays a bunch of code, and an error message ending in "terminated by signal 9" at the end, and stops booting the CD.

EDIT: It only seems to boot when I mess around with the boot settings. Wen it does eventually boot, it loads at an extremely low resolution (despite listing it as a high resolution in the settings). What do I do?

---

### Post by YannBuntu on 2011-10-13
hello
this may help: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by amtur_poet on 2012-02-29
Now, when I try to start up Ubuntu, all I get is a blinking underscore sign, nothing else after selecting it in GRUB. What should I do now?

---

