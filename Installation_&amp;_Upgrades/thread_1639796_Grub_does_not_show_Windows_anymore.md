---
title: "Grub does not show Windows anymore"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by Sanix on 2010-12-07
After installing the latest updates, grub removed my windows from the boot list. As the new grub version looks really complicated, I can't create the entry manually (only grub.cfg which is very crpytic compared to former menu.lst).
Could anyone give me an example, how the entry for a windows 7 should look like?

I tried the automatic way, which simply won't find my Windows:

grub-mkconfig

---

### Post by Shintek on 2010-12-07
Are you sure you didnt accidently delete/overwrite your windows partition?

---

### Post by coffeecat on 2010-12-07
Normally, you would  run 'sudo update-grub', but it seems that you may have effectively done that, because...

> **Sanix said:**
> grub-mkconfig

is what update-grub runs. However, did you run it with 'sudo' and/or any arguments? Because it needs to be...

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

If there is any doubt, try running:

```
sudo update-grub
```

If that doesn't work, open Synaptic package manager and see if the package os-prober is installed. I've seen a thread where the absence of os-prober was the cause of Windows failing to appear in the grub menu. Which is very odd because os-prober is part of a default install. Nevertheless, it's worth checking.

Lastly, if all else fails, run the boot info script here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post the RESULTS.txt file. We need that for the partition information needed for a grub2 Windows stanza. Please make sure you post the output in code tags (use the # icon in the toolbar above the message field), otherwise it will be unreadable.

---

