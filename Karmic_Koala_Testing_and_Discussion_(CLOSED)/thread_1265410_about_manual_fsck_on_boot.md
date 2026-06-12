---
title: "about manual fsck on boot"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-09-13
I noticed that every time that something fails during a shutdown (or every time you have to brutally power off the pc because of a freeze) the boot process fails and asks to run fsck manually.

This thing never used to be the same in previous versions of ubuntu. A normal fsck was run every N boots, without asking the user to insert any particular command.

I would like to report this thing but I don't know the exact package of the "bug"
Can you help?

---

### Post by dino99 on 2009-09-13
i think acpi has something to do with that.

---

### Post by Funnnny on 2009-09-13
I can confirm that. Everytime we have problem with the last boot, Ubuntu asks for run fsck manually, and I have to boot into the recovery mode to solve this problem

---

### Post by Robin Nixon on 2009-09-13
Same here

---

### Post by dino99 on 2009-09-13
you are lucky, i need to unplug

---

### Post by barisurum on 2009-09-13
Who could guess fsck would be a fscking problem someday...

---

### Post by kansasnoob on 2009-09-13
I had the same problem and Psyke83 gave me some info here:

[http://ubuntuforums.org/showthread.php?t=1252690](http://ubuntuforums.org/showthread.php?t=1252690)

It seems to be sorted out for me at present, dunno why:confused:

---

### Post by joey-elijah on 2009-09-13
Sort of the same for me, however Karmic refuses to shut down cleanly and just gets stcuk in a "loop" error of which i cannot recount because my eyes roll and i hit restart.

Manually FSCK'in does the trick, but an inconvenience nonethless. Hopefully i'll get a 10 sec boot during the beta :P

---

### Post by madmetal on 2009-09-13
same here with 64bit karma

---

### Post by excogitation on 2009-09-15
Same here.

Also every time initramfs gets updated.

> /dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4

---

### Post by Gourgi on 2009-09-15
> **excogitation said:**
> Same here.

Also every time initramfs gets updated.

i'm experiencing the same with my ext4 karmic with encrypted home dir.
is there going to be a fix for this or i have to re-install ??

---

### Post by xebian on 2009-09-15
Have the same problem here.  The thing is we get to this because of some timestamp of last mount was in the future.

---

