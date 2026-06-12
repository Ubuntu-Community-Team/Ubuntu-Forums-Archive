---
title: "Upgrading kernel doesn't change menu.lst"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by ioliver on 2005-02-11
A few people have mentioned that kernel upgrades result in synaptic (apt-get?) automatically updating their menu.lst in /boot/grub

This doesn't happen for me. I have had to edit by hand every time. Not too big a hassle but, from what I read of the plans for a mega-splash system in Hoary, I'd really like to hand control of updating this file back to the install/upgrade process.

Any ideas what I need to check?

I have Ubuntu on /dev/hda2 - could this be the issue?

All suggestions welcome.

Ian

---

### Post by GilGalad on 2005-02-11
What is the output of

$ sudo update-grub

That is the script which is run when a new kernel is installed. Any visible errors?

---

### Post by ioliver on 2005-02-12
sudo update-grub seems to have fixed it.  The only error was that it couldn't find a splash (expected) and it found all my Ubuntu kernels. It's added the automagic bits to the end of menu.lst

Many thanks.

I've moved them to the front, removed the manual kernel entries I'd already got there (other than those for Mepis etc.), and changed kopt by adding vga=0x305 xres=1024x768""800x600 (I need this vga setting to get virtual consoles working and to get a cursor in text consoles - suggestions for why all welcome!)

I guess the big question is, why didn't update-grub get run by synaptic as part of the kernel install? Is there a setting somewhere to say whether Ubuntu thinks I am using grub?

Maybe I need to use synaptic to remove grub and then install it again?

Regards

Ian

---

### Post by GilGalad on 2005-02-12
[QUOTE=ioliver]
I guess the big question is, why didn't update-grub get run by synaptic as part of the kernel install? Is there a setting somewhere to say whether Ubuntu thinks I am using grub?
[/QUOTE]

Have a look at your /etc/kernel-img.conf. In there it says what to do after installing a kernel image. Mine reads:

# Do not create symbolic links in /
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = /sbin/update-grub
postrm_hook   = /sbin/update-grub

---

### Post by ioliver on 2005-02-12
I was missing these two lines -

postinst_hook = /sbin/update-grub
postrm_hook = /sbin/update-grub

I really don't know why, but have added them back in.

Thanks for your help - I'd never have found that file otherwise.

Regards

Ian

---

