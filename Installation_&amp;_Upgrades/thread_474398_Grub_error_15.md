---
title: "Grub error 15"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by livestockPimp on 2007-06-15
Hi,
I recently did a installation and after the install on boot it tells me "grub error 15"
i have tried re-installing the MBR but this wont help either.

Thanks

---

### Post by coffeecat on 2007-06-15
From the Grub manual:

> 15 : File not found

This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.At a guess it sounds as if grub can't find menu.lst, or if menu.lst is there it can't find the kernel or initrd.

Was this a first-time bootup? Can you give some more details?

---

### Post by Tr0janV0dka on 2007-06-15
Tried using the Windows Recovery Console?

Slap your Windows XP disc in, make sure your BIOS boots off CD, wait until all the loading finishes and you should be given the option to press **r** to enter the Window Recovery Console and from there it's one simple command and your back to Windows.

/fixmbr

I learnt this the hard way when I first messed with Ubuntu. :guitar:

---

### Post by coffeecat on 2007-06-15
> **Tr0janV0dka said:**
> Slap your Windows XP disc in, make sure your BIOS boots off CD, wait until all the loading finishes and you should be given the option to press **r** to enter the Window Recovery Console and from there it's one simple command and your back to Windows.

/fixmbr

Was the OP wanting to repair the Windows bootloader? That wasn't the way I read it. I read it as a grub error after an Ubuntu install and wanting help to get into Ubuntu. This is the - cough - Installation and Upgrades subforum after all.

But now you've read it that way, I can see the post is ambiguous. Perhaps the OP will clarify.

---

### Post by livestockPimp on 2007-06-17
this is not windows related, the machine is a server with only linux installed on it,
There is defiantly a menu.lst and it appears correct, there is no splash screen or anything specified in the settings and since it drops out within a second of grub starting to load it cant be a kernel error i haven't selected the kernel to load.

Thanks for the replies so far.

---

### Post by Pumalite on 2007-06-17
> **livestockPimp said:**
> this is not windows related, the machine is a server with only linux installed on it,
There is defiantly a menu.lst and it appears correct, there is no splash screen or anything specified in the settings and since it drops out within a second of grub starting to load it cant be a kernel error i haven't selected the kernel to load.

Thanks for the replies so far.

Try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by livestockPimp on 2007-06-17
Thanks, i will give it a try tonight and let you know how it goes.

---

### Post by coffeecat on 2007-06-17
> **livestockPimp said:**
> There is defiantly a menu.lst and it appears correct


When I said that it's possible that Grub can't find the kernel or initrd I wasn't expressing myself clearly. Sorry for that. I've had this when I've made one tiny error in either the kernel or initrd line. Well - tiny to me that is, but obviously huge in computer terms. :)

I've sat in front of the screen for ages staring at menu.lst looking for the error, cussing the machine all the while, until the penny has dropped and I've seen what I'd done wrong. I know you've said that menu.lst appears correct, but suggest you triple-check that before reinstalling grub.

---

### Post by livestockPimp on 2007-06-19
the menu.lst is fine, it has dropped out on 2x debian installs, one from a netinst of testing and another from etch. and it is dropping out before the menu.lst even starts reading from what i can see otherwise i should at least get access to the menu.

---

### Post by Pumalite on 2007-06-19
> **livestockPimp said:**
> the menu.lst is fine, it has dropped out on 2x debian installs, one from a netinst of testing and another from etch. and it is dropping out before the menu.lst even starts reading from what i can see otherwise i should at least get access to the menu.

What did 'find' show?

---

### Post by livestockPimp on 2007-06-19
Thanks everyone, i found the problem
My motherboard was been stupid and since the booting hdd although identified in linux as sda it was actually in slave position and was pointing to the wrong hdd.

Thanks for all the help at least i learnt some grub from it all.

---

