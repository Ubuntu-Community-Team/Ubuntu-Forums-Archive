---
title: "Grub prevents disk error checking?"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by deleyd on 2008-04-18
I can only guess this problem is caused by Grub, but I really don't know.

I have Vista & Ubuntu on HP laptop. In Vista I want to run a disk error check, with "Automatically fix file system errors" checked. I get the ususal, "Windows can't check the disk while it's in use. Do you want to check for hard drive errors the next time you reboot?" I click, 'Schedule disk check'.

Then I reboot. And it doesn't perform the disk check. It just boots normally. I can only guess that maybe Grub is the problem. I believe there are problems with the files on the hard drive, or maybe the hard drive itself, but I can't get this disk checker to run on boot. (Not even sure where to ask Grub questions.)

---

### Post by Herman on 2008-04-18
Try running CHKDSK /R from a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") then, if you have a Windows Installation disc.

---

