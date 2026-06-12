---
title: "need to access old partition"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Twig E. Pottox on 2007-10-26
How do I give programs access to files on a partition from a previous install?
Just installed Xubuntu 7.10 over ubuntu 6.06 to pick up speed on an old computer.  when installing I left my /home partition (34Gb) alone and re-formated my / and swap partitions. The installer apparantly made a new /home partion in the 5Gb / partition and now programs will not access the files in my old /home partition although there is a link to it on the desktop. Other than that the install went well and is performing well on the K62 500(Mhz) with 256 ram, 1x 40 Ghz HDD

---

### Post by taurus on 2007-10-26
When you got to the partition screen, did you remember to mount your old partition (/home) to /home?  If you didn't, then the installer had to create new /home so you can log in.

You can boot into recovery mode from GRUB menu and add an entry for your /home in there.  Assuming it's /dev/sda3, it would look something like

```
/dev/sda3   /home   ext3   defaults   0   1
```

---

### Post by Twig E. Pottox on 2007-10-26
Thanks for The Advice,  Sorry to Be an Idiot but how to I boot to the Grub Menu. This is a buntu only machine.

That must be where I screwed it up (not re assigning/home). One must never assume.

---

### Post by taurus on 2007-10-26
When you first turn on your machine, you would get a GRUB menu where you have options to boot from Ubuntu, a Recovery Mode, or memtest+.  If you don't see that window, press Esc down within 3 seconds and that menu should show up.  Use the down arrow key to highlight Recovery Mode and hit the Return key to boot from it.

---

### Post by Twig E. Pottox on 2007-10-26
Thanks again for your help.  I got to the recovery mode but where do I make the entry fstab?
. Sorry to be such an idiot but but I am really dangerous at the command line  as my usual reward for going there is a busted machine. please elaborate a bit on what to do here.. Thanks again

---

### Post by taurus on 2007-10-26
```
nano -Bw /etc/fstab
```
and add that line to the end of it.  Then, save it with <Ctrl>o and exit with <Ctrl>x.  Reboot and see if it uses your old /home now.

```
shutdown -r now
```

Again, you need to be sure which partition is your old /home, okay.  I used /dev/sda3 as an example so don't include it if it's not the right one.

---

### Post by Twig E. Pottox on 2007-10-26
Thanks Taurus, The old dog is purring like a kitten. One more dumb question. Was there a reason to go through the recovery mode instead of just opening a terminal?

---

