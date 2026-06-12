---
title: "editing boot option with win xp as dual boot"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by matrunner on 2007-07-12
i have ubuntu feisty fawn....also upgraded using official auto update....now i have 4options with UBUNTU itself with diff kernel version option & their recovery mode....i want to remove the entry of older kernel version as i feel its not going to be so useful....hw to do it

                             another thing i am not lone user of system, others utilising it prefer xp so i want to set xp as default loader as time seconds end....hw to do it....

---

### Post by luctor on 2007-07-12
My ubuntu box is in dutch, so I hope i translate it correctly :-)

1)  take a look at /boot/grub/menu.lst to lookup the name of your old kernel
```

cat /boot/grub/menu.lst

```
2) use synaptic to remove the kernel you don't need anymore, this should also remove the boot options in the /boot/grub/menu.lst. Be very carefull to remove the proper kernel ....

3) edit /boot/grub/menu.lst
```

gksudo gedit /boot/grub/menu.lst

```
Look for the line
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

```

As you can see above, numbering starts from 0 so if all goes wel you should have the following entries in your menu.lst

1st boot should ubuntu
2nd boot entry should be ubuntu recovery mode
3rd boot entry should be Windows XP

Change "default 0"  to the desired boot entry, in your case this will probably be 2, then save the file

4) Run in a terminal
```

sudo update-grub 

```
(Don't know if this is actually necessary, but just to be safe ....)

Reboot, and it should work :-)

You might want to edit to following lines.
The things i've edited are in [COLOR="Red"]red[/COLOR]
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout [COLOR="Red"]30[/COLOR]      

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu

```

---

### Post by merlinus on 2007-07-12
You will have to edit /boot/grub/menu.lst as root and comment out (place a # iin front of) the old kernel lines.

Then count the remaining kernel stanzas, including the entry for xp, subtract one, and change 

default

to that number.

To edit menu.lst, in a terminal enter:

```

gksudo gedit /boot/grub/menu.lst

```

I recommend not deleting the previous kernel files, however, because something can go wrong and you may need to revert.

-merlin

---

### Post by matrunner on 2007-07-12
gr8 thx....
will try them.....

---

