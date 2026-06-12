---
title: "Ubuntu freezes at splash screen when booting from USB"
date: 2014-10-12
forum: Installation &amp; Upgrades
---

### Post by Henkus on 2014-10-12
Hi to anyone reading this, so, a couple of months back a computer of mine and wouldn't boot anymore: windows was corrupted. Since I didn't use the machine much I procrastinated fixing it but there are a lot of photos on that machine that I would like to retrieve, now I know I can just take the harddrive out and connect it to the MOBO of my current computer but I really would rather not have to deal with any hardware.

To access the files on my harddrive I installed Ubuntu on a flashdrive, and tried booting my computer from it, but it's stuck at the Ubuntu splash screen, and by Ubuntu splash screen I mean the Ubuntu logo with a loading bar which appears if you choose the "Try Ubuntu without installing" option after booting from a flashdrive.
I can still move the mouse pointer but the loading bar isn't moving at all.

If anyone has any idea what the problem may be and/or how I could fix it, please tell me.

Thanks in advance!

---

### Post by grahammechanical on 2014-10-12
Are you sure it was Windows that was corrupted and not the hard disk that was failing? You can try running the live session with some user modified boot parameters.

Look at section 6 - F6 Other Options. Try nomodeset or a combination of those options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by Henkus on 2014-10-12
Alright, so I tried a couple of those options but to no avail, then I tried to boot from the harddrive again so I could look up the error I was getting which made me think windows was corrupted, but now once I tell it to boot from the harddrive I just get a black screen with no text and nothing happens. Does this mean my harddrive is broken? If so, is there any other way I can retrieve the data?

---

### Post by Vladlenin5000 on 2014-10-12
HirensBootCD (or something like that) is a bootable CD with many diagnostic & repair tools for drives, among many other goodies.

---

