---
title: "Grub problem on multi OS"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by mavik1 on 2014-02-15
Hi,

My hdd has partioned as.

1) Window (sda1) -> Installed first
2) Ubuntu 10.04(sda6) -> Installed last
3) Ubuntu 12.04 (sda7) -> Installed Second

When (2) sda6 was formatted. after restart grub loader is not displayed, insted  It prompts grub rescue> .
How to recover or repair to grub. so that, grub sda 7 get displayed.
 
Thanks

---

### Post by oldfred on 2014-02-15
You really want to boot with grub2 from 12.04.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

