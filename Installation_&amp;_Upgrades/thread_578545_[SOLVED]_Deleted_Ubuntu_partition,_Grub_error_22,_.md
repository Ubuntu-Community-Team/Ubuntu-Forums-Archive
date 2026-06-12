---
title: "[SOLVED] Deleted Ubuntu partition, Grub error 22, get back to XP?"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2007-10-17
Let me say first: I'M NOT ABANDONING UBUNTU :lolflag:

I'm giving an old laptop to my fiance, who lives 800 miles away.  If she lived closer, I'd keep Ubuntu installed, but I don't want to try to support it long-distance.

Here's the situation: I dual-botted XP Home and Ubuntu Dapper-Feisty on this laptop, and here's what I did.  I used the live cd and gparted to delete the Ubuntu partition and then resized the XP partition to take the entire space.  Oops. I didn't realize I wouldnt overwrite grub.

Here's what I want to do: Get rid of grub altogether so that the computer boots straight into Windows.

Anyone know how?  I am currently left with an unbootable machine.  I have both the xp home disc and the Feisty Live cd.  If worse comes to worst, I can always reformat the disc using the XP disc, but that will take hours, and I don't really want to resort to that.  The XP partition has programs installed and is relatively up to date. I just don't want to start over.

Thanks!

---

### Post by Druke on 2007-10-17
hmm does windows xp have a rescue function? that may be able to restore the windows boot loader

What i would do in that situation is keep grub, make a 20MB partition for it on the HD and set it's timer to 1 second.

---

### Post by mjitkop on 2007-10-17
I think you have to use the XP disc to repair Windows. I've never done it but I think I read this in other threads. You may want to do a search in the forums to confirm what I'm saying. I'm sure somebody more experienced than I am will correct me if I'm wrong and/or give you a more detailed answer. :)

---

### Post by bg1256 on 2007-10-17
> **Druke said:**
> hmm does windows xp have a rescue function? that may be able to restore the windows boot loader

What i would do in that situation is keep grub, make a 20MB partition for it on the HD and set it's timer to 1 second.

If it has a rescue function, I can't see it.  It may have that option on the windows disc.  I will check that when I get back to that machine.

How could I edit Grub without having Linux installed?

---

### Post by Druke on 2007-10-17
thats the problem, it seems really out of the way (so theres prolly a much better way) but there should be a way to mount only the part that grub uses ( /boot ? )in that 20mb parition then just whipe the rest of ubuntu. You could also try the Rescue CD thats on the first disc of SUSE linux.

---

### Post by VCSkier on 2007-10-17
You're on the right track.  It can be done with the XP install disk, or with a couple other methods.  Here's a great help page with several of the possibilities listed.
[Restore the  Windows 'boot sector]("http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector")

---

### Post by bigken on 2007-10-17
boot from the windows xp cd at the prompt select R for repair console select the windows partition usually 1 then at the prompt type** fixmbr** enter** fixboot **enter **exit ** enter you should now be rebooting into windows :)

---

### Post by bg1256 on 2007-10-17
Thanks everyone!  I got it fixed!

I used the Super Grub Disc to get it working again. And thanks to this thread, I know of even more ways.

solved!

---

