---
title: "Cant Install. Something about WRONG IRQ?"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by WeesLo on 2006-05-10
When i boot my pc with the Ubuntu 5.1 disk in and start the install it gets to a point (still on black screen) that says [COLOR="Navy"]"[61.977712]ohci_hcd 0000;00:13.0 Unlink after no-IRQ? Controller is probably using the wrong IRQ"[/COLOR]

After that it stays on the black screen and i cant do anything, i can type anything i want, but it doesnt move from there.  pLS help:(

---

### Post by brucehohl on 2006-05-10
You should provide hardware information like your cpu, mainboard, etc.  Often this type of issue is related to your specific hardware.  A typical resolution is to add a certain boot parameter such as "boot: live noapic nolapic".  See this post for an example situation: [http://www.ubuntuforums.org/showthread.php?t=53094](http://www.ubuntuforums.org/showthread.php?t=53094)

You might also try Ubuntu-6.06 Flight 7 (beta 7).  These types of problems are often resolved in later versions.  The final Ubuntu-6.06 is due for release about 1 June 2006.

---

### Post by cpaulg on 2006-10-29
I have the exact same problem. I'm trying to install 5.10. I guess I'll download 6.10. Maybe I'll have better luck.

---

