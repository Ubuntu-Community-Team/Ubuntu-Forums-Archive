---
title: "how to write the grub.cfg  to install  fedora?"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by luofeiyu on 2012-05-30
my system:ubuntu11.10+grub1.99
i want to install  fedora 16 ,
the iso file is  in  /home/teiger/fedora/fedora.iso  ,/home/tiger  is on  /sda5
linux is in  /home/teiger/fedora/vmlinuz0
initrd is in  /home/teiger/fedora/initrd0.img


what i write  grub.cfg is :
menuentry 'fedora14' --class fedora --class gnu-linux --class gnu --class os {
    insmod loopback
        insmod iso9660       
    loopback loop (hd0,msdos5)/fedora/fedora16.iso
        linux (loop)/fedora/vmlinuz0
        initrd (loop)/fedora/initrd0.img
}

it can't work,would you mind tell me how to revise it ?

---

### Post by deadflowr on 2012-05-30
I was lost reading your thread title when I realized you meant writing grub.cfg to boot fedora iso. I looked around and found this helpful thread:

[http://ubuntuforums.org/showthread.php?t=1549847]("http://ubuntuforums.org/showthread.php?t=1549847")

---

### Post by oldfred on 2012-05-31
I prefer to create a folder that is closer to root, path statement is not so long. When grub loads it is before fstab and /home does not exist as a mount, so you have to specify full path. I have a separate partition just with the iso files.

menuentry "Ubuntu 12.10 Quantal ISO 64bit" {
    set isofile="/iso/quantal-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

Your should be if iso exact name is fedora16.iso

menuentry "fedora16 ISO"  {
set isofile=" /home/teiger/fedora/fedora.iso"
    insmod loopback
        insmod iso9660
loopback loop (hd0,5)$isofile 
    linux (loop)/fedora/vmlinuz0  fromiso=$isofile
        initrd (loop)/fedora/initrd0.img
}

But normally you need more parameters on linux line. I usually open ISO and look at syslinux folder or what ever is used to boot iso and see what parameters are there.
I only have alpha  and it has these parameters:

append initrd=initrd0.img root=live:CDLABEL=Fedora-16-Alpha-x86_64-Live-Desk rootfstype=auto ro liveimg quiet  rhgb rd.luks=0 rd.md=0

See this bug report for Fedora 14, but it seems it still is not totally fixed. Last post may have some help.

[https://bugzilla.redhat.com/show_bug.cgi?id=650672](https://bugzilla.redhat.com/show_bug.cgi?id=650672)

---

