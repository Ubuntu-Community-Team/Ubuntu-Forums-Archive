---
title: "proliferation of boot options"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by cannonballsimp on 2011-03-07
Hi
I'm running Lucid Lynx in a dual boot setup with XP Pro. Sometimes when Ubuntu updates, it adds a new boot option to the list where I choose which operating system to load. currently, I have six different versions of Ubuntu listed here, each with an associated recovery mode, in addition to memtest and XP.

Is there a way to remove some of them? They are really annoying!

thanks
Simon

---

### Post by cjhabs on 2011-03-07
> **cannonballsimp said:**
> Hi
I'm running Lucid Lynx in a dual boot setup with XP Pro. Sometimes when Ubuntu updates, it adds a new boot option to the list where I choose which operating system to load. currently, I have six different versions of Ubuntu listed here, each with an associated recovery mode, in addition to memtest and XP.

Is there a way to remove some of them? They are really annoying!

thanks
Simon

I have a slightly different setup that you - multi-boot but no windows.
I removed the extra kernels from /boot and then ran "update-grub".

Please make sure you are comfortable with what you are doing as you could end up screwing up the system boot if you delete the wrong files.

Thinking about it, you could just edit the menus and leave the extra kernels in place - /boot/grub/grub.cfg is the file - but if you run "update-grub" later on, those menu options will come back.

---

### Post by oldos2er on 2011-03-07
Use a package manager to remove them; Software Center, Synaptic, apt-get, whatever your preference is. I like to keep at least two kernels installed, "just in case."

Example: In Synaptic Package Manager, click Status, Installed, look for linux-image*, right-click to 'Mark for Removal', Apply.

If you have Ubuntu Tweak installed, it also has an option to remove unwanted kernels.

---

### Post by cannonballsimp on 2011-03-07
Thanks. Oldos2er, I'll try your suggestion. cjhabs, yours looks a bit beyond my Ubuntu comfort zone! Thanks anyway.

---

### Post by cannonballsimp on 2011-03-07
It worked. Thanks. Freed up 400MB. 
I noticed another set of similar filenames in Synaptic Package Manager, called linux-header xxxxxx. Any idea if I can get rid of those too? They're not bothering me, but if this was Windows, files like that would probably be taking up a fair amount of space.

---

### Post by oldos2er on 2011-03-07
Yes you can remove the linux-header packages matching the version number of the linux-image* you removed.

---

### Post by cjhabs on 2011-03-07
> **oldos2er said:**
> Use a package manager to remove them; Software Center, Synaptic, apt-get, whatever your preference is. I like to keep at least two kernels installed, "just in case."

Example: In Synaptic Package Manager, click Status, Installed, look for linux-image*, right-click to 'Mark for Removal', Apply.

If you have Ubuntu Tweak installed, it also has an option to remove unwanted kernels.

That is safer than my method - also I noticed that those packages still show in Synaptic after I manually removed the files - you learn something new every day! Thanks

---

