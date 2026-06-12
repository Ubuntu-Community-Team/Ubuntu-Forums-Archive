---
title: "Lucid does not boot"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by schmolch on 2010-04-18
I tried running several Live-CDs of Lucid.

Beta1: Live-CD Menu, Black screen, nothing
Beta2: Live-CD Menu, Boot-Logo, animation stops, nothing
Daily: Live-CD Menu, Black Screen, nothing

System:
AMD-X2, nvidia-gpu.

---

### Post by howefield on 2010-04-18
> **schmolch said:**
> Beta1: Live-CD Menu, Black screen, nothing
Beta2: Live-CD Menu, Boot-Logo, animation stops, nothing
Daily: Live-CD Menu, Black Screen, nothing

Not sure about the Black Screen issues, but for Beta 2, you might try pressing F6 after selecting the language.

Then press escape and remove quiet splash-- from the end of the boot line.

Some have also had success with nomodeset option, but removing quiet splash-- worked for me.

---

### Post by eltonw on 2010-04-18
> **schmolch said:**
> I tried running several Live-CDs of Lucid.

Beta1: Live-CD Menu, Black screen, nothing
Beta2: Live-CD Menu, Boot-Logo, animation stops, nothing
Daily: Live-CD Menu, Black Screen, nothing

System:
AMD-X2, nvidia-gpu.

It's possible that these were: bad downloads, bad burns to laser disk. [FONT="Comic Sans MS"][COLOR="Red"]Did you check the md5sums of the iso images after download, and *BEFORE* burning to the CD / DVD?[/COLOR][/FONT] Also, are these brand new disks or RW? If re-writable, check for scratches or dirt on the disks.

HTH...

---

### Post by schmolch on 2010-04-18
Thanks Howefield.

I removed the quiet-boot and i was able to see that it repeats itself on a usb device descriptor error -110

---

