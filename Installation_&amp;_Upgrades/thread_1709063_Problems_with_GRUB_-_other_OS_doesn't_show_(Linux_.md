---
title: "Problems with GRUB - other OS doesn't show (Linux newbie)"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by Laplacian3d on 2011-03-17
Hello,
I am having some problems with my grub.  My goal is to have a dual boot Lubuntu 10.10 and (streamlined, as much as possible) XP Pro on an older machine.  I have a tiny bit of experience with Ubuntu as a single install, but that's all.

Here is what I've done so far (in order):
1. partition sda (80 MB) into 3 partitions using Lubuntu boot disk: Linux swap (2 GB), ext 4 (38 GB), unpartitioned space (40 GB)
2. installed XP on the unpartitioned space (works fine)
3. installed Lubuntu on the Linux partition with (works fine)
[COLOR=Blue]At this point, grub has installed properly and I am able to select from the OSes (Lubuntu or XP) from the grub menu.[/COLOR]
4. Boot into Lubuntu and apply all recommended updates.  Updates successful.  Reboot.  (But "Reboot Now" option on update GUI doesn't work so I have to Reboot by clicking on shutdown/reboot.)

[COLOR=Red]When it reboots, the grub menu shows two Ubuntu (Lubuntu) OSes and no XP![/COLOR]  Selecting the first Ubuntu (Lubuntu) from grub menu brings me into a fully functioning OS, but choosing the second causes the machine to hang.

What is going on?  Why is XP removed from grub?  Why does grub show two Ubuntu OSes?  Can someone please help a Linux newbie?
Thanks.

---

### Post by ajgreeny on 2011-03-17
Install os-prober in your lubuntu install ```
sudo apt-get install os-prober
```then run ```
sudo update-grub
```
This is a documented problem in lubuntu that for some unknown reason does not install os-prober by default.

---

### Post by Laplacian3d on 2011-03-18
Okay, thanks for the tip.  That helped...except for one thing.  I have my XP choice back in the grub menu, but I still have two sets of choices for Ubuntu (Lubuntu).  Here is what my grub menu looks like:

```
Ubuntu with Linux, 2.6.35-27-generic
Ubuntu with Linux, 2.6.35-27-generic (recovery mode)
Ubuntu with Linux, 2.6.35-22-generic
Ubuntu with Linux, 2.6.35-22-generic (recovery mode)
Memtest
Memtest for serial
Windows XP
```

The second Ubuntu (2.6.35-22) hangs and doesn't come up.  How did this get here?  How can I get rid of it?  Will I have more issues with this combination of grub and Lubuntu?

Thanks for the help.

---

### Post by Quackers on 2011-03-18
That's normal. You now have 2 entries because you have 2 linux kernels. Some people recommend that you keep the second one as a spare, in case the first one stops booting. This is sensible.
You may not want to do that. If so, you can remove the old kernel via synaptic package manager. Note that there will be 3 entries for the kernel in synaptic to be removed. Also be careful to remove only the old one! Use the search box in synaptic - enter some of the kernel number, eg 2.6.35, and the installed kernels will appear in the main window.
Once it's removed you can then run sudo update-grub in a terminal to update your grub menu.

---

### Post by Laplacian3d on 2011-03-18
Great, thanks that worked.  I noticed that in synaptic there are a few different kernels.  Could I pick from any of those and install them as a backup?  The backup that was installed wasn't the latest (maybe for some reason...).

---

