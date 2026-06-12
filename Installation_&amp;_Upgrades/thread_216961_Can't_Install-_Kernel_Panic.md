---
title: "Can't Install- Kernel Panic"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by freewaybear on 2006-07-16
I'm trying to install Ubuntu 6.06 LTS on my new box, but as soon as I boot the disk, I get a"Kernel Panic-Not Syncing:Fatal exception in interrupt" message. I've read similar threads on the forums, and tried the acpi=off, noapic, nolapic options, and get the same result. I have an Athlon XP 3200+ with an ECS KT600-A mobo. Thanks in advance for any insight.](*,)

---

### Post by Choad on 2006-07-16
my mates semperon 64 used to get that message with the old breezy install disks.... but then a few months later it didnt.

was totally bizzare! didnt even have to turn acpi off or anything

try using the integrity checking tool of the install disk :)

---

### Post by freewaybear on 2006-07-16
Thank you for replying. Actually, I did try to do the integrity check, but the same message pops up before it gets far enough along to start the check. I also tried install disks for Hedgehog and Breezy, same problem. It's the same whether I try to install or run the live disk. If you or anybody else has any other ideas, I'd be eternally grateful. I'm about ready to dropkick this box!:???:

---

### Post by andlinux21 on 2006-07-19
I think its either the video card or the hard drive i am not sure i am having the same problems but only after i switched video cards out.  I will get back to you later when i solve my own problem.

---

### Post by freewaybear on 2006-07-20
I had just come to the conclusion that it was definately a hardware issue, but I was thinking RAM. But, the RAM I have functioned perfect in the machine I pulled it from. I will try swapping video cards, it never occured to me until you mentioned it. I'll try it after work tomorrow, and post the outcome here. Thank you for your suggestion, I was beginning to think no one had any interest in my problem.:D

---

### Post by freewaybear on 2006-07-20
I don't know if this applies to your specific problem, but mine occurs whether I try to run a live disk as well as trying to install, which makes me think that the hard drive isn't the issue. Good luck, though, and thanks for responding to my post.

---

### Post by rhelvey on 2006-07-27
Greetings, I am trying to overwrite gnome breezy on a XP dual boot box [Athlon XP 3000+ 512DRAM, ATI Radeon Xpress 200]. I thought I might try Dapper Kubuntu. I get to the initial install screen then when trying to install I get a similar message to above "<0> kernel panic-not syncing Attempted to kill init" Any idea how to move forward with the install?

Thanks,

rhelvey

---

### Post by freewaybear on 2006-07-28
Well, rhelvey, I hope for our sakes someone out there has some insight on these problems. For the one or two people following this thread, I forgot to get back here with my results from swapping video cards. It didn't help. On a side note, I also tried a windows 2000 install, just for testing purposes, but it BSOD'ed right away, so it is most certainly a hardware issue not suited for this forum, but I'm getting desperate. Besides, I want Ubuntu on this rig, it's all I've used for 2 years, and that's all I'll settle for. I know there is someone out there that can help me and Rhelvey. Thanks in advance.

---

### Post by magog45 on 2006-07-28
I'm having the same problems with an asus p2b-d, but it is very inconsistent, sometimes the live disk boots and sometimes the panic. I've used every possible install version and had Damn Small Linux and FreeBSD on the same machine so I don't think it is the hardware. Pure Debian also does the same thing so I'm inclined to think that there is something in the install process as many seem to be having similar problems then magicly after numerous attempts the install works. Not exactly a good way to build confidence in a distro although I like Breezy, it installed on the computer I'm using now no problem but also failed on the one I'm building. Somewhere in the hardware recognition there is a problem with certain architectures is all I can think of. I'd hate to have to put windoze xp on the new machine.

---

