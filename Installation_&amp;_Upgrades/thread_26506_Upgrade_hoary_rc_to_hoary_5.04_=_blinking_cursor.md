---
title: "Upgrade hoary rc to hoary 5.04 = blinking cursor"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by Lachlan on 2005-04-13
I have just upgraded hoary rc (kubuntu) with default repositories to hoary 5.04.
The upgrade process went fine and the upgrade appeared to be successful.I used the computer for 2 hours after the upgrade,(no problems) then went to bed.
               On booting into kubuntu today I got something like this: Initialising kernel: Loading kernel : Loading ramdisk,load below 4MB kernel overwrite is possible.
A blank screen and flashing cursor followed and that was it.

Cheers

Lachlan

---

### Post by nad on 2005-04-13
You've noticed that the kernel upgrade does not take effect until a reboot.

Do me a favor and check the available space of your /boot partition. If you have only one hard drive, this will be ' df -h /dev/hda* ' at the terminal prompt after a recovery login.

Dan M

---

### Post by Lachlan on 2005-04-13
Thanks for the reply.
I have swap (500MB) and a /root (4GB) partitions.Don't know how to boot into recovery login.

Lachlan

---

### Post by nad on 2005-04-13
Wartys' default /boot/grub/menu.lst was to hide the boot menu.

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

I thought that Hoarys' default was to show the menu. Anyway, as you start the computer and the bios info or splash screen is finishing, hold the ESC key down to see the grub menu list. Use the arrow keys to highlight the latest Recovery option and enter. You will be asked for the root password (what if it is not set...hmmm) to start a recovery session.

I've helped with errors where the disk is full after an upgrade. Deleting unnecessary files is all that is needed (why are all deb packages kept locally by default? apt-get autoclean).

Not sure if this is your problem, but it is worth a shot.

Dan M

---

### Post by Lachlan on 2005-04-14
Holding down the ESC key achieves nothing,no recovery mode,just a flashing cursor.

Lachlan

---

### Post by nad on 2005-04-14
Possible bad memory chip.

Dan M

---

### Post by Dr Gonzo on 2005-04-14
Can you boot the live cd?

---

### Post by Lachlan on 2005-04-14
Dan M : I have 3 other distros on this drive,so I don' think it's memory.

Dr Gonzo : I downloaded and burnt the cd.

Lachlan

---

### Post by nad on 2005-04-14
From one of your other distros, how is ubuntus' grub config'd?

---

### Post by Lachlan on 2005-04-14
Apologies all round,I have no grub,I used Lilo.When I tried to use grub during the original installation,grub destroyed the mbr.

Lachlan

---

