---
title: "My tar cloned partition won't boot..."
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by .neo on 2008-02-12
I've done a tar copy of Gutsy installed on a bigger hard disk with a 4gb partition to a smaller harddisk with a 2gb partition (that Gusty was installed with minimal Gnome so there was only about 1GB used space on the 4GB drive). After that I manually reinstalled grub using 'recover broken system' from Gutsy Live CD.
  Unfortunatelly, the system now freezes upon boot?! It does startup boot, which is visible if I choose recovery mode startup from grub... I've also tried randomly picking and accessing (listing their content with cat) some of the files on the cloned harddisk and it all seems to have been all copied ok??? Apart from UUID values which I don't get exactly menu.lst seems to be ok too?
  Is there a chance tar copy made a mess of some ownership rights or something? I used ```
tar -cf - . | ( cd /clone_path && tar xf - )
``` as root on the root of the cloned disk...
  Or is there someting else you suggest I should change in menu.lst files (like getting rid of UUID values), plz?
  TIA good ppl :)

---

### Post by mrsteveman1 on 2008-02-12
where does the system fail?

Do you know if the kernel actually loads?

Does the kernel get a chance to mount the root partition?

---

### Post by .neo on 2008-02-13
**A new development!** :)

I've booted in recovery mode and as before the booting freezes on a screen showing lines about my drives, saying stuff about sda, sda1, sda2, usb 3-2 (configuration #1 chosen from 1 choice) etc... I'm so sorry but I have no idea if kernel has loaded or not before freezing, because I'm not that familiar with the linux (ubuntu) booting sequence, my guess it isn't...

What I've noticed just now is that after couple of minutes of not responding (or as I so technically called it *boot being frozen* :) ) the recovery mode shows a following message (which I'll type over, so I apologize in advance in case I mistyped something - if anyone knows where is the boot log file please write here and I'll post it if you'd like):

```

usb 3-2: configuration #1 chosen from 1 choice <-- this is the line where boot freezes!!!
Done. <-- this and all after this line appears after a few minutes of waiting
      Check root= bootarg cat /proc/cmdline
      or missing modules, device: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/f81c74c0-c830-4733-9fc3-28fa6e322714 does not exist. Dropping to a shell!

BusyBox c1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

My guess is since I've basically just tar copied one drive to another that the reference to the old drive which stayed in menu.lst of grub is being searched for but not being found by that old UUID value (which I'm again so sorry but I don't know what it is)... I'll try and find more about grub and changing those UUID reference values (I think there's a way not to use UUID, but hda reference, which I'll investigate). If someone knows this however, and would write instructions I'll be much obliged :lolflag:

TIA again

---

### Post by mrsteveman1 on 2008-02-13
When Ubuntu was installed it set the boot files to point to your linux partition, identified by its UUID, which is unique to that partition. This is why the system was looking for /dev/disk/by-uuid/f81c74c0-c830-4733-9fc3-28fa6e322714

When you copied the files for your system to another partition, the boot files no longer pointed to the correct partition. The solution is to find out what the correct disk ID is for the new partition, you can do this by booting an ubuntu livecd and listing the contents of /dev/disk/by-uuid/ like this:

```
sudo ls -l /dev/disk/by-uuid/
```

Depending on how many partitions you have on the drive, it may be the only one present. This UUID will need to be put into the /boot/grub/menu.lst file, replacing the one that is present right now.

Alternatively you can in fact change the menu.lst file to use /dev/hda1 or /dev/sda1 etc, just make sure you get the right one.

---

### Post by .neo on 2008-02-14
Thanks for the info. I figured that UUID was the troublemaker too, but couldn't figure out how to generate new UUIDs... I did 'sudo update-grub' but that changed menu.lst to /dev/hda1 (which in fact didn't exist), so after not being able to start nano from shell terminal that I was trying to get started from 'rescue a broken system' (which I'd like to know how this can be done?), I finally gave up and booted ubuntu  desktop live cd where I changed the hda to sda... Now it boots :)

---

