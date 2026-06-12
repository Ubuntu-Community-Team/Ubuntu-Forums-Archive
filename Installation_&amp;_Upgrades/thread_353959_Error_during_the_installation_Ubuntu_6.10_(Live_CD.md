---
title: "Error during the installation Ubuntu 6.10 (Live CD)"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by cronoz on 2007-02-05
Hi! I've downloaded Ubuntu 6.10 Live CD (ubuntu-6.10-desktop-amd64.iso) I've burned the image, reboot my computer, and when i select Start or Install Ubuntu i got this error:
[http://img176.imageshack.us/my.php?image=p1010233uz2.jpg](http://img176.imageshack.us/my.php?image=p1010233uz2.jpg)
[I].
Decompressing Linux...done.
Booting the kerlen.
[ 35.385457] Kernel panic - not syncing: IO-APIC + timer doesn't work! Try usi
ng the 'noapic' kernel parameter
[ 35.385490] _
[/I]
 MY computer: AMD X2 4600, ASUS M2N-E, 2 x DDR-2 1GB Kingston, Nvidia 7950GT 512MB and HDD SATA2 250GB.

Thx for your help.

---

### Post by kebes on 2007-02-05
On the initial install screen, before starting the install, hit the key for "more options" (I think it's F6), and then add kernel boot flags. In particular you need to add:
noapic

Then press enter and the kernel should boot and the install should proceed. I believe "noapic" is all you need, but if that doesn't work, you can add "nolapic" and/or "acpi=off" and see if that works.


(Note: I've done an install on that exact hardware combo so I know it can be done!)

---

### Post by cronoz on 2007-02-05
it works but then i get a screen with the Ubuntu logo & letters in black and grey :S and a bar in the bottom in grey and black too. like if it was working in a secure or non-graphic way. do you understand me?

---

### Post by kebes on 2007-02-05
Hmm... does it eventually boot into the LiveCD environment?

You could try using the "Alternate CD" to install, which uses a simpler text-based installer. (The final install still has a the normal graphical environment.)


Note that I did installs on very similar hardware, but I was installing Ubuntu 6.06 LTS (Dapper Drake). You might want to try that version instead. (You can upgrade it to the latest version once installed.)

---

### Post by cronoz on 2007-02-05
ok i'll try 6.06 LTS thx mate :)

---

### Post by cronoz on 2007-02-06
I've start Ubuntu 6.06 LTS but it crashes when i select Install and Start Ubuntu :(

---

### Post by kebes on 2007-02-06
> **cronoz said:**
> I've start Ubuntu 6.06 LTS but it crashes when i select Install and Start Ubuntu :(

Try adding the "noapic" option, as mentioned a couple of posts before... See if that works.


Another note: Does the crash always occur at the same spot or is it somewhat random when it happens? I recall that with that particular motherboard, I initially had some OCZ RAM in it, but the install wouldn't work because it turns out that the RAM needed a rather high voltage (2.1 V or something), whereas that motherboard only reliably supplies up to 1.8 V (or whatever). I switched the OCZ RAM for Corsair RAM and it worked perfectly.

You said that your RAM was Kingston, so I don't think there should be a problem... (Does it say what voltage it is rated for on the RAM?) However bad RAM or a mismatch between RAM and motherboard can often lead to random crashes.

Another thing to try would be to update the motherboard BIOS. Maybe there's a known bug.

---

