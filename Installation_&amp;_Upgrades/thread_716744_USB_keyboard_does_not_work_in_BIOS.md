---
title: "USB keyboard does not work in BIOS"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by vintagecandy on 2008-03-06
I just bought a new Dell PC with Vista and am trying to install Ubuntu. However, I can't get the computer to boot from a CD. I also can't get into the BIOS to change the boot sequence because my keyboard doesn't seem to work at all until Windows starts. I searched around a bit and found that USB support is often not supported by default in BIOS, but of course I can't get into BIOS to enable it since the keyboard doesn't work. There is also no PS/2 port at all so I can't try a PS/2 keyboard. Dell's customer support is retarded and they just offered to send me a new keyboard, but I'm fairly certain that's not the problem. Does anyone have an idea? I'd appreciate any suggestions.

---

### Post by Mithrilhall on 2008-03-06
I would try a different USB port and a different keyboard if you haven't already tried that.

---

### Post by mozetti on 2008-03-06
If your USB keyboard isn't being recognized by the BIOS, then the only way I know of is to use a PS2 keyboard to access the BIOS to make the change. It baffles me that manufacturers would sell a PC with a USB keyboard, but not turn on USB-keyboard access in the BIOS from the start.

Don't have any friends or family that could "borrow" a PS2 keyboard from work for the night? Have a USB->PS2 adapter? (not sure if that will work though, but it's worth a shot).

---

### Post by wpshooter on 2008-03-06
Are you sure that your Ubuntu CD is a bootable CD ?  Did you burn the ISO as an image and NOT copy as data ?

Most default boot orders would be 1) floppy drive 2) CD ROM drive 3) hard drive.

---

### Post by vintagecandy on 2008-03-06
> **mozetti said:**
> If your USB keyboard isn't being recognized by the BIOS, then the only way I know of is to use a PS2 keyboard to access the BIOS to make the change. It baffles me that manufacturers would sell a PC with a USB keyboard, but not turn on USB-keyboard access in the BIOS from the start.

Don't have any friends or family that could "borrow" a PS2 keyboard from work for the night? Have a USB->PS2 adapter? (not sure if that will work though, but it's worth a shot).

Borrowing a PS/2 keyboard wouldn't help because there's no place to plug it in.  Or do you mean to plug a PS/2 keyboard into an adapter and then plug that into my computer's USB port? 

> **wpshooter said:**
> Are you sure that your Ubuntu CD is a bootable CD ?  Did you burn the ISO as an image and NOT copy as data ?

Most default boot orders would be 1) floppy drive 2) CD ROM drive 3) hard drive.

Yes, it's definitely a bootable CD.

---

### Post by wpshooter on 2008-03-06
A bit extreme but probably reflashing BIOS would setup CD-Rom drive ahead of hard drive in boot sequence !!!

---

### Post by mozetti on 2008-03-06
> **vintagecandy said:**
> Borrowing a PS/2 keyboard wouldn't help because there's no place to plug it in.  Or do you mean to plug a PS/2 keyboard into an adapter and then plug that into my computer's USB port?

No, I meant using a PS2 port on the computer. My gosh that's even worse than I thought -- they sold you a computer that can only access the BIOS using a PS2 keyboard, but didn't include a PS2 port? I'd just call the support line and try to get bumped up to a supervisor.

Or maybe you can call and say, "my computer keeps giving me an error about having an unbootable disc in the cdrom drive. How can I change the boot order in my BIOS so it doesn't check the cdrom drive?"

That will force them to get you into your BIOS, if there is any way.

---

