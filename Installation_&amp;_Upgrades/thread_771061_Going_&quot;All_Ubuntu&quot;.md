---
title: "Going &quot;All Ubuntu&quot;"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by y0diggity on 2008-04-27
I currently use a laptop that dual boots between Windows and Gutsy. I've decided to go to strictly linux. 
[LIST]
[*]How do I go about doing this?
[/LIST]
[LIST]
[*]What can I expect to be a pain in the butt?
[/LIST]
[LIST]
[*]How about my current linux configuration; will it change?
[/LIST]
[LIST]
[*]What about my Windows files; will I lose them?
[/LIST]
Thanks in advance!

---

### Post by overdrank on 2008-04-27
> **y0diggity said:**
> I currently use a laptop that dual boots between Windows and Gutsy. I've decided to go to strictly linux. 
[LIST]
[*]How do I go about doing this?
[/LIST]
[LIST]
[*]What can I expect to be a pain in the butt?
[/LIST]
[LIST]
[*]How about my current linux configuration; will it change?
[/LIST]
[LIST]
[*]What about my Windows files; will I lose them?
[/LIST]
Thanks in advance!
Hi and you can use gparted via the live cd and delete your windows partition. Before this you can move your data from windows to ubuntu. Then with the live cd and gparted you can delete you windows partition and use this to store data for previous installs or resize you Ubuntu partition to increase it size.

---

### Post by vanadium on 2008-04-27
It is not that easy, in my opinion, but quite possible.

> I currently use a laptop that dual boots between Windows and Gutsy. I've decided to go to strictly linux.

    * How do I go about doing this?

As overdrank sketched: deleting Windows partition, move Ubuntu partition to front of disk (time consuming operation), update /boot/grub/menu.list (grub)

> 
    * What can I expect to be a pain in the butt?

You will see when you get there. With enough experience and no mistakes, there won't be pain in the but. If there is, it is the moving of the Ubuntu partition, which will take a lot of time and has not a 100% of success (95% perhaps).
> 
    * How about my current linux configuration; will it change?

Not if you keep your current Ubuntu installation. However, a much faster and easier way to go would be a clean reinstall, and that is what I would recommend.
> 
    * What about my Windows files; will I lose them?

External storage is cheap now, and if you do not have that already, you should urgently obtain it to saveguard your personal files. Operating systems can be reinstalled. Personal data files, when lost, are lost forever.

---

