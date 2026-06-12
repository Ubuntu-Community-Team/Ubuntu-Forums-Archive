---
title: "grub-mkrescue error while creatin LiveCD of installed Ubuntu."
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by Kamil_Jwiak on 2013-09-14
Hello Everyone,

I've tried to make a LiveCD of my ubuntu with [THIS ]("https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall")tutorial.
Unfortunatelly, the last step, which is ***Building the CD/DVD*** using **grub-mkrescue** ends with an error.
> Enabling BIOS support ...
Using MULTIBOO.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/multiboot2.mod (multiboot.mod)
Using GCRY_SHA.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/gcry_sha1.mod (gcry_sha256.mod)
Using GCRY_SHA.001;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/gcry_sha256.mod (gcry_sha512.mod)
Using PASSWORD.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/password.mod (password_pbkdf2.mod)
Using SEARCH_F.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/search_fs_file.mod (search_fs_uuid.mod)
grub-mkisofs: Unable to open disc image file
: No such file or directory

According to [kebabbaro post]("http://ubuntuforums.org/showthread.php?t=688872&page=32&p=11549686#post11549686") I've changed *chmod *to *+r* recursively to all files.
```
sudo chmod +r ~/cd/casper/filesystem.squashfs
```
I doesn't change anything. I still get error message posted above :(

Can you help me fix this issue?
I'm using /usr/bin/grub-mkrescue (GNU GRUB 1.98-1ubuntu13) on Ubuntu 10.04 32-bit edition.

Best Regards,
Kamil

---

### Post by sudodus on 2013-09-15
Hi Kamil_Jwiak,

I have no experience of that tutorial. Let us hope that the creator of it will see your thread and help you along that path :-)

But there might be another path to your goal, to make a live system of your Ubuntu. If you would be happy with a live USB drive (instead of a CD), you can try the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971"). You can use it to make a tarball of your installed Ubuntu with all its tweaks, provided it is a basic installation with one root partition and and swap partition.

But you should be aware that Ubuntu desktop 10.04 LTS is past end of life. The current LTS version is Ubuntu 12.04.

---

