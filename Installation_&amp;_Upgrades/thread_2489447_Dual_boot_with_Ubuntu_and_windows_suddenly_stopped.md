---
title: "Dual boot with Ubuntu and windows suddenly stopped working"
date: 2023-07-31
forum: Installation &amp; Upgrades
---

### Post by qubento on 2023-07-31
Hi, I had installed Ubuntu 22.04 alongside windows 11 which was working fine for few months. After a system restart after power issues, the grub options don't show up. I am unable to boot ubuntu now. 
Here is the boot repair url
https://paste.ubuntu.com/p/XYQdxwTKdG/
The uefi secure boot is turned off and I have disabled fast startup on windows 11 now. Please help recover the Ubuntu installation. I have unbacked up android studio projects in it. Thanks

I went ahead with the recommended repair and it reported error NVram locked. Here is the new url 
https://pastebin.ubuntu.com/p/QJp7Dnx9Nr/

---

### Post by qubento on 2023-07-31
Solved it. Got the grub menu back by adding boot option manually in boot settings from bios options

---

### Post by oldfred on 2023-07-31
We are seeing more of the locked BIOS (really UEFI) error.

Did you change some setting(s) or just add an Ubuntu entry in UEFI boot in UEFI setting menu?

---

### Post by qubento on 2023-07-31
Just added ubuntu entry in boot options. Didn't change anything else. Maybe the recommended repair from boot repair tool also helped. Not sure though

---

### Post by oldfred on 2023-07-31
Thanks, please change to solved, so others may find thread.

---

