---
title: "[SOLVED] 7.10 install issues - APIC"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by boyce1 on 2008-04-26
I've just tried to install gutsy, from a clean install

the first error was 

"[4294672.157000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC"

from the cd install, so i added in the install command line "noacip" and that seemed to fix it. The install completed without a problem.

However, i rebooted my computer, and it came back up with the not connect to io-apic error.

i figured i'd have to use the command again, so i edited the grub boot thing, and put noapic in:

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c9cff81f-f1cf-4cb1-->

i then press enter, then 'b' to boot. it seems ok, i don't get the APIC error, except the Ubuntu startup page seems to freeze. a tiny bit of the bar is there, but nothing happens :(

i tried going into the terminal, and saw the line "...sbin/modprobe 'abormal exit'.

then i am stuck :)

i have no idea what to do/try now, im not that experienced with linux. i would really appreciate any help, thanks.

---

### Post by eyelessfade on 2008-04-26
"acpi" :)

Just one question, why gutsy? Hardy just came out. Try that to see if your problems have gone away

---

### Post by boyce1 on 2008-04-27
The amount of problems i have seen about Hardy, lets get the more stable version working first :)

I heard ASUS motherboards create a lot of problems for Linux? It won't let me disable ACPIC in BIOS, i don't know what to do :(

---

### Post by eyelessfade on 2008-04-28
Ok try to edit your grub again. set noacpi, and remove the "splash" and "quiet" part and boot

if and when it hangs again, post the output.

---

### Post by boyce1 on 2008-04-28
its working ok so far,

before splash, i put "noapic acpi=off", and it loaded up fine.

this is ok now, however occasionally the ubuntu wont load up and i'll have to restart.

apart from that, alls good :)

---

### Post by rahelvey on 2008-04-29
I do hate to sound stupid but so be it.
Where and at what point do I put in noacpi acpi=off?

---

### Post by eyelessfade on 2008-04-30
when grub starts, press Escape to get the menu.
then "e" for edit. at the end of the line you put your no=acpi then enter and "b" (make it permanent with editing /boot/grub/menu.lst

or from the bootcd you write something like ubuntu(not sure press F1-F4 to check) and at the end you write your noacpi

---

### Post by boyce1 on 2008-05-04
i tried many ways of getting it to work, but the best way was to:

press ESC to enter grub boot

in the main system thing, press 'e' and put "noapic apci=off" in the line before 'splash'.

then press enter, then 'b' to boot.

---

