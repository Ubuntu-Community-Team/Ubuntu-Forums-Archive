---
title: "Does portable USB Ubuntu write to hard drive?"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2011-06-20
Hello,

If I have Ubuntu installed on a USB drive and run it on a PC (not installing to the PC...just running the Live version), is anything at all written to the host PC's hard drive? I don't want the host PC's hard drive to be written to at all for security purposes. I'd be using Firefox, LibreOffice, and other apps that come with the Live USB version.

Thanks!

---

### Post by Allavona on 2011-06-20
I have a friend who disconnects his HDD and uses a 32GB USB drive that has Linux installed. This way he ensures that no info is written to his HDD. MacPup E17 is what he's using, I think.

---

### Post by mlentink on 2011-06-20
You could write to it if you mount it. Which means you would have to want to write to it.

---

### Post by clay7 on 2011-06-20
Thanks for the replies and info!

So, unless I mount a drive, no temp or system files are written to a hard drive? Or to a swap portion of a drive?

---

### Post by oldfred on 2011-06-20
If you do not want it to use swap you may have to set the noswap parameter on boot. Many liveCDs use swap to speed up an install, so they mount swap if found on the hard drive. If you have a lot of RAM on the computer it may not use swap anyway.

---

### Post by clay7 on 2011-06-20
Good deal...thanks to all! Marking as solved.

---

