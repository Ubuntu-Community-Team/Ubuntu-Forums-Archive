---
title: "Can Ubuntu desktop 14.04 LTS be installed along with Windows Server 2008 r2"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by sandeep21 on 2015-07-24
Good day 

My friend has a HP Proliant ML 110 G7 server with single hdd (two partition) having Windows Server 2008 r2. Can we install Ubuntu 14.04 LTS desktop version along with existing Server 2008 r2 in the second partition?

---

### Post by SeijiSensei on 2015-07-24
Yes.

When you get to the partitioning step, choose "manual" and tell the installer to put Ubuntu in the empty partition.

---

### Post by sandeep21 on 2015-07-24
Good day SeijiSensei,

Thanks for your prompt reply. My question was based on several opinions we got stating that we should install Ubuntu Server and not Ubuntu desktop along with Windows Server 2008. Please advise.

---

### Post by SeijiSensei on 2015-07-24
Ubuntu Server differs from the desktop versions in only two, irrelevant ways.  First, it bundles server programs like the Apache web server by default, and second, it does not include a graphical desktop.  Otherwise there is no functional difference between the server and desktop versions.  For instance, you could install a desktop release, then add the server programs you want to it.  Alternatively you could install the server version, then add a graphical desktop.

---

### Post by sandeep21 on 2015-07-25
Good day SeijiSensei

Many a thanks for your guidance and clarification. We will start installation today. Will bother you if we come across any issue.

---

### Post by sandeep21 on 2015-07-26
Good day All,

As planned we installed Ubuntu 14.04 in the second partition (which was the d: drive of Windows Server 2008 r2). The installation went smoothly. Now we have discovered that Windows 2008 r2 option in the GRUB menu is not loading/booting win server 2008. Please advise.

---

### Post by SeijiSensei on 2015-07-27
What happens? "Is not loading" is not a sufficient description of the problem.  Is there an entry for Windows 2008 when the boot menu appears on screen? Does it boot and fail? Does it throw an error?

Does /boot/grub/grub.cfg contain a stanza for Windows 2008 that looks something like this?
```

menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-1E1E81AF1E81808F' {
        insmod part_msdos
        insmod ntfs
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  1E1
E81AF1E81808F
        else
          search --no-floppy --fs-uuid --set=root 1E1E81AF1E81808F
        fi
        parttool ${root} hidden-
        chainloader +1
}

```
This is the code that displays the Win7 bootloader on my Kubuntu 14.04 machine.

Did you install grub to /dev/sda (or hd0) or some place else?

---

