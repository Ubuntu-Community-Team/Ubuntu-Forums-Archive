---
title: "GRUB adding tons of boot options"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Xorlathor on 2010-03-29
This is no huge problem, but it is rather annoying to me. I am using the 10.4 beta, and whenever I get a large update (like a updated kernel) GRUB adds another boot option to the menu (I'm dual booting Vista and Ubuntu.) So my GRUB menu looks something like this when I turn my computer on:

[CENTER]GNU GRUB version 1.98-1ubuntu2[/CENTER]

Ubuntu, with Linux 2.6.32-18-generic
Ubuntu, with Linux 2.6.32-18-generic (recovery mode)
Ubuntu, with Linux 2.6.32-17-generic
Ubuntu, with Linux 2.6.32-17-generic (recovery mode)
Ubuntu, with Linux 2.6.32-16-generic
Ubuntu, with Linux 2.6.32-16-generic (recovery mode)
Ubuntu, with Linux 2.6.32-14-generic
Ubuntu, with Linux 2.6.32-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows vista (loader on/dev/sda1)

[CENTER]--------------------------------------------------------[/CENTER]

I really only need the top two and bottom three options - how can I remove the rest without risking messing up GRUB?

---

### Post by coffeecat on 2010-03-29
> **Xorlathor said:**
> I really only need the top two and bottom three options - how can I remove the rest without risking messing up GRUB?

Agreed. Keep the immediately previous kernel in case of trouble with the latest, but to uninstall all the old ones, open up Synaptic and do a search for all installed packages with '2.6.32-14' in the package name. There will probably be four packages. Mark them for uninstallation. Do the same with '2.6.32-16' and then 'Apply'. Your grub menu will be automatically updated for you.

---

### Post by Arand on 2010-03-29
Uninstall the relevant kernels:

Either use Computer Janitor from the System -> Administration Menu
and uninstall the relevant kernel version packages.
MAKE SURE TO NOT UNINSTALL PACKAGES THAT YOU WANT. Computer Janitor is a horrible tool which by default tends to suggest removing things that are wanted, make sure to only remove things you know you want removed.

You may have to run CJ twice, since it only seems to remove one of the two installed header packages on the first run.

OR

These commands:```
aptitude search 2.6.32-14
aptitude search 2.6.32-16
aptitude search 2.6.32-17
```Should give  a list of all packages associated with those old kernel versions. Just "sudo aptitude remove" the one's marked as "i" (installed) in those searches ("A" means automatically installed, irrelevant in this case).

Word of caution: You might want to keep at least one backup-kernel apart from the current one, unless you trust in it always being able to boot.

- Arand

---

### Post by 2hot6ft2 on 2010-03-29
> **Xorlathor said:**
> 
Ubuntu, with Linux 2.6.32-18-generic
Ubuntu, with Linux 2.6.32-18-generic (recovery mode)
Ubuntu, with Linux 2.6.32-17-generic
Ubuntu, with Linux 2.6.32-17-generic (recovery mode)
Ubuntu, with Linux 2.6.32-16-generic
Ubuntu, with Linux 2.6.32-16-generic (recovery mode)
Ubuntu, with Linux 2.6.32-14-generic
Ubuntu, with Linux 2.6.32-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows vista (loader on/dev/sda1)

I really only need the top two and bottom three options - how can I remove the rest without risking messing up GRUB?
It is recommended to keep the 2 most current kernels (those with the highest numbers) that way if something doesn't work right with the newest one you can still boot to the last known working one.

Below is what you would do if the 2 newest kernels were 2.6.32-18 and 2.6.32-17 which would be the ones at the top of the grub list.
Keeping in mind that there is a Recovery Mode for each kernel so those would be the top 4 listed.

To remove the others go to synaptic
System > Administration > Synaptic Package Manager
and search for
> 2.6.32-16
and
2.6.32-14

For each kernel there are 3 files that are needed. like below.
To remove kernel 2.6.32-16 right click on these and Mark for Complete Removal:
> linux-headers-2.6.32-16
linux-headers-2.6.32-16-generic
linux-image-2.6.32-16-generic
and for kernel 2.6.32-14 do the same with these:
> linux-headers-2.6.32-14
linux-headers-2.6.32-14-generic
linux-image-2.6.32-14-generic
**[COLOR="DarkRed"]Be careful when removing kernels not to remove all of them or removing any of the 3 needed files as shown above for any kernel you want to keep.[/COLOR]**
Otherwise you will most likely not be able to boot into Ubuntu.
Once you have the ones marked that you wish to remove click on Apply.

That will leave your grub looking like this:
> Ubuntu, with Linux 2.6.32-18-generic
Ubuntu, with Linux 2.6.32-18-generic (recovery mode)
Ubuntu, with Linux 2.6.32-17-generic
Ubuntu, with Linux 2.6.32-17-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows vista (loader on/dev/sda1)

If you want to remove the memtest entries (you can always boot a livecd if you want to test the RAM) you can do it by running this in a terminal
Applications > Accessories > Terminal
and run
```
sudo chmod -x /etc/grub.d/20_memtest86+
```
Which would leave your grub looking like this:
> Ubuntu, with Linux 2.6.32-18-generic
Ubuntu, with Linux 2.6.32-18-generic (recovery mode)
Ubuntu, with Linux 2.6.32-17-generic
Ubuntu, with Linux 2.6.32-17-generic (recovery mode)
Windows vista (loader on/dev/sda1)

---

### Post by Xorlathor on 2010-03-29
Much thanks to all - I simply cleaned up the ones I didn't want via Computer Janitor, and left the 2 newest kernels.

---

### Post by 2hot6ft2 on 2010-03-29
> **Xorlathor said:**
> Much thanks to all - I simply cleaned up the ones I didn't want via Computer Janitor, and left the 2 newest kernels.
Please mark your thread as solved using the Thread Tools at the top of the thread.

---

### Post by audiotopsy on 2010-07-01
Hello - Ive got exactly the same problem yet when I try Computer Janitor all I get in return is ¨could not find anything to clean up you can close the program now¨  any suggestions please........?

---

