---
title: "Can't boot ubuntu 13.10 after install Fedora 20 on a x86_64 EFI machine"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by kid1994hn2 on 2014-02-01
Hi all,
I can't boot ubuntu from gub menu after I install fedora (but I can boot Fedora and windows)
[IMG]http://i1152.photobucket.com/albums/p483/kid1994hn/CAM00013_zpsb5977d96.jpg[/IMG]
[IMG]http://i1152.photobucket.com/albums/p483/kid1994hn/CAM00014_zps4096a766.jpg[/IMG]

But I can boot from here
[IMG]http://i1152.photobucket.com/albums/p483/kid1994hn/CAM00012_zps2ea9a884.jpg[/IMG]

Do you have any idea?

---

### Post by oldfred on 2014-02-01
Best to see details, it almost looks like Fedora's entry is a BIOS type not UEFI type entry as it should be loading grub in Ubuntu&#8217;s efi folder:

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

