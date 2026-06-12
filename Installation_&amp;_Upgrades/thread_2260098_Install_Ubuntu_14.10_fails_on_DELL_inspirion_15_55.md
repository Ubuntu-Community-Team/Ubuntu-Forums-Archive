---
title: "Install Ubuntu 14.10 fails on DELL inspirion 15 5547"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by Yajnab on 2015-01-09
The System I own is Dell Inspirion 5547. On trying to Install Ubuntu 14.10 on it following the steps as per needed for UEFI systems I got into a problem at the end.
Grub2 failed to install
grub-efi-amd64-signed package failed to install into /target/..

I hope someone solves it.

---

### Post by ibjsb4 on 2015-01-10
I do not run efi and not going to be much help, but we have our forum efi expert 'oldfred'.  Maybe his post will help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=efi+oldfred&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=efi+oldfred&sa=Search&cof=FORID:9)

It could also help to edit your thread title to include EFI.

---

### Post by oldfred on 2015-01-10
Were you installing in BIOS or UEFI boot mode?
If BIOS, you many not have had the bios_grub partition, but if Windows is UEFI, you really want grub installed in UEFI boot mode.
How you boot installer UEFI or BIOS is how it installs. Boot-Repair can convert a BIOS install to UEFI or vice-versa. But you need to boot it in UEFI mode.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See also links in my signature.

And this is the most important part:

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

