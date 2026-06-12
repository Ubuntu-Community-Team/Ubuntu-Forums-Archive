---
title: "acpi not work line in breezy"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by bullgr on 2006-06-01
hi...

i updated to dapper but now acpi is not working like in breezy.
in breezy i just press the power button and the pc shutdown just fine.
now when i press the button the pc got a hard power off.
when i give the command
> sudo shutdown -h now
the pc makes a normal shutdown, but last i must press the power button to
power off the pc.

please, i must solve the problem because i use ubuntu server in my workplace
and it's important to power off the server from the power button (windows co workers:???: )

thank's

---

### Post by daiwai on 2006-06-02
I have the same problem, any ideas how to fix this?

---

### Post by cam_tram on 2006-06-04
I was having the same problem.  Try passing 'acpi=force' to the kernel at boot, that worked for me

---

### Post by norman_h on 2006-06-06
That did not work on my ASUS M6R lappy.

Thanks anyway :)

---

### Post by cam_tram on 2006-06-25
try compiling a new kernel, the 2.6.16 kernel fixed a slew of acpi related issues for me

---

### Post by norman_h on 2006-06-25
...even the 2.16.17 kernel didn't work :(

maybe im doing something wrong...

---

### Post by forlau on 2006-06-26
add to your /boot/grub/menu.lst  **apm=on acpi=on**: It should look like this

```
kernel      /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda8 ro quiet splash  apm=on acpi=on

```

---

