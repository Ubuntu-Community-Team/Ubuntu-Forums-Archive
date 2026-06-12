---
title: "external hard instalation"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by linux_noob0 on 2010-02-14
hi there. i got a new laptop, but i'm not satisfied by the current support for its hardware at the moment, so i'm thinking about putting ubuntu on an external hard for now. i wondered if it was possible to make it bootable from any machine too (from the external usb hard drive, it's a transcend btw). i tried it once, but it messed up my normal booting (grub was installed), but i just wanted to install it on the external... is there a clean way to do so? thanks!

---

### Post by darkod on 2010-02-14
When installing, in step 4 remember what your ext hdd is called. Usually if you have one int hdd it would be /dev/sda, and the ext /dev/sdb.
Then in the last screen, before clicking Install, click on Advanced and it will show where it plans to install the bootloader (grub2). Make sure you select the same disk, for example /dev/sdb. There should NOT be a number, like /dev/sdb1, just /dev/sdb.
Grub2 will be on the ext hdd and its config files on the ubuntu partition on the same ext hdd so in theory you can boot it on any computer that supports booting from usb.
Of course, if you also have windows on your computer when you install ubuntu, it will be included in the grub menu and that won't work if you move the ext hdd to another computer. But ubuntu should.

---

### Post by linux_noob0 on 2010-02-14
thanks for the fast reply! :)
i'll try it as soon as possible!

---

### Post by linux_noob0 on 2010-02-14
ok, tried it, but kinda bumped into a wall. everything seems to work, i select my usb hard to boot from, grub opens, ubuntu starts loading, but then it stops saying something about waiting too long for the root drive to respond... anyone knows how to fix this?

*edit
tried it on another computer, same thing, it just says 'dropping to shell' and.. basically drops to shell :/

---

### Post by darkod on 2010-02-14
In the grub menu instead of hitting Enter after highlighting the ubuntu entry, hit 'e'. A list with the boot commands will be displayed. Find the line starting with linux... and at the end add rootdelay=90.
Hit Ctrl + X to boot and see if it boots correctly. If it does, we'll have to find a way to make that permanent, this will only edit it for the current boot.

---

### Post by linux_noob0 on 2010-02-14
hey, thanks for the reply again. i tried the modification you suggested. now it stays at the white ubuntu logo longer, but when it disappears, when i press enter, the same thing happens as before.

---

### Post by darkod on 2010-02-14
So it didn't work. The only thing I could find about this problem is that when booting from usb drives it can be slower than internal drives and adding this rootdelay can help. Yes, it will stay bit longer but it should boot OK.
Obviously the problem is different with you. I'm not sure right now what to do. Maybe it doesn't like your usb hdd. :(

---

### Post by linux_noob0 on 2010-02-14
maybe :/
i'll try experimenting some more when i find some time.
thanks for your help anyway, atleast i know how to install it :)

---

