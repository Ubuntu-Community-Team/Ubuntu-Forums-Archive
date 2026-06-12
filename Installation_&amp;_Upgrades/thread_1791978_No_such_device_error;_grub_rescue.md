---
title: "No such device error; grub rescue"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by Dave4237 on 2011-06-27
I tried to reinstall Ubuntu 11 on a large drive. I could not get the install completed because the prompts were not as straight forward as I had hoped. I ended up destroying the large drive so that it is not even recognized in a Win 7 computer.

Now when I try to boot the Win XP drive by itself (or with the other drive) I get this error:

No such device b2f0458-9253-4133-04b5-???????.
grub rescue

When I connect that drive to a Win 7 computer I cannot find any file with the word grub in its name. I am not able to search the text inside any files on Win 7.

How do I get my Win XP drive to boot without looking for an Ubuntu install that does not exist?

---

### Post by YesWeCan on 2011-06-27
You'll need to restore your XP MBR boot code. Best to use a Windows CD.

You can also do this using your Ubuntu live CD with these commands:
[COLOR=Navy]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]   (assuming your XP disk is sda - check using Disk Utility)


The Grub boot code and second stage code are embedded at the front of you disk. You cannot search these areas by normal means.

The Ubuntu installer is badly designed IMO. You have to be very careful to look out for where the Grub boot code is put. Grub breaks the MBR-system which Windows relies on. I always recommend disconnecting your Windows disks while you install Grub in order to make sure the Grub code ends up on your Ubuntu disk.

---

### Post by Dave4237 on 2011-06-29
The XP CD crashes with a PCI.SYS error, Address F74830BF base at F748000 with Datestamp 367d855c.

And I do not know how to get a prompt with Ubuntu 11.

---

