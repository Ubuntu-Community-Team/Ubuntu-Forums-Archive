---
title: "Install failing with ACPI Errors"
date: 2017-10-06
forum: Installation &amp; Upgrades
---

### Post by ian23 on 2017-10-06
Hi,

Trying to do a new install on my machine and getting ACPI errros. Which I am trying to stop in the loopback.cfg but is failing.

Could any one please provide me with what I am missing, I have tried acpi=off , file :

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} acpi=off quiet splash nomodeset acpi_osi=\"Linux\"" ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash nomodeset acpi_osi=\"Linux\"" ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz.efi  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash nomodeset acpi_osi=\"Linux\"" ---
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}

Thanks
Ian

---

