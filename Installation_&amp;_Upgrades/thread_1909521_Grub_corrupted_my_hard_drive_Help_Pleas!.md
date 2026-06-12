---
title: "Grub corrupted my hard drive Help Pleas!"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by Stealthp90 on 2012-01-15
Okay first of all i will start of saying that i tried installing 11.10 on to my AMD a6-3400m laptop. and i tried doing the fixes for this hardware. it asked me at one point to put grub on using the installation manager. So i did, and that made it so i could not start windows which i need for school, and also Linux dose not work either. When i try rein staling windows it cant even see my hard drive. How can i fix this.:confused:

---

### Post by carl4926 on 2012-01-15
Boot the Ubuntu cd to a Live desktop
Open a terminal and post the result of

```
sudo fdisk -l
```

---

### Post by Stealthp90 on 2012-01-15
I cant do that Ubuntu dosent work normally on the AMD a6-3400m

---

### Post by carl4926 on 2012-01-15
> **Stealthp90 said:**
> I cant do that Ubuntu dosent work normally on the AMD a6-3400m

So you were installing it....why?

---

### Post by darkod on 2012-01-15
Did you try before installing to run in live mode? Did you need to add some boot parameter for it to work?

If yes, just add the same parameter now and boot into live mode.

If not, try this:
Boot with the cd but immediately when the first purple screen shows, press Esc. That should show you the older type of text menu with first option Try Ubuntu.
At the bottom there should be information how to select various options, I think if you hit 'e' is for edit. The boot lines should show.
With the arrows keys position the cursor on the line starting with linux, towards the end before it says 'quiet splash'. In front of it add radeon.modeset=0.
Press Ctrl + X to boot and see if that boots into live mode.

---

### Post by Stealthp90 on 2012-01-15
There are supposed work arounds.

---

### Post by punkybouy on 2012-01-16
You installed the GRUB boot loader without configuring it to work with your other OS (Windows) and by installing it you wiped out the Windows boot loader. A drive can only have ONE boot loader. You can now boot from the Windows install CD and go into repair mode and re-install the Windows boot loader OR you can modify the GRUB loader you already installed. Windows is probably still there, you just have a boot loader that will offer it as a boot choice.  Here is a link that might help.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2012-01-16
Windows sometimes can NOT see the hard drive if it contains only Linux filesystem partitions.

I would first boot into the BIOS and confirm that you can see the drive OK.

Then, if you have an Ubuntu destktop CD, I would boot into that, select Try Ubuntu, and see if the Windows OS partitions and files are still there.

It's all too easy, using the new-improved installer, to accidentally erase your entire Windows install, when doing manual formatting (the "Something Else" option).

Let's at least confirm that did NOT happen to you.

---

