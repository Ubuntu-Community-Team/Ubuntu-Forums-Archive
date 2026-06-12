---
title: "Can install 10.4 using noapci but won't boot"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by p2theg77 on 2010-06-12
Hello and thanks in advance for your help.
 
I can install Ubuntu 10.4 LTS using the "noapci" option. Installation runs, I configure, then restart. I remove the cd and restart to boot from hard drive and I get the "IO-APIC no timer" error again.
 
How do I fix?

---

### Post by p2theg77 on 2010-06-13
> **p2theg77 said:**
> Hello and thanks in advance for your help.
 
I can install Ubuntu 10.4 LTS using the "noapci" option. Installation runs, I configure, then restart. I remove the cd and restart to boot from hard drive and I get the "IO-APIC no timer" error again.
 
How do I fix?
 
Do I need to edit Gurb?  I new to Ubuntu.  I could really use some advice...

---

### Post by p2theg77 on 2010-06-13
> **p2theg77 said:**
> Do I need to edit Gurb? I new to Ubuntu. I could really use some advice...
 
.

---

### Post by alterpinguin on 2010-06-13
if you are right, that your system runs
with the "noapic" option
you can check it at the grub-boot-menu.
Dont wait till the auto-boot starts, press the "cursor-down"-key
then curser-up key to select again the default menu-entry.

Now check this entry with the edit-mode:
press "e" key
check the line starting with
linux   /boot/vmlin.......

and check what options at the end.

go to the end with the curser and
remove there the optins like

quiet
splash

and if the option

noapic

is not there, then type it at the end. Options are separted by space.
Other options of use could be:

nomodeset
that disables the new style of graphic-resolution-change

noapci
that disables all apci, if problem with some powersettings
but if this is off, normaly no powersave-method is possible.

acpi=oldboot
if the old 9.04 ubuntu could poweroff the computer and the new
10.04 cannot, this might help

i915modeset=0
or was it 1, this is only for graphics chips from i915chipset

there are more, you may search for kernel-boot-options.

To start the edited line,
press:
ctrl-x
or
strg-x

that is the same, only some keyboards have different key-caps-text.

If you press Escape, you get back to the old menu. All changes are lost.
Same goes after a restart. This changes are only temporary.

If you get working settings, you have to fix the grub-config.

but that is another story, can be found in the forum too. First step
is for you to find the right settings for your hardware/software combi.

---

### Post by p2theg77 on 2010-06-14
> **alterpinguin said:**
> if you are right, that your system runs
with the "noapic" option
you can check it at the grub-boot-menu.
Dont wait till the auto-boot starts, press the "cursor-down"-key
then curser-up key to select again the default menu-entry.
 
Now check this entry with the edit-mode:
press "e" key
check the line starting with
linux /boot/vmlin.......
 
and check what options at the end.
 
go to the end with the curser and
remove there the optins like
 
quiet
splash
 
and if the option
 
noapic
 
is not there, then type it at the end. Options are separted by space.
Other options of use could be:
 
nomodeset
that disables the new style of graphic-resolution-change
 
noapci
that disables all apci, if problem with some powersettings
but if this is off, normaly no powersave-method is possible.
 
acpi=oldboot
if the old 9.04 ubuntu could poweroff the computer and the new
10.04 cannot, this might help
 
i915modeset=0
or was it 1, this is only for graphics chips from i915chipset
 
there are more, you may search for kernel-boot-options.
 
To start the edited line,
press:
ctrl-x
or
strg-x
 
that is the same, only some keyboards have different key-caps-text.
 
If you press Escape, you get back to the old menu. All changes are lost.
Same goes after a restart. This changes are only temporary.
 
If you get working settings, you have to fix the grub-config.
 
but that is another story, can be found in the forum too. First step
is for you to find the right settings for your hardware/software combi.
 
That fixed it!  I deleted the "search no floppy" string and added the "noapic". Thank you so much! Now I just gotta figure out how to get wireless internet thru a wireless usb adapter... :KS I know the fix is just temporary but is there a quick way to edit grub to make change permenant?  I'm coming straight from windows with no knowledge whatsoever.  Sorry for being lazy and thanks again.

---

