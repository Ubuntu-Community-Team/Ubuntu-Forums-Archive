---
title: "Installation on multiple hard drives"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by rerendered3 on 2008-08-06
Here is an interesting challenge.

I'm planning a multiple-user computer with multiple hard drives and had the idea of putting a unique installation on each hard drive (all Linux, of course). My idea is to have GRUB (or maybe even BIOS) give a choice of which drive (or OS) to boot from. Any good ideas?

---

### Post by SarahKH on 2008-08-06
That's easy :)  After the first time skip the bootloader bit of the install (if possible) and just create one spankingly large /boot/grub/menu.lst file with all the installed kernels in it pointing to the various drives and such.

Of course, Linux is by default a multi-user operating system, so it's perfectly possibly to have tens, hundreds (thousands even on a big enough box) of users on the same OS... accessing the machine at the same time.  Unlike Windows you can split the OS as you wish so /home/<user1> can be on /dev/hda and /home/<user2> on /dev/hdb and so on.

So, what your suggesting is quite possible, bit fiddle what with all the automated installers for various distro's but quite dooable.  But other than testing different distro's out, why go to that lengths to just do simple multi-user?

---

### Post by rerendered3 on 2008-08-08
Why? Mostly so that each install can have it's own apps list, and to protect the users from each other's tweaking (Linux *can* be broken).

---

### Post by rerendered3 on 2008-08-08
...and to prove it can be done.

---

### Post by SarahKH on 2008-08-17
> **rerendered3 said:**
> ...and to prove it can be done.

Fair enough :)

It can be done, as I said, install each distro to a drive and combine the resultant GRUB statements in to a single one sitting where ever you install the first distro too.   That should do it. They'll each boot their own kernel and see /dev/X as their root directory. 

Of course.  Any one would be able to "sudo mount /dev/sda /mnt" and poke around the file system on the other drives. 

I agree Linux can be broken, it can explode in humorous (read expensive) ways.  I've not played with it much but I'm reasonably certain that be expanding on the groups system you could make applications vanish for certain users (from both the menus and console).

---

