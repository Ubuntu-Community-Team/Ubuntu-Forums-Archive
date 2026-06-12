---
title: "How to boot windows first in dualBooting ?"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-10-29
I am using ubuntu 11.10 and windows 7 in dual booting.
Ubuntu boot first, how can I set window to boot first ?

---

### Post by awam66 on 2011-10-29
Download and install "Startup Manager" (it is in the repositories).This allows you to set what starts first and the resolution of the grub screen.
HTH

---

### Post by hoboy on 2011-10-29
> **awam66 said:**
> Download and install "Startup Manager" (it is in the repositories).This allows you to set what starts first and the resolution of the grub screen.
HTH

I have just installed it then set default operating system to windows e that then reboot, but still launching ubuntu first.
does this work on ubuntu 11.10 ?

---

### Post by raja.genupula on 2011-10-29
look at my signature and get grub customizer. open it and from preference option you can do what ever you wanna do .

all the best

---

### Post by garvinrick4 on 2011-10-29
> I have just installed it then set default operating system to windows e that then reboot, but still launching ubuntu first.
does this work on ubuntu 11.10 ? Good question, does setting it to Windows and doing a sudo update-grub make it work in a proper fashion?
## That grub-custimizer is a good looking GUI tool it looks like, can do about anything with
grub from post above me.
## There is a setting in /etc/default/grub that chooses the boot order by changing a number
and saving hoboy but takes a bit of reading and learning. Easy but does take some learning.
Look under /etc/default/grub in this documentation below. At one time was the only way.
Now 3 or 4 different methods from new gui apps.

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by awam66 on 2011-10-29
> **hoboy said:**
> I have just installed it then set default operating system to windows e that then reboot, but still launching ubuntu first.
does this work on ubuntu 11.10 ?

Sorry don't know about windows choice as I don't have it, but it works for my various Ubuntu versions.

---

### Post by Mark Phelps on 2011-10-31
> **garvinrick4 said:**
> Good question, does setting it to Windows and doing a sudo update-grub make it work in a proper fashion?

Not on my PC with 11.10, or with recent updates to 11.04. It claims to work, but when you reboot, the old default selection is still there.  I think it's not able to handle the nested kernels now.

Have switched over to using Grub Customizer and found that to work well.

---

