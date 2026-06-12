---
title: "Reset before uncompressing kernel"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by jabber42 on 2006-09-23
Hi all,

I just installed the server version of Dapper. I did the install on my main desktop machine and then switched the hard drive I installed to into an old Pentium 200.
The problem I'm facing is that the Pentium computer resets just after getting the "boot" message from Grub, right before the point where I would see "Uncompressing Linux" if I could get that far with booting. Booting on my main desktop computer works fine, just the old Pentium shows the reset problem.

Any ideas?

Greets, Jabber42

---

### Post by K.Mandla on 2006-09-23
Did you install a different version of the kernel? I had a similar problem on an old machine that I used the 686 kernel on. Endless reboots at that same point.

---

### Post by jabber42 on 2006-09-23
No, I'm using the default kernel. I even removed libc-686 (which caused some problems way  back with Hoary).

---

### Post by jabber42 on 2006-09-25
Solved; just in case anyone else has this problem: It indeed originated from using a wrong kernel. The default server kernel seems to be i686. Installing and booting linux-image-386 solved everything for me.

---

