---
title: "3rd Master Hard Disk Error"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by CSEatOSU on 2008-06-06
I took my windows machine, took out the hard drives, put in a new one.  I had some problems installing Hardy from the CD but finally got it running last night.  I did some reboots, updates, and everything was fine.  Shut the computer down before bed.  I woke up this morning, started up the computer, now I get this error message at startup:
```
3rd Master Hard Disk Error
Press F1 to Resume
```
I press F1 and it goes to a screen like this:
```
Intel UNDI, PXE-2.1 (build 082)
Copyright <stuff>

For Realtek <stuff> Gigabit Ethernet blah blah blah

CLIENT MAC ADDR <stuff>

PXE-M0F: No boot filename received

PXE-M0F: Exiting PXE ROM.
```
It does all that about 3 times then I get:
```
Reboot and select proper Boot device
or Insert Boot Media in selected Boot device ans press a key_
```
I NEED SOME HELP!!!

Thanks.

---

### Post by briandu on 2008-06-06
your BIOS is pointing at your network to boot.

Check ur boot settings in BIOS

Do u know how?

---

### Post by CSEatOSU on 2008-06-06
> **briandu said:**
> your BIOS is pointing at your network to boot.

Check ur boot settings in BIOS

Do u know how?

No I don't.  Could you tell me?

---

### Post by CSEatOSU on 2008-06-06
> **briandu said:**
> your BIOS is pointing at your network to boot.

Check ur boot settings in BIOS

Do u know how?

I figured out how to enter BIOS during setup.  I pressed 'Delete' to get in there during setup.  I went to check the boot sequence and it goes:

1st:  Floppy Drive
2nd:  CD/DVD Plextor
3rd:  Hard Drive
Boot From Other Device:  [No]

---

