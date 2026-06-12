---
title: "Unable to boot after software update on dual boot system"
date: 2021-01-25
forum: Installation &amp; Upgrades
---

### Post by giridhart on 2021-01-25
Hi,

I have Dell XPS with Windows and Ubuntu 20.04.
Recently I installed KDE plasma desktop and that seems to have corrupted the boot.
I managed to boot again using boot-repair live CD, and booting into one off the advanced options listed in Grub menu.

This happened again with software update, I'm able to boot into Windows from Grub but could not into Ubuntu.

I tried boot-repair live CD [https://paste.ubuntu.com/p/dK5bPXjdt4/](https://paste.ubuntu.com/p/dK5bPXjdt4/) before the repair
and [http://paste.ubuntu.com/p/vKDSynyVw5/](http://paste.ubuntu.com/p/vKDSynyVw5/) is log generated for the repair.

I tried to boot manually from grub without success,

The commands I used are below,

set root=(hd1,gpt6)
linux /boot/vmlinuz-5.8.0-38-generic root=/dev/sdb6
initrd /boot/initrd.img-5.8.0-38-generic ---> hangs here

I tried ls -l (hd1,gpt6)/boot/initrd.img-5.8.0-38-generic  which also hanged

Thank you

---

