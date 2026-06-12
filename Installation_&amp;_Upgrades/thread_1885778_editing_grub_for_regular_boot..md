---
title: "editing grub for regular boot."
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by red40y on 2011-11-23
alrighty, i was having graphics problems on my dell inspiron. i managed to figure it out, but i dont know how to make my changes perm. i added "acpi=off radeon.modeset=0" to the grub when i start ubuntu, but i dont know how to make it perm so i dont have to keep adding it each time i want to run ubuntu =). any help would be great. 
[B]
[/B]

---

### Post by oldfred on 2011-11-23
You need to edit this and then run sudo update-grub to rewrite grub.cfg:

```
gksudo gedit /etc/default/grub
```
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by red40y on 2011-11-24
thank you for the much needed help! and have a safe holidays!

---

