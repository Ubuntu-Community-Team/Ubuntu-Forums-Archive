---
title: "Dual boot question."
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by Nathan Otis on 2006-11-08
So I have Ubuntu running just fine. I've seen HOWTOs on installing Ubuntu *after* Windows, but how can I set up my current, well running Ubuntu (Dapper) machine to dual boot with 98se or XP? Is a complete format/reinstall required?

Thank you,
n.

---

### Post by ReaderRat on 2006-11-08
Windows loves the MBR (Master Boot Record), and will overwrite your GRUB menu....Ubuntu won't boot. I would reinstall, but that's me. I have a lot of free time on my hands. Check with someone more knowledgeable than I.
Here is a link on GRUB boot menu, etc.
 [[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)

---

### Post by confused57 on 2006-11-08
> **Nathan Otis said:**
> So I have Ubuntu running just fine. I've seen HOWTOs on installing Ubuntu *after* Windows, but how can I set up my current, well running Ubuntu (Dapper) machine to dual boot with 98se or XP? Is a complete format/reinstall required?

Thank you,
n.
You have the best chance of dualbooting by installing Windows on a partition located before the Ubuntu partition, but some people have success installing Windows after:
[http://www.ubuntuforums.org/showthread.php?t=219344](http://www.ubuntuforums.org/showthread.php?t=219344)

Here's the thread I was looking for:
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

---

