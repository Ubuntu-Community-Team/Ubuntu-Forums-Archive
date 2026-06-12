---
title: "Accidently deleted Win7 from boot menu"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by fl0sT on 2011-06-25
I had a win7 installed on my system first. Then I installed Ubuntu and added grub2 boot option with win7 utility program EasyBSD. But then I accidently deleted win7 boot option from windows loader menu.

Now I can only chose to load Ubuntu. How can I restore Win7 loading option?


ps. I have Win7 option in grub2 but it returns me to the previous screen, from which I have deleted win7.

---

### Post by Mark Phelps on 2011-06-25
You will need to restore the Win7 boot loader files -- which you can do by running Startup Repair three times from a Win7 Repair CD.

Since you probably don't have one of those, and didn't take the trouble BEFORE installing Ubuntu to make one of those, go to the link below, select and download, and then burn, the proper Win7 Repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then boot from that CD and run Startup Repair -- three times.

---

### Post by fl0sT on 2011-06-25
Thanks.

Although the link you provided doesn't have a link to the file
> Downloads have suspended pending copyright clarification.

For those who might have similar problem, I found ISO's here
[http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/)

---

