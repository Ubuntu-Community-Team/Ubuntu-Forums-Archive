---
title: "Installed Ubuntu on external HD;now internal HD won't boot unless ext HD is turned on"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by MEC407 on 2008-08-27
Good evening,

First of all, I apologize in advance if this question has already been asked dozens of times.  I did try searching for it, using several different search terms, and although I got dozens upon dozens of threads, none seemed to match my situation.

OK, so I've got an internal SATA HD which has Windows XP on it, and an external USB HD, onto which I installed Ubuntu 8.04.  Installation went very smoothly.

When I turn on the computer, I get a boot screen that asks me to choose between Ubuntu and Windows.  That's fine.  No problems there.

Here's the snag: when the external HD is turned off or disconnected, I can't boot at all.  The boot loader (I think that's what it's called?) starts to load, but then it freezes and doesn't go anywhere.  And that's it.  I can't do anything unless I plug the external HD back in and turn it on, restart, and then everything's fine again... I can boot into Windows or Ubuntu as I please.

Is there any way to configure it so that I can boot into Windows even if the external HD is turned off or disconnected?

Thanks in advance for any help you can provide!  And again, I apologize if this is a frequently asked question; I really did try to search for it before asking. ;)  Oh, and I'm a Linux newbie, as I'm sure is obvious, so please be gentle. ;)

---

### Post by xravexheavenx on 2008-08-27
Looks like your MBR is looking for the external or some more grub files are located on the external.  Check your grub settings and please post them.

---

### Post by MEC407 on 2008-08-27
Thanks very much for the quick reply.  Can you explain, in really simple terms, how to check my grub settings?  I tried searching the site for "grub settings" but I'm not coming up with anything useful. :(

---

### Post by MEC407 on 2008-08-28
I just noticed that when I try to start the computer with the external HD turned off or disconnected, not only does the boot loader not work, but I'm also getting an "error 21" -- I assume this is a GRUB error?  I didn't notice it before because the left side of the screen is partially cut off when the computer first starts up.

---

