---
title: "Help with grub.cfg invalid signature Windows menuentry"
date: 2016-01-15
forum: Installation &amp; Upgrades
---

### Post by aristo c. on 2016-01-15
Hi guys!

I recently made a Kubuntu installation on a 2 hdd system (one with windows, one with linux). 
During Kubuntu installation no other systems were detected so no Grub menu entry for Windows.
Afterwards I edited the grub.cfg file with grub-customizer, and this is what I added:

```
### BEGIN /etc/grub.d/44_custom_proxy ###
menuentry "Windows 8.1 64-bit"{
    savedefault
    insmod part_gpt
    insmod fat
    set root='hd1,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  CA9C-F56C
    else
      search --no-floppy --fs-uuid --set=root CA9C-F56C
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/44_custom_proxy ###
```

I'm getting the "invalid signature" error upon selection. I made sure partition type is gpt, EFI is on /dev/sdb3, and UUID is as above.
What am I missing here? All help is welcome. Thanks.

All the best

---

### Post by Mark Phelps on 2016-01-15
First of all, you should NEVER hand-edit grub.cfg -- other than to do a temporary test.  Why? Because the next time you do an update, that is liable to overwrite grub.cfg and remove all the edits you made.

A better way to do what you want (add an entry for MS Windows) is to open a terminal and run "sudo update-grub".  This will invoke the os_prober app which will search for Windows, and when it finds it, automatically update GRUB for you.

Good Luck

---

### Post by grahammechanical on 2016-01-15
When you installed Kubuntu did you load the installation DVD/USB in EFI mode? Windows 8.1 would have been installed in EFI mode and that means Kubuntu must also be installed in EFI mode. Installing Kubuntu in BIOS/Legacy mode could explain why no other operating systems (that is Windows 8.1) were detected during the installation process.

Regards.

---

### Post by aristo c. on 2016-01-15
To Mark Phelps,
I used grub-customizer to manually add the new entry, I don't know if it will be overwritten when I update. From what I gather grub-customizer uses os_prober built-in to look for the OSs and, of course, it doesn't detect it.

To grahammechanical,
To be perfectly accurate it wasn't me who installed Kubuntu, so I can't answer the question, but I take it it must be from that. I did notice the computer had secureBoot enabled but failed to mention that to the person who would be installing. I suppose because of secureBoot it could only be installed in BIOS mode, right, in case no way around it uhm?

---

### Post by oldfred on 2016-01-15
So far most computers have three ways to boot UEFI with secure boot, UEFI, and BIOS.
You can turn secure boot off and still boot in either UEFI or BIOS boot mode.
Some systems call Secure boot "other" and first option is Windows. That is really the secure boot setting.
On my Asus motherboard I had to set "other" and then UEFI only. Even a setting of CSM and UEFI with UEFI first only booted in BIOS/CSM/Legacy mode. So UEFI only with "Other" or really secure boot off worked for my system. But systems vary a lot.

If Ubuntu installed in BIOS mode, but Secure boot is on, then Ubuntu will not boot. BIOS mode has no secure boot capability.

Best then to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by aristo c. on 2016-01-16
Thanks oldfred,

I believe this thread will be useful for people experiencing the same issue.

All the best.

---

