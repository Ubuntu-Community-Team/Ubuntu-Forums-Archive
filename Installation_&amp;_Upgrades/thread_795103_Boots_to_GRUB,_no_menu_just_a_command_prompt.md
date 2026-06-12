---
title: "Boots to GRUB, no menu just a command prompt"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by psyvision on 2008-05-15
Hello,

I have just install Ubuntu AMD64 onto my computer from the install option on the live CD but it will not boot from GRUB.  

I installed Ubuntu into the free space available after resizing an NTFS partition on one of my data drives (i.e. Windows isnt installed to it). The install went fine and GRUB was installed onto  hd0 - I didn't want to change this so left as default, if I boot to Windows by typing commands at the GRUB prompt I use hd0 so presume this is the correct boot drive.

Now, when booting my computer it reaches GRUB but goes to the command prompt as opposed to the usual auto booting or pressing Esc to choose an option from the menu.

I have gone back onto the live CD and checked the menu.lst and it all seems fine.  I am also able to boot to Windows and Ubuntu by entering the commands into the GRUB prompt manually, so that seems to be functioning fine.

Any ideas on why I don't get a menu?

---

### Post by dstew on 2008-05-15
Are you sure that grub stage2 and menu.lst are both in the same /boot/grub directory?

---

### Post by psyvision on 2008-05-15
Sorry it took me a while to check, stage 1, stage2 and menu.lst exist within /boot/grub/

---

### Post by dstew on 2008-05-15
At the grub command line, enter **configfile menu.lst** and see what happens.

---

### Post by psyvision on 2008-05-16
When entering that line I get the message:

Error 1: Filename must be either an absolute pathname or blocklist.

So I repeated with:

configfile /boot/grub/menu.lst

and the menu appeared.  However, when I selected an option I got the error message:

Error 18: Selected cylinder exceeds max supported by BIOS.


Now the machine isn't that old, the BIOS isn't the newest revision, and yet it's not that old.  Should I update the BIOS to the latest version? and secondly, when viewing the partitions from Windows using Norton Partition Manager and using "sudo fdisk -l" I get a message saying that the partitions do not end on cylinder boundaries...

---

### Post by dstew on 2008-05-16
If you get Error 18 on a newer machine, there a lot of reasons why. Certainly upgrade your BIOS if you can. Sometimes, it is because a drive was installed that exceeds the LBA addressing limit of 137 Gb on some middle-aged BIOSes. A good resource is [Herman's grub error page]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors").

---

### Post by psyvision on 2008-05-16
I'll try the BIOS update and let you know what happens.  Windows is on a 250GB drive and Linux at the end of a 500GB drive...

---

### Post by psyvision on 2008-05-16
Okay, thank you for that! The BIOS update has fixed error 18 that GRUB was reporting.

However, I still don't get the menu, I get a command prompt and have to type configfile /boot/grub/menu.lst before I see anything...

Would seeing how my disk is laid out help?

---

### Post by dstew on 2008-05-16
Yes, go ahead and do ```
sudo fdisk -l
```It is an interesting puzzle why the menu does not appear. The reason it is interesting is because clearly grub is accessing stage2, because you get the command line. But, menu.lst is in the same directory, so it should show the menu.

A couple of possibilities come to mind. Perhaps you have two grub directories, and the one that gets accessed at boot time has a stage2 but no menu.lst, or an empty menu.lst, but the /boot/grub directory that you access using the configfile command has the correct menu.lst. We might look for that.

Also, the menu itself might have been hidden, and it is possible that the default item is to drop to a command line. If that is the case, when you boot grub and get the command line, hit <ESC> and the menu should appear. If the menu doesn't appear, then the first possibility (multiple grub directories) is more likely.

---

### Post by psyvision on 2008-05-16
Okay, let me just say that the machine has had Fedora on it before, I deleted the partitions relating to it and resized the Windows partition to use the free space generated.

Ubuntu is installed on a completely different drive...

---

### Post by dstew on 2008-05-17
That is an important clue. Perhaps a piece of the Fedora system was left behind that is causing the problem. I think the simplest thing to do is to re-install grub to make sure that the boot loader (on track 0 of the boot disk) is hooked up to the partition with the correct /boot/grub/menu.lst file. I do not know a great deal about Fedora, but if you used grub to boot it, and if you did not re-install grub, then deleting the Fedora partition would *_not_* have deleted the old boot loader, because it resides on track 0, which is not part of any partition.

Re-installing grub is simple. Here is how to do it. Boot as usual to the grub command line. On the command line, enter```
find /boot/grub/menu.lst
```That should return a partition name in grub-speak, like (hd1,0). *If it returns two names, post back for instructions on how to figure out which is the correct one.*

If you got only one name, use that name as the argument for the root statement. For example, if the **find** statement returned (hd1,0), then the root statement would be:```
root (hd1,0)
```Then, re-install the boot loader on your boot hard drive:```
setup (hd0)
```Reboot the computer, and see if you get the menu now. You can actually reboot the computer from the grub command line with the **reboot** command.

---

### Post by psyvision on 2008-05-17
Thank you!

Fixed the problem,  I had tried a similar re-install of grub to solve the no menu problem but I think I must have got the wrong drive letter.

Now to install Fedora and break it some more :p

---

