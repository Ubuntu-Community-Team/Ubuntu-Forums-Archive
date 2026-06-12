---
title: "Question about partitioning on install"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by Jenuall on 2007-06-15
Hi there,

I've just decided to install ubuntu on my laptop and am working my way through the installation. I'm following this guide [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) to aid me in setting up a dual boot installation of ubuntu. I've got a question about step 4 "prepare disk space" - basically I want to use option 1 "Guided" as it seems the safest for a new-comer, but the language used is slightly unclear:


"Guided - resize SCSI1(0,0,0), partition #1 (sda) and use freed space

New partition size: XX% (XX GB)"


Now does this mean it will create a "new" partition on this disk of size XX and install ubuntu onto here, or does it mean that it will resize the current windows partition to XX and install ubuntu onto the freed space?

Thanks for any help - just want to get this right as I want to give linux a fair chance to impress me, and messing up my partition during installation may just bias me against it a bit!

---

### Post by merlinus on 2007-06-15
The latter is correct.  Re-size windows partition to xxx and then use freed-up space for ubuntu.

Best to get rid of all temp files and defrag windows several times first.

-merlin

---

### Post by Jenuall on 2007-06-15
Thanks, that's helped me get up and running!

One further question - Is there a way to make Windows XP the default option in the boot loader? Several other people use the laptop and it would be simpler if they didn't have to select an OS at startup!

---

### Post by merlinus on 2007-06-15
Sure.  You will have to change one setting in /boot/grub/menu.lst.

Make a backup first, so if things go haywire you can restore it.

```

sudo cp /boot/grub/menu.lst /boot/grub/menu_old.lst

```

Then:

```

gksudo gedit /boot/grub/menu.lst

```

Count the number of kernel stanzas, including the last one for windows.

Here is an example of a kernel stanza:
> 
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74ea0d79-f0a5-4381-a98d-08258758e696 ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

and here is an example of the windows stanza:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Look for the line that says:

default    0

It is near the beginning of tthe file.

Change it to the number that is windows, minus one.

For example, if windows is the fifth, then change default to 4.

You can also change the timeout setting, the number of seconds before the default choice starts up.

Look for the line that says:

timeout    15

and change it to anything you like.

5 would be the least.  Otherwise you will have to press Escape quickly to be able to choose ubuntu! 

-merlin

---

