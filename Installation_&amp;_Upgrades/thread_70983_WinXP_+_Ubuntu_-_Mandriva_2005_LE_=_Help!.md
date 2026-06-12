---
title: "WinXP + Ubuntu - Mandriva 2005 LE = Help!"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by FroGGerUK on 2005-10-01
Here's where I am. 

I'm currently, and predominately, a Windows XP user who *really* wants to move away from Windows. 

Some time ago, I installed Mandriva 2005 LE and we really *didn't* get on. However, after tying Ubuntu Live it looks like *this* is the one I've been looking for.

However, I'm still a *very* new newbie and I'm not really sure how to go about installing a dual-boot Ubuntu/WindowsXP box on a system that already has Mandriva installed :-(

I'm not at all really sure how to go about this, so *any* input from you guys would be *really* appreciated.

Step-by-step even more appreciated :-)

Thank you.

---

### Post by aysiu on 2005-10-01
You may find this helpful:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Instead of "free space," though, just use the Mandriva partition. And since you already have that carved out, you don't need to do the resizing either.

---

### Post by FroGGerUK on 2005-10-01
[QUOTE=aysiu]You may find this helpful:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Instead of "free space," though, just use the Mandriva partition. And since you already have that carved out, you don't need to do the resizing either.[/QUOTE]
When I look (in Windows) at 'Computer Management' -> 'Disk Management' I can see three partitions (used by Mandriva, I guess) that are 5.85/1.07/5.12GB in size. Should I select "Delete logical drive" on all three before attempting to install Ubuntu?
And what about the boot the Grub loader? Will it replace the one installed by Mandriva?
Thanks for your help.

---

### Post by aysiu on 2005-10-01
[QUOTE=FroGGerUK]When I look (in Windows) at 'Computer Management' -> 'Disk Management' I can see three partitions (used by Mandriva, I guess) that are 5.85/1.07/5.12GB in size. Should I select "Delete logical drive" on all three before attempting to install Ubuntu?[/quote] No. Ubuntu can overwrite those.

> 
And what about the boot the Grub loader? Will it replace the one installed by Mandriva?
Thanks for your help. Yes, it will. Follow the instructions I linked to (*sans* resizing to get the free space).

---

