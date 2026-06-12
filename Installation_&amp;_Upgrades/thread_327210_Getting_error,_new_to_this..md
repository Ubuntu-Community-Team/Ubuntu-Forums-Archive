---
title: "Getting error, new to this."
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by Gonzo_PhD on 2006-12-28
Hi, I installed Ubuntu 6.06 LTS with ease on my old computer, but now on my new one I get an error before the live boot that says:

"Failed to start X server(your graphical interface). It is not set up correctly. Would you like to view the X server output to diagnose the problem?"

But I don't know what to do from there. Could it be a hardware problem? I have RAID 0, could that too be the problem?

Hardware:
AMD X2 4200+
Gigabyte AM2 motherboard
Corsair RAM
nVidia 8800 GTS

---

### Post by taurus on 2006-12-28
Actually, it's more like a graphic card problem.  Therefore, you can either use the safe mode option at the beginning to see if LiveCD can start or download and use the alternate CD to install it then.

---

### Post by Gonzo_PhD on 2006-12-28
Thanks.

After that, is there a nVidia driver I could download to fix it?

---

### Post by taurus on 2006-12-28
Yes.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by blackmh on 2006-12-28
In install menu hit F4 for vga modes. Because I have same problem, the only mode that works for me is 1024x786, 32 bit so I suggest you to try that one first. After you install ubuntu, you will have to install nvidia drivers through command line because same error will appear.

---

### Post by Gonzo_PhD on 2006-12-28
Thanks for the help.

---

### Post by Gonzo_PhD on 2006-12-28
I've got another question, this is my first time with a computer with RAID 0 and I'm trying to dual boot with XP, when I try manually partition the drives it shows both drives as "unallocated". What do I do?

---

### Post by paridoth on 2006-12-28
i'm not sure but i think linux doesn't support raid 0 you might want to search the forums before you take my word on it though

---

