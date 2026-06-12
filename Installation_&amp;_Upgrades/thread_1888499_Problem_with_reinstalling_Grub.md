---
title: "Problem with reinstalling Grub"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by grubgy on 2011-11-29
Hello,

I had a primary Windows XP installation and installed ubuntu next to it using the grub bootloader.

I had to replace XP with 7 and tried to reinstall grub afterwards.

Figured out sda6 was mz ubuntu system partition and used mounted that before doing grub-install.

After rebooting I do not get the boot menu but a grub prompt.

Boot repair did not change that.
Here is the output
[http://paste.ubuntu.com/753880/](http://paste.ubuntu.com/753880/)

---

### Post by oldfred on 2011-11-29
Was this Ubuntu install an upgrade where you kept grub legacy?

You still have menu.lst in sda6 and no grub.cfg(grub2). But you have installed the grub2 boot loader to the MBR. Since it cannot find grub.cfg it will not boot.

You can chroot into your system and create a grub.cfg, but you may be able to use supergrub to directly boot and then create the grub.cfg inside your install.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Once in your system with either supergrub or chroot, you need to run this to create the grub.cfg.
sudo update-grub

Or it may be better to totally refresh. Also after you are in your system.

sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Another alternative may be just to install old grub to the MBR. But sometimes the grub & grub2 get confused and do not work correctly. Best to have clean install of one or the other, but not both.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by grubgy on 2011-11-29
the ubuntu probablz started with grub 1 and kept it I guess. My attempts to reinstall grub installed grub2 and this was not compatible with the existing grub on sda6?

Right now I can not enter ubuntu nor windows so burning another image is not possible.

---

### Post by raja.genupula on 2011-11-29
Hi man 
well may be this link can helpful to you
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)

---

### Post by drs305 on 2011-11-29
If you ran grub-install successfully from a LiveCD with Grub 2, you may have enough of the files necessary to manually boot.

When you attempt to boot, do you get a 'grub-rescue' prompt?

If so, run these commands and then reply here with the answers to the questions after the # symbols:

```

ls (hd0,6)/ # Do you see 'initrd.img' and 'vmlinuz'
ls (hd0,6)/boot/grub # Do you see lots of *.mod files
```

---

### Post by grubgy on 2011-11-29
> **drs305 said:**
> 
```

ls (hd0,6)/ # Do you see 'initrd.img' and 'vmlinuz'
ls (hd0,6)/boot/grub # Do you see lots of *.mod files
```


Both directories contain the mentioned files but aren't they from the original grub 1 installation and grub 2 sits in my MBR?

---

### Post by drs305 on 2011-11-29
> **grubgy said:**
> Both directories contain the mentioned files but aren't they from the original grub 1 installation and grub 2 sits in my MBR?

You didn't indicate if you had a 'grub-rescue' prompt, which is important.

Since Grub 2 was installed in the MBR, I'm assuming the LiveCD you used contained Grub 2 and not Grub legacy. The 'grub-install' command puts the required Grub modules in /boot/grub and builds a core.img file. I'm hoping you have a 'grub rescue' prompt and the modules are from Grub 2.

I'm thinking that perhaps the boot repair tool was confused by the presence of menu.lst with a Grub 2 MBR and that's why it didn't repair things.

Anyway, if you have a grub rescue prompt, try this:
```
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod (hd0,6)/boot/grub/linux.mod
linux (hd0,6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,6)/initrd.img
boot
```

If it boots, run:
```

sudo apt-get install --reinstall grub-common
sudo update-grub

```

---

### Post by grubgy on 2011-11-29
I guess my MBR is sort of messed up.
When I boot the system I only get a
grub> prompt. Not grub-rescue>

Also above the prompt it says:

GNU GRUB version 1.99-12ubuntu5

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere elte TAB lists possible device or file completions.

So the prompt is grub1 :confused:

---

### Post by drs305 on 2011-11-29
The 'grub' prompt is even better. Try the commands anyway.

In the previous thread YannBuntu reminded that you said your /usr folder was also a problem and that's why Boot Repair probably didn't work. I'd forgotten your mention of the /usr problem, but try the commands in the previous post anyway just to see if it boots.

---

### Post by YannBuntu on 2011-11-29
Hello grubgy

As said above, your Ubuntu contains GRUB1 (which is obsolete). To remove it and install GRUB2 instead, just choose the "Purge and reinstall GRUB" option in the Advanced options of Boot-Repair. (and indicate us the new URL in case you still have troubles).

---

### Post by grubgy on 2011-11-29
It managed to boot ubuntu and I did the reinstall and update grub lines. The last one gave me options to keep the old menu.list or the new one. Since the old was containing xp I thought the new one would make more sense.

Restarting the system leaves me in the grub prompt again.

---

### Post by grubgy on 2011-11-29
> **YannBuntu said:**
> Hello grubgy

As said above, your Ubuntu contains GRUB1 (which is obsolete). To remove it and install GRUB2 instead, just choose the "Purge and reinstall GRUB" option in the Advanced options of Boot-Repair. (and indicate us the new URL in case you still have troubles).


With the above lines I managed to boot the original system. Is it possible to fix or reinstall grub2 from there? Just asking because there seems to be a problem with my optical drive and booting the live cd takes 20 minutes and boot-repair isn't much faster. Also the buttons in the advanced settings of boot-repair regarding grub were dithered the last time I tried to do something there.

---

### Post by drs305 on 2011-11-29
> **grubgy said:**
> It managed to boot ubuntu and I did the reinstall and update grub lines. The last one gave me options to keep the old menu.list or the new one. Since the old was containing xp I thought the new one would make more sense.

Restarting the system leaves me in the grub prompt again.

Boot again, ensure you have an Internet connection, and then completely purge and reinstall both grub-common and grub-pc. When you get to the install selection, make sure the asterisk is next to sda and NOT sda6. You select/deselect a drive or partition with the spacebar, and TAB to get to OK.
```
sudo apt-get update # check internet connection
sudo apt-get purge grub-common # This will also remove grub-pc. Disregard the warning as long as you have an Internet connection.
sudo apt-get install grub-pc # Installs grub-common and grub-pc (Install to sda, not the partition)

```

---

### Post by grubgy on 2011-11-29
You made this world a better place...

=D>

---

### Post by drs305 on 2011-11-29
I'll take that as an affirmation you now have a working Grub 2. :-)

Once you are sure it is working, if you don't have any other issues, please mark the thread SOLVED via the 'Thread Tools' link near the top right of the original post. (It's reversible)

Happy Ubuntu-ing !

---

