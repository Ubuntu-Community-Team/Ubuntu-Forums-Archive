---
title: "symlinks for the Documents and Video folders"
date: 2024-06-02
forum: Installation &amp; Upgrades
---

### Post by fabio61 on 2024-06-02
I have a dual boot system with three HD.
Two of them are solid-state HDs, with Ubuntu 22.04 (root and /home) on the first and Windows on the second. The third HD is a mechanical HD (formatted ad NTFS) that hosts all my data. In the mechanical HD, I have the folders "documents" and "video."
When I use Nautilus or another file manager, the default menu offers "documents" and "video" in the preferred panel; however, they do not point (of course) to my folders with the same name (that are in the mechanical disk) but to empty folders in the /home.
To obviate this problem, I have used a simple method for the last few years: I have created symlinks with the same names (just using the function "create a link in Nautilus) and substituted them to the default folders in the /home. In this way, when I clicked on the preferred list in Nautilus, I had access to the folders in the mechanical disk.
I have worked well with this method for years. Recently, I had to reinstall the system for a hardware problem (I had to change my motherboard); I did the same thing, but now the system behaves much differently: the links on the preferred menu are broken (a red cross appears instead of the folder icon), and I have no access to the folders and files (neither on the file manager nor from the applications) until I click on the mechanical disk in the "+ other positions" section of the menu. At this point, everything is back to normal: I have access again to the files, and the folder icon appears again.
I have to follow the same procedure for any new system access, which is annoying. Supposedly, the system configuration did not change (unless the technician who changed the motherboard modified some connection).
Does anybody have an idea about what happened and how to solve the problem?

---

### Post by Holger_Gehrke on 2024-06-02
That reads as if your mechanical disk isn't getting mounted at system start-up. Check your /etc/fstab. The system might try to mount the disk using a device file name (e.g. /dev/sdc1) which has changed. The right way to do mounting has been the use of UUIDs or Labels for a long time now since device names have became subject to change without notice depending on the order in which device declare themselves ready for use during startup. Read the manual page for fstab (man 5 fstab) for details on what to put into the fstab and use sudoedit when editing that file. Alternatively gnome-disks has a menu-entry 'Edit Mount Options' in the menu you get when clicking on the cog-button in the main pane under the display of partitions on the drive. Should do the same thing.

Holger

---

### Post by fabio61 on 2024-06-02
> **Holger_Gehrke said:**
> That reads as if your mechanical disk isn't getting mounted at system start-up. Check your /etc/fstab. The system might try to mount the disk using a device file name (e.g. /dev/sdc1) which has changed. The right way to do mounting has been the use of UUIDs or Labels for a long time now since device names have became subject to change without notice depending on the order in which device declare themselves ready for use during startup. Read the manual page for fstab (man 5 fstab) for details on what to put into the fstab and use sudoedit when editing that file. Alternatively gnome-disks has a menu-entry 'Edit Mount Options' in the menu you get when clicking on the cog-button in the main pane under the display of partitions on the drive. Should do the same thing.

Holger

Thank you very much, Holger,
Now I know what happened: after the new motherboard was installed, the technician could not restore the system as it was, and I had to compile the fstab manually with the new UUIDs. I had not realized that the line about the mechanical drive was entirely missing.
I will fix it and change the post label to solved as soon as I restart the system

---

### Post by fabio61 on 2024-06-02
work perfectly,

thank you

---

