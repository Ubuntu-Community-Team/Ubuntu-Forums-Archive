---
title: "Worried before continuing"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by gddeluca on 2008-09-09
OK, total Ubuntu (and Linux) newbie here. I've searched a bit and couldn't find some words of comfort.

I'm planning on installing Ubuntu on an existing Vista system which has a single internal drive split into two main Windows partitions (C: and D:) and it has some free space which was the former recovery partition.

When I go through the Install and let it use the largest available free space it chugs ahead and just before doing the REAL work, it shows a display box summarizing what its going to do. But in there it shows MULTIPLE linux drives being formatted and is using the (to me anyway) cryptic linux names for the drives/partitions.

Why are multiple drives being formatted? I'm paranoid that it thinks its going to use my Windows C: and D: partitions and my Vista system will be blown away.  I can restore it sure, but I don't need that kind of pain.

I assume its putting these multiple partitions into the ONE free area, but I'd like some warm fuzzy feelings before hitting the OK/Proceed/Whatever the button said.  I can't remember now, but I don't think it mentioned the sizes of these partitions, if it had, I could have confirmed what space it was using.

Am I simply too paranoid? I can't believe it would do me in, but ......

George

---

### Post by Pumalite on 2008-09-09
Make space for Ubuntu with the Vista partitioner first.
Format that 'free space' and later use in the installation, going 'Manual'
Backup everything before the installation of any new OS

---

### Post by zvacet on 2008-09-09
> Am I simply too paranoid?

No,but you are uncomfortable with steps you have to take.Read [this]("http://psychocats.s465.sureserver.com/ubuntu/installing") instructions and you will see that is not hard as it look.Good luck!

---

### Post by gddeluca on 2008-09-10
Pumalite: I've already GOT free space on the drive unallocated to any partition. THAT's the space I want Ubuntu to use.

zvacet: Thanks for the pointer. I hadn't stumbled across that particular set of instructions before.  However it shows my problem. When the partitioner come up it has 4 options. I chose the "Guided - Use the largest continuous free space" but the description in the instructions you pointed at describe it as:

The third option (Guided - use the largest continuous free space) will *make Windows as small as possible* and install Ubuntu in the remaining empty space. 

Reading that it sounds like it will SHRINK my windows partitions as much as possible, exactly what I DON'T want. Doesn't largest continuous free space mean just that, FREE space. I don't read that as permission to muck about with my Windows partitions!

No bloody wonder I'm confused.

I gather from all this that I'll have to go to Manual and be really, really careful.

I'm not impressed here, it seems like I could easily have created a major recovery problem for myself here rather than an interesting experiment to have a look at Ubuntu.

No wonder newbies shy away from Linux.  And I'm no computer novice, I've worked an all manner of hardware and software for over 40 years.

George

---

### Post by Pumalite on 2008-09-10
Go 'Manual' and choose the partition in question.

---

### Post by ad_267 on 2008-09-10
Yeah I don't think the installer is really designed for people with an intermediate level of experience. It either expects you to have no idea about partitions and resizes just your main windows partition or you need to use the manual method. The manual method is safest so go with that. Just remember you need to create a swap partition too that's about twice the size of your ram.

---

### Post by gddeluca on 2008-09-11
OK, thanks to everyone who replied, I now have Ubuntu installed where I wanted it and Dual booting works fine. I just have to figure out how to modify grub's menu to make Windows the default (for now) or my better half would throttle me if Ubuntu came up.

I can just hear the "What did you do to Windows Now? !!!"

I'm still a bit disappointed that with a free space area available on a disk, Install couldn't provide an automatic way of using it without going through Manual setup. It should be a no brainer.

Thanks again to all who replied.

George

---

### Post by Pumalite on 2008-09-11
Don't complain when Ubuntu offers you total control with 'Manual'
To make Windows first in boot; edit menu.lst and change 'default=0' to 'default=??' where ?? is the place that Windows occupyies in menu.lst; taking into account that Grub starts counting from 0

---

### Post by ad_267 on 2008-09-11
Or you could just change default to:
```
default saved
```

That way you don't have to keep changing it every time you update your kernel.

---

