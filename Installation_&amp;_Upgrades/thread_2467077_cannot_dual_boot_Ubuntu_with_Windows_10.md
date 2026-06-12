---
title: "cannot dual boot Ubuntu with Windows 10"
date: 2021-09-15
forum: Installation &amp; Upgrades
---

### Post by tomsargood on 2021-09-15
Hello,
I am unable to boot into Ubuntu after installing it next to Windows 10 on my hp 250 g3.
I have tried running the boot-repair tool which said it ran successfully but when i boot it just goes automatically into windows.
fast startup is disabled. If it is helpful i can upload the Boot Info Summary.
Any help would be greatly appreciated! Thank you for reading.
Tom

---

### Post by mikewhatever on 2021-09-15
Are both Ubuntu and Windows installed in the same UEFI/BIOS mode?
Is there an Ubuntu entry in the BIOS boot menu?

---

### Post by tomsargood on 2021-09-15
Hello, thank you for the quick answer!
I'm not sure about the first question.
Ubuntu doesn't appear in the BIOS boot menu

---

### Post by jeremy31 on 2021-09-15
Try going into BIOS/System Config, go to OS boot menu and see if ubuntu appears there.  If it does, put it at the top of the list and press F10 twice, save BIOS settings and restart

---

### Post by tomsargood on 2021-09-15
AHAH!!! I had to press enter when selecting OS Boot Manager then I could see ubuntu and move it above windows!
Thanks a lot!!

---

