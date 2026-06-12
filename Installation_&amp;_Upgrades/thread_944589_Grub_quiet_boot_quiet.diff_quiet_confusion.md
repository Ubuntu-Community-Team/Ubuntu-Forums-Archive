---
title: "Grub quiet_boot quiet.diff quiet confusion"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by cshooshan on 2008-10-11
Good day!

I have two identical HP 6910p laptops with dual boot Edubuntu 8.04 and Windows XP. They should function in identical ways.

However, I am stumped as to why the Grub menu functioned differently on the laptops.

On one, the responses to the individual menu items are echoed to the console; one the other, there are no messages. This is true whether or not I select a menu item from the menu or hit "c" and enter the commands manually.

An example:

After entering:

root         (hd0,4)

one laptop responds with:

FileSystem type is ext2fs, partition type 0x83

the other responds with nothing (or maybe a blank line).


If I run grub from within a terminal session while booted into the Edubuntu GUI, both laptops behave "quietly" (that is, I do not get the echoed responses in the terminal).

I tried reinstalling grub to the mbr with setup (hd0). The command was successful but there was no change in this behavior.

The menu.lst and grub.conf files on both machines seem identical.

I am stumped!

Is there something that patches grub during an ordinary Edubuntu/Ubuntu install that may have been overwritten or missed on one machine than the other?

Do I need to copy something else to the mbr? Do I have to find and figure out how to apply the quiet.diff patch that may exist somewhere?

Should I figure out a way to get a development version of grub for upgrade (current version: 0.97-29ubuntu21)?

In case you are interested, why do I care?

1. I really want to understand how grub loads on boot and where it gets its configuration and settings.

2. I really want to suppress the "FileSystem Type unknown" message after choosing "Windows XP" (because it is ntfs) so as not to confuse the other users of the laptop (similar configurations are being setup for students in our schools).

Thanks for any help!

-- Charlie

---

### Post by caljohnsmith on 2008-10-11
That's really strange. I suppose I might start with uninstalling Grub from the machine that does the echoing, reinstall the Grub package, and reinstall all the Grub files back into /boot/grub with "grub-install" to see if it changes the behavior. If you want to give it a shot, then boot into Edubuntu on the "echoing" computer, and do:
```
sudo apt-get purge grub
cd /boot/grub
sudo mv menu.lst ..
sudo rm *
sudo apt-get install grub
sudo grub-install /dev/[COLOR="Blue"]sda[/COLOR]
sudo mv ../menu.lst .
```
Make sure to change sda if your drive is different. Also, please be extremely careful about the rm command above; make sure you are in the /boot/grub directory and nowhere else when you run that command, and also make sure you successfully moved your menu.lst to the /boot directory above it with the mv command before the rm command. 

See if that makes any difference in Grub's behavior. Let me know how it goes. :)

---

### Post by cshooshan on 2008-10-12
caljohnsmith:

Problem solved! That did the trick.

I did verify that the /usr/sbin/grub version before and after were the same. Everything else looks the same, too.

I'm guessing that the voodoo of "sudo grub-install /dev/sda" from a clean install far exceeds the "setup (hd0)" I tried from the existing install.

Thanks again for the succinct yet safe and thorough response!

-- Charlie

---

### Post by caljohnsmith on 2008-10-12
> **cshooshan said:**
> caljohnsmith:

Problem solved! That did the trick.

I did verify that the /usr/sbin/grub version before and after were the same. Everything else looks the same, too.

I'm guessing that the voodoo of "sudo grub-install /dev/sda" from a clean install far exceeds the "setup (hd0)" I tried from the existing install.

Thanks again for the succinct yet safe and thorough response!

-- Charlie
That's great that reinstalling Grub is all it took. In case you are interested, the primary difference between "setup (hd0)" and "grub-install" is that grub-install will create all the necessary Grub files in the /grub directory if they don't exist; but both grub-install and "setup (hd0)" will install Grub to the MBR (Master Boot Record) in the way you used it. And actually, the grub-install command is basically a script that uses the Grub "setup" command, because the man page says:
> grub-install copies GRUB images into the DIR/boot directory specfied by --root-directory, and uses the grub shell to install grub into the boot sector.
Anyway, cheers and have fun. :)

---

### Post by cshooshan on 2008-10-12
I hadn't mentioned that I first tried to use the Synaptic Package Manager to reinstall grub with "Mark for Reinstallation." Based upon your suggestions, I now know that "Mark for Complete Removal" is equivalent to "purge" and I should have done that first.

But, I do like the control of doing everything from the terminal.

Thanks again.

---

