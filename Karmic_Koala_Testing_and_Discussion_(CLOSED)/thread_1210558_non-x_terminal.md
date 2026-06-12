---
title: "non-x terminal"
date: 2009-07-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sintacto on 2009-07-11
Hi y'all

I am testing 9.10 with a 12.1 elo touch screen 800x600
with openchrome driver the touch screen is working but to calibrate
I need a non-x terminal 
control+alt+f1 takes me to a all black screen 
booting into repair mode is the same
grub and usplash and x with gnome work ok

any one else have no non-x terminal?

any thing i could try to fix this?


does any one have 12.1 serial touch screen
who could share min-max x/y with me?
for a short term fix


thanks.

---

### Post by BwackNinja on 2009-07-11
I would recommend trying adding "vga=0x303" or "vga=771" (no quotes of course) to your grub kernel line in menu.lst or just while booting

---

### Post by wayne_cat on 2009-07-11
> **BwackNinja said:**
> I would recommend trying adding "vga=0x303" or "vga=771" (no quotes of course) to your grub kernel line in menu.lst or just while booting

the vga option does not work with the new kernel versions ... the last version that I could boot with this option was 2.6.30-9 :(

edit: try to add "i915.modeset=0" to the grub kernel line if your system has a intel graphics controller

---

### Post by BwackNinja on 2009-07-11
It works with these kernel versions, just not with KMS. Only intel has KMS by default, and you can get it with radeon too, this is openchrome.

---

### Post by wayne_cat on 2009-07-11
> **BwackNinja said:**
> It works with these kernel versions, just not with KMS. Only intel has KMS by default, and you can get it with radeon too, this is openchrome.

A vga option results in a black screen on my system with an ATI x1600 .. nothing happens ... seems to kill my kernel :(

I saw the modeset option (disable KMS) in an older thread ... it was an option to solve the "black screen problem" on systems with intel adapters.

---

### Post by sintacto on 2009-07-11
thanks for the help 
i will try again when i get home

---

### Post by sintacto on 2009-07-11
I added vga=771 to usr/share/doc/memtest86+/examples/grub-menu.lst
but still no terminal in recovery mode or with control+alt+f1

i must add that with this monitor the bios screen is off to the left
and the motherboard splash too but then grub is ok and x works fine
if that changes anything.

---

### Post by sintacto on 2009-07-13
I would like to thank you guys for the help

I just got this working by adding a # 
to this line at /etc/default/grub
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux


#GRUB_CMDLINE_LINUX="splash vga=789 #GRUB_DISABLE_LINUX_UUID=true"

then: 
sudo update-grub


I was then able to run touchcal-0.31 
for serial elo 12.1 touchscreen
minx=335
maxx=3724
miny=511
maxy=3665

hope this helps someone
thanks

---

### Post by Starks on 2009-07-13
> **wayne_cat said:**
> the vga option does not work with the new kernel versions ... the last version that I could boot with this option was 2.6.30-9 :(

**edit: try to add "i915.modeset=0" to the grub kernel line if your system has a intel graphics controller**
nomodeset is the new command.

---

