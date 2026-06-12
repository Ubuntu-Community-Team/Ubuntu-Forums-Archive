---
title: "--no floppy"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Anzan on 2009-06-23
My Karmic alpha 2 VM went through another partial dist upgrade today but Grub now fails and says

error: unknown argument '--no floppy'

I asked an associate and they said that,
"There was an old kernel bug that would basically cause funny behavior if the floppy disk module was loaded, so people, for years, would load their kernels with a 'no floppy' option.  This is probably no longer valid."

I can't figure out how to get to

/boot/grub/menu.lst

to change this option.

It's no big deal as it's just a VM but if anyone has any ideas I would appreciate it. 

Or I might just wait until the next alpha.

---

### Post by douham on 2009-06-23
Anzan, a search of the Karmic forum is helpful before creating a new thread please ;)
 anyway, this should provide all you need.[http://ubuntuforums.org/showthread.php?t=1194714]("http://ubuntuforums.org/showthread.php?t=1194714")

---

### Post by lonniehenry on 2009-06-23
A search of this forum would have come up with this link.[http://ubuntuforums.org/showthread.php?t=1194714](http://ubuntuforums.org/showthread.php?t=1194714) 
You will not find /boot/grub/menu.lst being used as karmic alpha new installs use grub2 by default now.  Several threads available about the changes.

Edit: I have to type faster- douham beat me to the draw

---

### Post by Anzan on 2009-06-24
Thanks, folks. I'll search next time.

---

