---
title: "Error loading up windows from GRUB"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by blackearth99 on 2010-02-05
I installed ubuntu on my external hard drive last night and all went well until I got to the GRUB OS loading screen. I pressed enter on the windows xp professional selection and all I get is an "error: invalid signature, press any key to continue" 

Now my theory is that since I have a raid 0 set up on my laptops hard drives that the GRUB loader is not accessing the correct hard drive to boot windows.

Here is what the selection says about windows-  "microsoft windows xp professional (on /dev/mapper/nvidia_cabcadae1)"

Does anyone know how to change the path to which the hard drive access "nvidia_cabcadae0"? Or if I'm completely wrong i'd like some help/insight on what the problem is.

---

