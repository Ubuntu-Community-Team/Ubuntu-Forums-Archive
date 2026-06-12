---
title: "Editing grub menu"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Haywood on 2007-02-28
Hi,

I just installed Ubuntu 6.10 to dual boot on my Windows XP laptop.  Everything in the installation went fine and I can access both OS, no problems.  After I installed Ubuntu 6.10, it said there were updates available.  No problem.  I did the updates and rebooted.  My question is this: the grub loader list is now getting longer.  Is there anyway to edit the menu of options there?  Thanks in advance.

Bill

---

### Post by rsambuca on 2007-02-28
There are a few ways to go about it.  One method is to simply remove the entries from your menu.lst file (which is what grub uses for boot instructions).  You can either 1. delete them, or 2. comment the entries out by putting a "#" in front of the lines you want to remove, or 3. you can change the line that says "howmany=all" to howmany=1, or if you are sure the upgrade is stable, you can remove the old kernels using the Synaptic Package manager.  If you search for linux image, you will see the versions you have installed, and you can remove the old ones.

If you are going to edit your menu.lst, you can use the gedit text editor by typing this command:```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Haywood on 2007-02-28
Worked like a champ.  Thanks:guitar:

---

### Post by rsambuca on 2007-02-28
Good stuff!  What method did you use, by the way?

---

### Post by Haywood on 2007-02-28
I removed the old kernels using the Synaptic Package manager.  Once again thank you for your assistance.

---

### Post by bkthiess on 2007-03-01
Ever since updating to Kubuntu, nothing will let me open the menu.lst.  It says command cannot be found.  I went through the back door and opened the menu.lst in the text editor, but it would not let me save changes.

It's not a big deal, but my wife wants it to boot into Windows by default, and ever since going to Kubuntu, it won't let me change.

---

### Post by rsambuca on 2007-03-01
The menu.lst file is there.  Are you sure you are spelling it correctly?  If you are using kubuntu, try copying and pasting this command in a terminal```
kdesu kate /boot/grub/menu.lst
```

---

### Post by bkthiess on 2007-03-01
Thanks for the guidance, I tried it once and it worked.  I changed the default from 0 to 5.  But it should have been 6. I ran the command again, and only got this:

bthiess@FX390:~$ kdesu kate /boot/grub/menu.lst
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

And nothing else. Kate wouldn't open.  Any other hints?

---

### Post by rsambuca on 2007-03-01
try gedit in place of kate.

You can also use nano and edit the file in the terminal as well.

---

### Post by bkthiess on 2007-03-02
Thanks for all the help rsambuca.  It worked again after a reboot.  ??

Now I've got grub working just the way I want it.  Thanks again!

---

