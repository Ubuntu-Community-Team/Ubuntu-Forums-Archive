---
title: "Grub Broken"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by cle-ziskind on 2014-07-23
Looking for the easiest way to fix my Trusty system. It's a Dell Poweredge, with 2 disks, Trusty is installed on /dev/sdb and (some-other-distro) on /dev/sda, and I guess I removed sda (the info on it is obsolete, anyway).

Grub stuff (like update-grub) now fails with:

/dev/VolGroup00/LogVol00: read failed after 0 of 4096 at 77745553408: Input/output error
/dev/VolGroup00/LogVol00: read failed after 0 of 4096 at 77745610752: Input/output error
/dev/VolGroup00/LogVol00: read failed after 0 of 4096 at 0: Input/output error
/dev/VolGroup00/LogVol00: read failed after 0 of 4096 at 4096: Input/output error
  No volume groups found

What to do?

---

### Post by oldfred on 2014-07-23
VolGroup? Is that RAID or LVM?

If you remove one drive with LVM you break entire system. With some versions of RAID each drive can be used, but if RAID 0 you also break the entire thing. Both drives have some data.

If both drives still there was grub on system you deleted?

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cle-ziskind on 2014-07-23
> **oldfred said:**
> VolGroup? Is that RAID or LVM?

If you remove one drive with LVM you break entire system. With some versions of RAID each drive can be used, but if RAID 0 you also break the entire thing. Both drives have some data.

If both drives still there was grub on system you deleted?

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

LVM. But it was a pull from another system - had to get the data off, ISTR.

When it updated grub, it installed grub to sdb and sdb1 (the 'good' drive that booted the machine, and the machine is running off of). But I'm still getting errors - and I'm afraid to reboot. I shouldn't be, right?

---

### Post by cle-ziskind on 2014-07-23
> **oldfred said:**
> 
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Sorry, it doesn't work:

ERROR:root:Could not find any typelib for Notify

(glade2script:11553): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assert
ion 'GDK_IS_SCREEN (screen)' failed

(glade2script:11553): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: asser
tion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

[...]

/usr/share/boot-sav/gui-g2slaunch.sh: line 29: 11638 Segmentation fault      (co
re dumped) $G2S $1 -g ./$PACK_NAME.glade -s ./$APPNAME.sh --combobox="@@_combobo
x_format_partition@@col" --combobox="@@_combobox_bootflag@@col" --combobox="@@_c
ombobox_ostoboot_bydefault@@col" --combobox="@@_combobox_purge_grub@@col" --comb
obox="@@_combobox_separateboot@@col" --combobox="@@_combobox_efi@@col" --combobo
x="@@_combobox_sepusr@@col" --combobox="@@_combobox_place_grub@@col" --combobox=
"@@_combobox_add_kernel_option@@col" --combobox="@@_combobox_restore_mbrof@@col"
 --combobox="@@_combobox_partition_booted_bymbr@@col"

---

### Post by oldfred on 2014-07-23
IF errors are from Boot-Repair it may not be a good download. 
Or is that from Live installer?

Or if from your system.
Those errors seem like they are past grub. 
If you only have one install grub menu does not normally show.
If BIOS you can hold shift key from BIOS until grub menu appears, or if UEFI often escape key required to get grub menu.

If you can get grub menu try second entry or recovery boot.

---

