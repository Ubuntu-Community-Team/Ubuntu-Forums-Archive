---
title: "HP laptop Ubuntu install"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by Delinquentme on 2008-10-10
Soo im using this walk through:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

now Im on the last step sitting at the "Ready to install" screen and this is what I'm hesitant about:

On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)"

im looking at my install and theres NO migration assistant listed.

should i be worried ?

PS my HD setup is a single HD with 3 partitions
1 as the primary C drive 
1 HP recovery D drive
and the 20 gb of (currently) unformatted space im saving for my ubuntu install

---

### Post by Delinquentme on 2008-10-13
bump bump!

---

### Post by qwertymodo on 2008-10-13
I just recently did this same as you (HP laptop, vista, mine was x64, dunno if that makes a difference), and Vista DID NOT show up in the list of OSes to migrate settings from, that list was blank.  It still worked just fine.  Just when you're done, know that grub will take over your boot managing.  If you want to restore Vista's bootloader, check out this link:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4")

However, what I did was I ignored the whole thing about copying entries from menu.lst and using neogrub.  What I did was to use EasyBCD to reinstall the Vista bootloader and then just added Grub (NOT neogrub) via the Linux options.  That link is still useful for screenshots and for getting EasyBCD if you want to do it my way.  Here's my steps.

Install Linux
Reboot into Vista (last entry on the boot menu)
Install EasyBCD
Click on Manage Bootloader from the options on the left
Select Reinstall Vista Bootloader radio Button
Click Write MBR
Click on Add/Remove Entries from the options on the left
If Linux is there, remove it
Down where it says add an entry click the Linux tab
From the dropdown menu select Grub
Select your Linux boot partition and click Add
Reboot :)

If you want to do it that way just be sure DO NOT UNCHECK THE OPTION TO INSTALL GRUB TO THE BOOT SECTOR WHEN YOU INSTALL LINUX

If you don't install grub at install time you'll just have to do it the neogrub way

---

### Post by Delinquentme on 2008-10-15
is there any advantage to having vista as the boot loader??

---

### Post by qwertymodo on 2008-11-11
If you plan to use Ubuntu more, then no.  The point is to keep BOTH bootloaders.  I just don't know how to write Grub to the MBR without completely losing the Vista bootloader, whereas I DO know how to do it by keeping the Vista bootloader in the MBR.  By writing grub to the boot sector of your Ubuntu partition, both bootloaders stay intact, whereas if you forget and install grub to the windows partition, you lose the vista bootloader.  So be sure to install grub to the right partition, then it's a matter of writing grub to the MBR.  Google is your friend.

---

