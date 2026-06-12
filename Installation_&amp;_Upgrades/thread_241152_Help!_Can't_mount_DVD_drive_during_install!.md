---
title: "Help! Can't mount DVD drive during install!"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by BrandonTheBlack on 2006-08-21
I am attempting to install the 64-bit edition of Dapper 6.06 Desktop. The installer loads ok, but when I choose to install it, it gets hung up at a certain point. So I tried checking the CD for errors. It tells me that it can't find a CD drive!

It's not just Dapper 6.06 that's doing this. Fedora and Slackware are doing the same thing, even the 32-bit version of Dapper. I'm not sure what could be causing this, because the drive works fine with Windows (installed from the drive less than 3 days ago).

The drive in question is a Benq DVD DC DQ60, an IDE DVD-RW drive with the lastest firmware installed. So, I ask you more knowledgeable folk, what is going on? Why won't any version of Linux detect my drive?

---

### Post by VirtuAlex on 2006-08-21
try alternate cd...

---

### Post by Fass on 2006-08-21
I've seen such behaviour sometimes is due to DMA weirdness (several distros' CDs not recognising the drive after having loaded the installer), so this might be worth a shot.

You'll have to pass a parameter as you boot the CD that either turns DMA on or off... now, if I could just remember what it was... alas, google fails me. I think that if you choose the "expert" install you can choose if you want dma on or off. Try that! Or have a look in the parameters you can pass to the bootloader to see if you can find one that controls dma.

Also, experimenting with the "noapic nolapic acpi=off vga=771 pci=noacpi" settings is a suggestion, too.

---

