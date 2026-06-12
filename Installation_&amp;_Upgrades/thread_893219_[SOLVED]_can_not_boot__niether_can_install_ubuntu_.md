---
title: "[SOLVED] can not boot  niether can install ubuntu or any os"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by AceDip on 2008-08-18
when i start my pc and just when the GRUB is supposed to pop up, instead this thing comes up.

```
error 17 : file not found
```

and nothing happens after that.

---

### Post by AceDip on 2008-08-18
when i try to install ubuntu again.
it gives following errors.

```
[507.25487] hda: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq: 0x00
[508.26587]SQUASHFS error: sb_bread fialed reading block 0x32584
[509.51248]buffer I/O error on device hda,logical block 302412
[509.65974]SQUASHFS error:unable to read fragment cache block
[510.26487]SQUASHFS error:unable to read page,block 223564b
[512.56231]run_init: /sbin/init:I/O error
[601.23561]kernel panic - not syncing,attemting to kill init
error 17 : cannot mount selected partition
grub > quit

```

all this lines keep on repeating for a long time,.

---

### Post by SkonesMickLoud on 2008-08-18
Boot into the LiveCD and in a terminal enter:

```
sudo grub
```

Then:

```
find /boot/grub/stage1
```

It should return something along the lines of:

```
(hdx,y)
```

Then enter:

```
root (hdx,y)
```

Then:

```
setup (hdx)
```

Reboot.

---

### Post by AceDip on 2008-08-18
when i try to boot into the live cd.the welcome screen with ubuntu over it and the timer bar takes a hell lot of a long time and in the end i start getting the above messages ,which keep on coming for a while and nothing happens

---

### Post by SkonesMickLoud on 2008-08-18
When you boot the CD are you given an option to boot into "rescue" or "safe" mode?

These will be text only, but will accomplish the same thing.

---

### Post by AceDip on 2008-08-20
> **SkonesMickLoud said:**
> When you boot the CD are you given an option to boot into "rescue" or "safe" mode?

These will be text only, but will accomplish the same thing.

no i do not get any option like that..
the screen just shows the above mentioned list of errors.

---

