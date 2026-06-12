---
title: "Ubuntu over Fedora with Windows Partition"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by WaitingforGuiteau on 2008-05-27
I recently tried to update from Fedora 6 to Fedora 9, and at some point in the process I did something very silly with the GRUB and now when I try to boot up the computer it goes through a short process of looking for CDs to boot from, then just starts printing 'GRUB' repeatedly.

Sick of this, I'm planning on installing Ubuntu instead since I've heard such glowing things about it, but I do have a few questions about this:

[LIST=1]
[*]If I do this over Fedora, what should I do to make sure I don't delete all of my data? Yes, I'm stupid and didn't make a back-up before updating.
[*]There is also a Windows XP partition that I need to keep just in case I come across something Windows-specific. Will the Ubuntu installer recognize this and leave it alone?
[*]There is a shared folder between the Windows and Fedora partition, which contains most of my useful information. Is there anything I should look out for when installing Ubuntu that might modify this particular folder?
[*]Will the Ubuntu installation remove all of the software I may have downloaded, such as Kile or FeynDraw?
[/LIST]

Thanks in advance for your help.

---

### Post by Rallg on 2008-05-27
Your best bet might be to fix the situation with Fedora 9, rather than try to fix it by installing Ubuntu. There are various ways to fix Grub. If you cannot suceed in fixing Grub, then you may be in for a world of hurt if you try to retain your old programs in a new system installation.

Although Grub works the same for Fedora and Ubuntu, you may need to fix your Grub menu.lst with some Fedora-specific code. So try the Fedora forum. Before asking there, prepare yourself. If necessary using a live CD with GParted, find out the complete list of your partitions. Which are primary, which are extended, which are logical, and which has the boot flag? What are their hd or sd device names?

Where is Grub installed? Is it in more than one place? (If so, that does not necessarily hurt.) From the live CD, you can go to Places > Computer > file system > dev, to locate your various volumes (patitions), then look within them for /boot/grub. Find each occurrence of menu.lst within the grub folder(s). Make a copy of the menu.lst contents, for future reference. Be sure that you are not simply reading the file system on your live CD.

Finally, in Terminal:

ls -l /dev/disk/by-uuid

which will reveal the mount pounts (as sd rather than hd) and their uuid codes.

Equipped with that information, you may be able to fix Grub. But again, the Fedora forum will know what codes to use.

---

