---
title: "error 17"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by nikos_sahi on 2008-10-24
Hello I just installed the Ubuntu 8.04.1 on my external hard drive and everytime that computer boots from that there is a message asking me to choose from list (ubuntu, ubuntu recovery etc) and when every option i try it says Error 17 press any button to go back! can anyone explaine me why it happents and give me a step by step solution please??? I also now can not have access on my external drive from windows! why that happend? does anybody know???

Waiting for your help! thanks!:)

---

### Post by caljohnsmith on 2008-10-24
Probably what happened is Grub (Ubuntu's boot loader) installed itself into the MBR (Master Boot Record) of your internal drive. To get a better idea of your setup, please boot your Live CD, open a terminal (applications > accessories > terminal), and post:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
That should help clarify your setup. :)

---

