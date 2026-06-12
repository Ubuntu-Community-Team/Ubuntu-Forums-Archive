---
title: "how to set boot flag during dapper install?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by davious on 2006-06-02
I want to change which partition gets the boot flag during the graphical install but I can't figure out how to.  Does anyone know?

Here's my problem:
I've got a Tecra a4 s211 laptop.
My set up is a dual boot xp/ubuntu with a boot partition, something like:
hda1 /boot *
hda2 /xp
hda3 /

funny thing is, fdisk finds the boot flag on hda2 /xp these days
so fdisk -l looks like
hda1 /boot
hda2 /xp *
hda3 /

but the laptop still boots from grub on hda1 /boot !?

a few months ago, I re-installed breezy and I forgot to change the boot flag back to hda1 and it overwrote hda2's mbr (I guess, or something like that?) and I couldn't boot into windows any longer. the only solution I came up with was to reinstall xp, then reinstall breezy with the correct boot flag selected.

I wanted to make sure that I moved the boot flag to hda1 this time when I install dapper, but with the new graphical interface, I don't know how to do that.

---

### Post by lcg on 2006-06-02
> **davious]I want to change which partition gets the boot flag during the graphical install but I can't figure out how to.  Does anyone know?[/QUOTE]

AFAIK this is not possible with the graphical installer.

[QUOTE=davious]a few months ago, I re-installed breezy and I forgot to change the boot flag back to hda1 and it overwrote hda2's mbr (I guess, or something like that?) and I couldn't boot into windows any longer. the only solution I came up with was to reinstall xp, then reinstall breezy with the correct boot flag selected.[/QUOTE]

Actually, you are mixing concepts here. There is exactly one MBR per disc and it has nothing to do with partitions. However, each partition also has a boot sector (e.g. you can use GRUB in the MBR to "chainload" Windows XP on another partition said:**
> I wanted to make sure that I moved the boot flag to hda1 this time when I install dapper, but with the new graphical interface, I don't know how to do that.
AFAIU, you want to dual boot between XP and Dapper. Do you want GRUB to display a list of installed systems? Or NTLOADER? Or something else entirely?
With that information, I (or someone else) can probably help you better with your problem.

HTH,
Lars

---

### Post by davious on 2006-06-02
so.. I think the exactly problem was that the breezy installer asked if I wanted mbr installed on the /xp partition.. and I mistakenly agreed to it.  But I think the reason it asked me that was because the boot flag was set to the /xp partition.

I want GRUB to display a list of installed systems and I'm used to chainloading to windows.  The problem i had with the breezy install was my first install disaster after a lot of fc and ubuntu dual boot installs.

---

### Post by davious on 2006-06-02
So, I guess my question is. this: Is there a way to know where the mbr will be written, and is it at all related to where the boot flag is?

---

### Post by lcg on 2006-06-03
[QUOTE=davious]So, I guess my question is. this: Is there a way to know where the mbr will be written, and is it at all related to where the boot flag is?[/QUOTE]
I'm sorry, I can't answer that for the graphical installer, I have only used it once for testing and prefer the alternate installer myself. I suppose it defaults to installing GRUB to the MBR, ignoring any partition boot flags. At least that's the default I'd choose since GRUB can boot pretty much out there while others -- especially NTLOADER -- may not be so easy to convince to boot Ubuntu.

HTH,
Lars

---

