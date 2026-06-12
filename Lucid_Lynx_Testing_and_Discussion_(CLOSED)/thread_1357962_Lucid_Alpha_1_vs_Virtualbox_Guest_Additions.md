---
title: "Lucid Alpha 1 vs Virtualbox Guest Additions"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrew.46 on 2009-12-17
Hi,

I have just installed the alpha 1 of Lucid as a guest with Virtualbox 3.0.10_OSE with no problems. (I am aware that version 3.1.2 has just been released just yesterday but I have not installed this yet.) The problem is that despite installing the Guest Additions, which install with no error messages the mouse integration and resizing fail without error on the guest system. Can anybody reproduce this, or better still suggest a fix?

If the newest version of Virtualbox solves the problem this will be an easy fix :).

Andrew

---

### Post by LKjell on 2009-12-17
I use the latest version and it does appear that the mouse is hidden, xrandr works. Share folder is broken.

---

### Post by Merk42 on 2009-12-17
I have the same problem, so I just removed the guest additions.

---

### Post by andrew.46 on 2009-12-17
Hi,

Mouse Integration at least is possible, I found the solution here:

Cursor Control in Ubuntu 10.04 alpha 1 workaround?
[http://forums.virtualbox.org/viewtopic.php?f=1&t=25709](http://forums.virtualbox.org/viewtopic.php?f=1&t=25709)

and it works beautifully on my system.

Andrew

---

### Post by w13rdo on 2010-03-14
I used that fix, and it was fine until feature freeze, then it borked up mightily.  I'll go sans Guest Addons until Beta 1 at least.

---

### Post by grubdude on 2010-03-14
Guest Additions worked fine with me up through the -15 kernel. Ever since -16 was released it hosed my system and can only run in low resolution mode.

I have reverted back to -15 until it is fixed....

---

