---
title: "Install Ubuntu w/o boot manager?"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by Joshuwa on 2006-03-15
Hi,

I'd like to install Ubuntu on a shared computer. However, I'd like it to only boot Ubuntu if a CD was in the drive, or someother method other than a boot selection screen. 

Is there any way I could do this?

This machine will dual-boot Ubuntu and Win2k. Basically, what I want to happen on normal boot is a boot straight to Windows. No grub selection screen, just a typical boot up.

But if a boot cd was in the drive, or maybe a special key was pressed, then it would boot to Ubuntu.

Thanks for any help or info, I really appreciate it!

---

### Post by stuporglue on 2006-03-15
I think you can hit escape at the begining of the Ubuntu installer and get into advanced mode. Go through the steps and just skip the boot loader part.

You could then get the Smart Boot Manager floppy or CD and use that.

You could also just install Grub, then edit the grub config file and set the default  boot to Windows, and set the timeout to 1.

---

### Post by Joshuwa on 2006-03-15
That's a good idea, I never knew about smart boot manager (I've used linux, but am quite the n00b lol).

It seems that Smart Boot Manager requires LILO, which might be too tricky for me to mess with at this point. :/

Thanks for the quick response!

---

### Post by calimarno on 2006-03-15
Hi Joshuwa,
Ubuntu needs a boot manager (windows as well, but it's hidden). You can also hide grub by editing the file /boot/grub/menu.lst and remove the # at the beginning of the line

# hiddenmenu

You can also set win as default and when you want to boot on Ubuntu "Esc" at the boot will show up the grub menu.

I hope I was clear enough.

---

### Post by cotcot on 2006-03-15
I have installed what you want. During ubuntu install answer "no" on the question if GRUB is to be installed in the MBR. Than the installer will ask you where to put it. Answer /dev/fd0 to divert it to the floppy drive. After the ubuntu install you have to set the windows partition active again (you can for that use fdisk or ranish or ultimate boot CD ...) because the ubuntu installer sets the ubuntu partition active by default.
Floppy in will give you the grub menu. If you do not want to select anything just wait untill the default selection switches to ubuntu. You can edit /boot/grub/menu.lst to set the waiting time before starting the default to 0.
Floppy out will give windows without any menu. It is the same as before because you haven't changed the MBR.

---

### Post by Joshuwa on 2006-03-15
> **cotcot]I have installed what you want. During ubuntu install answer "no" on the question if GRUB is to be installed in the MBR. Than the installer will ask you where to put it. Answer /dev/fd0 to divert it to the floppy drive. After the ubuntu install you have to set the windows partition active again (you can for that use fdisk or ranish or ultimate boot CD ...) because the ubuntu installer sets the ubuntu partition active by default.
Floppy in will give you the grub menu. If you do not want to select anything just wait untill the default selection switches to ubuntu. You can edit /boot/grub/menu.lst to set the waiting time before starting the default to 0.
Floppy out will give windows without any menu. It is the same as before because you haven't changed the MBR.[/QUOTE]

This PC doesn't have a floppy drive said:**
> Hi Joshuwa,
Ubuntu needs a boot manager (windows as well, but it's hidden). You can also hide grub by editing the file /boot/grub/menu.lst and remove the # at the beginning of the line

# hiddenmenu

You can also set win as default and when you want to boot on Ubuntu "Esc" at the boot will show up the grub menu.

I hope I was clear enough.

Seems like a better solution, if I'm understanding it correctly.

Through this way, it would always boot normally to windows as usual, but if during the boot I hit 'esc' it would bring up the grub menu?


Thanks again for the solutions :-D

---

### Post by calimarno on 2006-03-16
> Through this way, it would always boot normally to windows as usual, but if during the boot I hit 'esc' it would bring up the grub menu?

Yes.
And windows entry should be the first one in your 'menu.lst' to boot automatically.

---

