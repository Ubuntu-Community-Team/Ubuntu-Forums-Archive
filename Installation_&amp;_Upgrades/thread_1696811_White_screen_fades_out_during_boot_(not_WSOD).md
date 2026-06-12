---
title: "White screen fades out during boot (not WSOD)"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by philipradams on 2011-02-27
Hello, I am returning to Ubuntu after several years.  My last installation was 7.04 and I was a pretty basic user then.  Now, I am running 10.10, and I am having an interesting issue.

During boot, right after POST and right before the bootloader screen with the progress bar and Ubuntu logo, my monitor goes completely white.  However, almost instantaneously it starts to fade to black, and eventually goes away.  I know it's not the white screen of death that I've heard about, because next I can log in and use my computer just fine.

If anyone could point me in the right direction to try to fix this, I would greatly appreciate it.  Even filenames related to Ubuntu boot would help, as I'm still learning.

Thanks!

---

### Post by zenwalker on 2011-02-27
Does the same happens even when you disable the splash in grub?

---

### Post by philipradams on 2011-02-27
> **zenwalker said:**
> Does the same happens even when you disable the splash in grub?
Yes, it does.  I have deleted "quiet splash" from /etc/default/grub, because I like the looks of the commands running across the screen during boot, and the white screen persists.

Thanks for getting back to me so quickly!

---

### Post by Hedgehog1 on 2011-02-28
> **philipradams said:**
> 
During boot, right after POST and right before the bootloader screen with the progress bar and Ubuntu logo, my monitor goes completely white.  However, almost instantaneously it starts to fade to black, and eventually goes away. 

The flash is the video memory getting intialized after the boot logo from the bios (the logo that says 'Dell' or 'Asus' or 'MSI').

Making it stop is an interesting challenge.

Do you know what mother board (or PC model if not hand built) you have?  An if you are running off the on-board video or do you have a discrete video card (and if so , what kind?).

I don't know that this can be solved; but it is a fun brain teaser to try.

:KS

---

### Post by philipradams on 2011-02-28
> **Hedgehog1 said:**
> Do you know what mother board (or PC model if not hand built) you have?  An if you are running off the on-board video or do you have a discrete video card (and if so , what kind?

My motherboard is an Intel D865PERL, and I am running a Visiontek Radeon 2600 Pro.  It's a computer that I built myself.

---

