---
title: "How do I set boot order?"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2008-08-28
After I stumbled thru the Hardy install, being careful to try to not disturb the XP partition or the Gutsy partition, I ended up with about 6 or 8 boot options. That's OK, I tried them all out and got an idea of what they do and which is the latest best Hardy. So then I wanted to make that Hardy the default option. I found /boot/grub/menu.lst and tried re-ordering it, but no luck.

How the heck can I edit something to get the boot order I want?

---

### Post by iaculallad on 2008-08-28
Open your menu.lst file for editing:

```
gksudo gedit /boot/grub/menu.lst
```

and locate the line of text (colored BLUE) below:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="Blue"]default         0[/COLOR]**

```

and change the number "0" with the value of Hardy in your menu.lst file. Counting will start to "0" and incrementing by 1.

So, here's a Sample:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic   **[COLOR="Blue"]<---- 0[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)  **[COLOR="Blue"]<---- 1[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic   [COLOR="Blue"]**<---- 2**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)   **[COLOR="Blue"]<---- 3[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+   **[COLOR="Blue"]<---- 4[/COLOR]**
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Counting will continue until it reaches your last boot option.

If I want to make Ubuntu 7.10 (Recovery Mode) as my default, I will replace 0 with 3 in:

```
**[COLOR="Blue"]default         3[/COLOR]**
```

And, Save and close the file.

---

### Post by jpkotta on 2008-08-28
> **bliffle said:**
> After I stumbled thru the Hardy install, being careful to try to not disturb the XP partition or the Gutsy partition, I ended up with about 6 or 8 boot options. That's OK, I tried them all out and got an idea of what they do and which is the latest best Hardy. So then I wanted to make that Hardy the default option. I found /boot/grub/menu.lst and tried re-ordering it, but no luck.

How the heck can I edit something to get the boot order I want?

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

```

Change the "default" option in menu.lst.  To choose the first entry, set default to 0; to choose the second, set default to 1; etc.  When Ubuntu updates the kernel, it automatically puts the newest one at the top of the list, so default 0 is probably what you want.  The list at the end of menu.lst is regenerated each time the kernel is updated.

Edit: I'm slow.

---

### Post by bliffle on 2008-08-30
OK, I see how to set the default boot. Thank you.

But can I set the boot order? I tried shuffling the various entries in "/boot/grub/menu.lst" around to get the boot selector to present them to me in order of what I figured would be my preference.

But that didn't work.

Did I change the wrong file? Do I need to run some program before rebooting to establish the new menu.lst?

---

### Post by caljohnsmith on 2008-08-30
> **bliffle said:**
> OK, I see how to set the default boot. Thank you.

But can I set the boot order? I tried shuffling the various entries in "/boot/grub/menu.lst" around to get the boot selector to present them to me in order of what I figured would be my preference.

But that didn't work.

Did I change the wrong file? Do I need to run some program before rebooting to establish the new menu.lst?
Yes, you should be able to move the OS entries around in menu.lst to get whatever order you want to see them in on start up. Did you remember to modify menu.lst as root (i.e. using sudo)? Maybe your changes didn't stick. Feel free to post the contents of your menu.lst if you need further help:
```
cat /boot/grub/menu.lst

```

---

### Post by shoffman11 on 2008-08-30
> **bliffle said:**
> Did I change the wrong file? Do I need to run some program before rebooting to establish the new menu.lst?

Did you run **grub-install /dev/sdX** where X is the letter of your primary hard drive?

I usually have to do grub-install /dev/sda

Hope that helps

---

### Post by caljohnsmith on 2008-08-30
> **shoffman11 said:**
> Did you run **grub-install /dev/sdX** where X is the letter of your primary hard drive?

I usually have to do grub-install /dev/sda

Hope that helps
As you have written it, grub-install will reinstall Grub to the MBR of sda, and also recreate any of Grub's system files in /boot/grub if they are missing, *except* menu.lst. So I don't believe grub-install is going to help bliffle change the order of his OSs in his Grub menu. :)

---

