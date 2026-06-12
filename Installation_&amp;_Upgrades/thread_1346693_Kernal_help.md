---
title: "Kernal help"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by jats605 on 2009-12-05
Ok, so I just installed the newest updates (the one with the new kernals) and now I have to scroll down on grub to get to Vista. Is there a way to make only 1 kernal appear?

---

### Post by darkod on 2009-12-05
Not sure but you can do few things. Get rid of the memtest entries if you already haven't done that, and also put vista to be first on the list.

---

### Post by jats605 on 2009-12-05
How do I make vista First? *feels like /\/00b*

---

### Post by darkod on 2009-12-05
Here are the some basics about grub2. If you go into the /etc/grub.d folder you will see few files which names start with numbers. Grub2 menu is created from those files and in the order of the numbers.
10_linux takes care of ubuntu and maybe other linux OS, 20_memtest86+ makes the memtest entries, and 30_os-prober scans for any other OS (windows/linux) and that's why vista is at bottom.

Make a copy of 30_os-prober and rename the copy 06_os-prober. Because it will be copy of the original file it should be executable already but just in case in terminal run:
sudo chmod +x /etc/grub.d/06_os-prober

Then run:
sudo update-grub

That should create vista at top, your linux kernels and the vista at bottom too. Reboot and try it.
Once you are happy with your vista on top entry make the original 30_os-prober file unexecutable with:
sudo chmod -x /etc/grub.d/30_os-prober

If you want to get rid of the memtest entries make that file unexecutable too:
sudo chmod -x /etc/grub.d/20_memtest86+

After any change to grub2 config files you need to run:
sudo update-grub

If all of that works, you might want to change the default OS. The setting is in:
sudo gedit /etc/default/grub

Change the GRUB_DEFAULT=0 to the value you want. Note that the number should be one less than the entry in grub menu. If you want the 1st entry it's 0, the 2nd is value 1, etc. But do this at the end after your grub menu is formed to know how to count them. And you need to run update-grub after this too, of course.

---

### Post by jats605 on 2009-12-05
gah, untill I get a junky computer I can mess around with I might just uninstall. :( idk. 
In case i do decide to go Vista-only, I would just have to re-install the Vista bootloader right?

::EDIT:: On second thought, Wubi sounds like a good option...

---

