---
title: "Autoinstall grub.cfg and txt.cfg"
date: 2021-01-24
forum: Installation &amp; Upgrades
---

### Post by hamstermandk on 2021-01-24
I am trying to create an unattended install but I can't figure out the right syntax for my configs.
I created a custom ISO from ubuntu-20.04-live-server-amd64.iso
I placed "user-data" and "meta-data" in /nocloud

As I can understand I need to both edit grub config and isolinux config.
So I did this, but I can't make it do the unattended install.

/boot/grub/grub.cfg

menuentry "Install Ubuntu Server" {
	set gfxpayload=keep
	linux	/casper/vmlinuz "ds=nocloud;s=/cdrom/nocloud/" quiet autoinstall -
	initrd	/casper/initrd 

/isolinux/txt.cfg

label live
  menu label ^Install Ubuntu Server
  kernel /casper/vmlinuz
  append   initrd=/casper/initrd quiet autoinstall ds=nocloud;s=/cdrom/nocloud/ ---

---

### Post by hamstermandk on 2021-02-10
I found that you ONLY need to change the grub.cfg file.
This is working for Ubuntu 20.04 live server

menuentry "Install Ubuntu Server" {
	set gfxpayload=keep
	linux	/casper/vmlinuz   quiet autoinstall ds=nocloud\;s=/cdrom/nocloud/ ---
	initrd	/casper/initrd

---

