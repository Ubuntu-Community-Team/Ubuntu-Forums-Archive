---
title: "Can't Boot"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rahulthewall3000 on 2009-10-02
Hey, I get this error when I try to boot into my brand new Kubuntu 9.10 Beta install (it was working before - I just removed network manager and replaced it with wicd).

Here's the error:

```
render error detected, EIR: 0x00000010
page table error
PGTBL_ER: 0x00000100
[drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
render error detected, EIR: 0x00000010
page table error
PGTBL_ER: 0x00000100

```

---

### Post by dino99 on 2009-10-02
i915 chipset : is it blacklisted ?

---

### Post by Amaranth on 2009-10-02
Try booting with the 'nomodeset' option (edit your grub linux line to add it).

---

### Post by benuch on 2009-10-08
Hello,

I have same bug!

I tried the nomodeset option

Error on drm disappear, but the boot stop at starting apparmor profiles

Have you other idea???

---

