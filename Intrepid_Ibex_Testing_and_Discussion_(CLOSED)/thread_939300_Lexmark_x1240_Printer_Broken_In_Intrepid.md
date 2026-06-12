---
title: "Lexmark x1240 Printer Broken In Intrepid"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-10-05
I have a Lexmark x1240 printer which has always worked in previous versions of Ubuntu, but won't work in Intrepid. The error I get in the printer configuration is:

> idle - /usr/lib/cups/filter/rastertoz600 failed

The howto I've always followed to get this working is here:

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

I am dual booting with Windows, and it does work under Windows so I know it's connected properly. That walkthrough has always worked fine until now so I have no idea why this won't work. :(

Any help will be greatly appreciated, I cannot stand rebooting into Windows just to print. :(

---

### Post by ger_macaco on 2008-10-07
Exactly the same here, with a Lexmark z600.

Using Intrepid and the how-to mentioned.

Any ideas?

---

### Post by jlacroix on 2008-10-07
I'm happy to know I'm not the only one with problems.

---

### Post by ger_macaco on 2008-10-07
OK, after several tries and reboots, now the error message has changed to:

"Can't write page 1 header"

Didn't find any information about it on Google.

---

### Post by jlacroix on 2008-10-07
What did you do to get that far?

---

### Post by ger_macaco on 2008-10-07
Tried umounting and mounting again usbfs and done some reboots before and after doing that.

Also got an update of 119 packages from adept with, mainly, KDE 4.1.2.

Any of those (or both) got me here.

---

### Post by jlacroix on 2008-10-08
Please let me know if you are ever successful in getting this going.

---

### Post by QB89Dragon on 2008-10-25
I've got this same problem (intrepid amd64).

---

### Post by jlacroix on 2008-10-26
Less than a week away until the final release, it doesn't look like this is going to be fixed. :(

---

