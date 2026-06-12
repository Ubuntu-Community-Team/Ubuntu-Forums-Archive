---
title: "&quot;Unknown Interrupt or Fault&quot; EIP"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by ImmortalGrey on 2007-02-25
I've downloaded and burned the ISO for the desktop edition of 6.10, and when I boot my system from the CD, I get the main menu just fine, but when I try to Start/Install, I get an odd error:

"Unknown Interrupt or Fault at EIP *Insert several numbers here*"

The disc will still run memory tests, but everything else returns with this error.

How do I get past it?

I'm on Windows XP now, with a Compaq Presario desktop... x86 platform.

---

### Post by Kateikyoushi on 2007-02-25
Did you run the disc check ? What speed did you use to write the disc ?

---

### Post by ImmortalGrey on 2007-02-25
> **Kateikyoushi said:**
> Did you run the disc check ? What speed did you use to write the disc ?

Highest possible, not sure what it was, but it was the exact settings off of the Ubuntu site..


And I've resolved this, I guess the solution was to go F6 for more options, and type in "acpi=off" at the end of the line of text.  Don't know how I missed that after searching the web for hours, but yeah.

And the disc check was affected by the error above as well.

---

### Post by Kateikyoushi on 2007-02-25
That makes it interesting, the disc check was effected, now I wonder where should I begin eliminating the possibilities in such cases.

---

