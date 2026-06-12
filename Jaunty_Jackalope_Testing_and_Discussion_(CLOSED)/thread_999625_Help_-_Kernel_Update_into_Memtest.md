---
title: "Help - Kernel Update into Memtest"
date: 2008-12-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2008-12-02
Yesterday evening I did an update as normal and shutdown my machine. This morning when I came to boot it I found that it went straight into memtest. The grub boot boot line is

root (hd0,0)
kernel /boot/memtest86+.bin
quiet


any ideas on how to recover this?

---

### Post by cszikszoy on 2008-12-02
I would check /boot/grub/menu.lst

Near the top there should be an entry that says "Default      #"

make sure that number corresponds to the correct entry in the grub boot list.

---

### Post by Peter09 on 2008-12-02
Well, looks like I am going to have to get a LiveCD as there is no way I can get it to boot -- unless I can modify the boot line... I wonder why I am the only one who appears to have this problem?

---

### Post by cszikszoy on 2008-12-02
That is strange.  You don't even get the grub menu for a couple of seconds after POST but before memtest starts?  I believe it should show something for about 2 seconds, and pressing escape should show the full grub menu.

Other than that, checking out /boot/grub/menu.lst with a LiveCD should work.

---

### Post by Peter09 on 2008-12-02
All I get when pressing escape is one option
> Ubuntu jaunty (development branch), memtest86+

Where this came from I do not know as everything was working until yesterday evenings update. As already said, if I edit this option I get the details from my first post. 

When I came on to the forum this morning I expected lots of people to be suffering from this, but it appears to me alone....:confused:

---

### Post by plun on 2008-12-02
No problem with this today.

Some facts about GRUB

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Gina on 2008-12-02
> **plun said:**
> No problem with this today.

Some facts about GRUB

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)Useful link - thank you - I'll add that to my website as I haven't got it ATM.

---

