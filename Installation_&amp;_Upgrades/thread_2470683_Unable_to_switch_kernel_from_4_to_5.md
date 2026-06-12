---
title: "Unable to switch kernel from 4 to 5"
date: 2022-01-07
forum: Installation &amp; Upgrades
---

### Post by amdijefri on 2022-01-07
Hello, I am trying to switch my Ubuntu VM on Rackspace from kernel 4 to 5, unsuccessfully. I have tried many how-tos online about ```
sudo grub-mkconfig | grep -E 'submenu |menuentry '
``` followed by ```
sudo vi /etc/default/grub
``` followed by a reboot. No matter what I set ```
GRUB_DEFAULT
``` to, the system always boots to version 4. This is a VM so connecting to the emergency console before the kernel menu timeout, as some how-tos advise, will not work. Here is the output of grub-mkconfig in the hopes it is useful and a simple fix. Thank you.
```
$ sudo grub-mkconfig | grep -E 'submenu |menuentry '
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-92-generic
Found initrd image: /boot/initrd.img-5.4.0-92-generic
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f690b157-f6c5-431b-a48b-1280f030f798' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f690b157-f6c5-431b-a48b-1280f030f798' {
    menuentry 'Ubuntu, with Linux 5.4.0-92-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-92-generic-advanced-f690b157-f6c5-431b-a48b-1280f030f798' {
    menuentry 'Ubuntu, with Linux 5.4.0-92-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-92-generic-recovery-f690b157-f6c5-431b-a48b-1280f030f798' {
Found linux image: /boot/vmlinuz-5.4.0-91-generic
Found initrd image: /boot/initrd.img-5.4.0-91-generic
    menuentry 'Ubuntu, with Linux 5.4.0-91-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-91-generic-advanced-f690b157-f6c5-431b-a48b-1280f030f798' {
    menuentry 'Ubuntu, with Linux 5.4.0-91-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-91-generic-recovery-f690b157-f6c5-431b-a48b-1280f030f798' {
Found linux image: /boot/vmlinuz-4.15.0-34-generic
Found initrd image: /boot/initrd.img-4.15.0-34-generic
    menuentry 'Ubuntu, with Linux 4.15.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-34-generic-advanced-f690b157-f6c5-431b-a48b-1280f030f798' {
    menuentry 'Ubuntu, with Linux 4.15.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-34-generic-recovery-f690b157-f6c5-431b-a48b-1280f030f798' {
Found memtest86+ image: /boot/memtest86+.elf
menuentry 'Memory test (memtest86+)' {
Found memtest86+ image: /boot/memtest86+.bin
menuentry 'Memory test (memtest86+, serial console 115200)' {
done
$ uname -a
Linux [redacted] 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

