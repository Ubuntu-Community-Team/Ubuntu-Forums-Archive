---
title: "Making Ubuntu the boot option instead of the default"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by pudgy parrot on 2008-08-10
I've actually got 2 questions here:

1.  I want to move my partitions.  I dont save any data in Ubuntu, so I only need a small section of my drive.  Whats the best way to do that?

2.  When my computer boots, I get about 5 or 6 options to choose from.  I'd like to see if I can get rid of the safe modes and other modes of Ubuntu from that list.  Also, I'd like windows to be the default that boots up when the computer is turned on.  My wife is getting tired to babysitting the boot process to get into windows.  She doesn't like linux. 

Thanks every one.

---

### Post by Pumalite on 2008-08-10
You can save data in ntfs with ntfs-3g (by default). Don't get rid of Recovery Mode; you might need it sooner than you think.

---

### Post by pudgy parrot on 2008-08-10
> **Pumalite said:**
> You can save data in ntfs with ntfs-3g (by default). Don't get rid of Recovery Mode; you might need it sooner than you think.

I'm sorry I'm pretty new and I dont know what that first sentence means.

---

### Post by Pumalite on 2008-08-10
Ubuntu by default can read and write to an ntfs partition (which is Windows)

---

### Post by Kralizec on 2008-08-10
The application StartUp-Manager (check the repositories for it) allows you to graphically determine the default operating system. You can also set the number of linux kernels to display in the boot menu using that app. Additionally, you could simply uninstall the kernel versions you don't want. A third, more advanced solution, would be to edit (as root) the **/boot/grub/menu.lst** and delete the options you don't want.

---

### Post by Pumalite on 2008-08-10
Leave at least one additional kernel to boot from. You never know when you are going to need it.

---

