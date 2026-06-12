---
title: "Grub installation failed on UEFI hardware"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by solidrepellent on 2013-08-25
Hi all,

I have a new Sony Vaio duo 11 with UEFI and GPT enabled hardware. I  would like to dual boot Windows 8 with Kubuntu. When I try and install  Kubuntu 12.04, I get "Grub installation failed error" as shown in the  attached picture.

[http://i.imgur.com/r2zR7Tk.jpg](http://i.imgur.com/r2zR7Tk.jpg)

I then booted again into the live USB of Kubuntu 12.04 and then run  boot-repair tool. The following is the URL which the boot-repair tool  gave. The tool works perfectly but when I boot, it boots back to Windows  and does not give the grub menu. 

[http://paste.ubuntu.com/6025474/](http://paste.ubuntu.com/6025474/)

My questions:

1) Why does the Grub installation fails when Ubuntu's does not?
2) What else can I do to get the Grub right?

---

### Post by oldfred on 2013-08-25
The first error is related to secure boot. Best to turn secure boot off and just boot in UEFI mode. But a few systems will only boot Windows with secure boot on. Then you have to install Ubuntu in UEFI mode with secure boot. 

Your install is now UEFI mode, but you have to go into UEFI menu and choose the ubuntu entry. You still show an opensuse entry in efi partition. If you uninstalled it, that does not delete boot folder in efi partition and may not delete entry in UEFI. Which you have to do from UEFI menu or UEFI shell in command line mode.

---

