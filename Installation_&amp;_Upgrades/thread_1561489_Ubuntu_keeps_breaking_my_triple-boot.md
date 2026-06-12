---
title: "Ubuntu keeps breaking my triple-boot"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by kev717 on 2010-08-26
I have a triple-boot configuration on my new desktop: I have a 2Gb /boot partition shared with Sabayon and Fedora, a 77Gb Sabayon partition, and a 400Gb LVM containing a 200Gb Fedora partition and a 200Gb Ubuntu partition. The order of installation went Sabayon then Fedora then Ubuntu.  Ubuntu detects Fedora perfectly and adds the appropriate kernel to the boot menu, however there is no Sabayon (in the ubuntu installer it said that it detected sabayon as a gentoo-base system).  I got it to work once by modifying my grub.cfg to include a section that I backed up from the Sabayon bootloader while trying to fix the Sabayon boot with Fedora.  EDIT: Basically, I inserted a menuentry for Sabayon manually.  

Today Ubuntu upgraded my kernel and my triple-boot is once again broken.  Is there some way I can fix my triple-boot so that when ubuntu upgrades the grub menu it automatically includes Sabayon as well?  I will attach my grub.cfg from both the new Ubuntu install and the original Sabayon install.  

Attachments: 
-Ubuntu's new generated grub.cfg
-Sabayon's old generated grub.cfg

Thank-you in advance for any help that is offered.
-Kev717

---

### Post by wkulecz on 2010-08-26
This is one of the main reasons I've been so critical of grub2, but at least the docs are finally starting to catch up.  Support for multiboot is flaky at best -- os-finder feature usually runs amok creating more menuentries that is reasonable to deal with, but you seem to have the opposite problem.

Read:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
especially section 7.

I've got a quad boot system with Windows, 6.06, 8.04, and 10.04  the only reason I've stayed reasonably sane about it is 6.06 and 8.04 are in maintainence mode so the kernel updates don't change the vmlinuz names on these.  Update-grub seems to handle 10.04 OK automatically but it's be a total PITA if the vmlinuz names were changing on the other systems.

---

### Post by oldfred on 2010-08-26
Can you not just copy a Sabayon entry into 40_custom for Ubuntu or copy Ubuntu's entries into 40_custom for Sabayon?

I thought you could not share /boot without creating issues with kernels. Are Sabayon & Fedora so different that you have no overlap?

You can also copy a simple boot loader into 40_custom that will always boot the most current version. Uses linked vmlinux & initrd in root.

From Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by kev717 on 2010-08-26
Copying the Sabayon menuentry to 40_custom seems to have worked.  If Sabayon updates the kernel though I should think that I will also have to update that entry which is no problem (I don't like messing around with boot loaders so I'm not likely to define a boot loader in 40_custom)

Also, sharing a /boot partition may only cause conflicts if Fedora or Sabayon try to boot from the other's kernel.  I have a Fedora 10/13 system with a shared /boot partition and there are no problems with booting to either versions of the OS.  

thank-you for your help.
-kev717

---

### Post by oldfred on 2010-08-26
The boot loader I posted just uses a link in root. The link in root is updated on every kernel update, so the link always points to the newest kernel. Otherwise it is the same as the standard entries that use specific kernels in /boot.
Do not know if other distributions do the same thing.

---

