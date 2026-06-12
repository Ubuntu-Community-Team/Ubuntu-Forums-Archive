---
title: "Corrupted installation"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by yidaho on 2008-02-07
Hi,

When I boot the computer up it come up will the grub Ububtu/Windows menu but if you select Ubuntu the OS doesn't install.  I guess it's become corrupted somehow.  Windows Vista loads up OK.

I guess my two options are to either reinstall Ubuntu and hope it fixes the problem or uninstall and re-install Ubuntu.

P.S.  I can't find my Vista disk to fix the MBR so that it boots straight into Vista either.

Anyone any advice on what's the best way to sort this out.

regards,

Paul

---

### Post by Pelham123 on 2008-02-08
What happens when you try to boot Ubuntu from the grub menu? Does it come up with a grub error? Does it hang or crash? Do you get as far as the splash loader? Give us a bit more info ;)

---

### Post by yidaho on 2008-02-08
Hi Pelham123,

Grub menu -> Ubuntu 7.10, kernal 2.6.22.14-generic etc
Select Ubuntu from list
Kernal alive, kernal mapping ..... message at the bottom of screen, blank screen and some hard disk activity that nothing happens, just a blank black screen.

---

### Post by Pelham123 on 2008-02-08
Maybe this post will help...

[http://ubuntuforums.org/archive/index.php/t-516033.html](http://ubuntuforums.org/archive/index.php/t-516033.html)

Note the edit for *nosplash noapic nolapic *additions to the boot line. Fair amount of waffle there tho ;)

---

### Post by yidaho on 2008-02-08
Waffle, are you not kidding!

"Retry using this boot parameter (make sure to hit F6 first).

nosplash noapic nolapic"

F6 doesn't seem to do anything.

On  the grub menu you can edit the boot commands, do you add the "nosplash noapic nolapic" command and where if you do (first line?)

---

### Post by Pelham123 on 2008-02-08
At boot up press `esc` to enter Grub menu. Highlight ubuntu, then press 'e' to enter edit mode.

Scroll down to the "kernel..." line (this tells grub the flags to be passed to the kernel when ubuntu boots)

Press 'e' again to edit this line.

Move to the end of the line with arrow keys, you'll see existing flags and can add other new flags to the end, ie *nosplash noapic nolapic *

Press Enter to accept the editing.

Then press 'b' to boot using that kernel and those flags...

---

### Post by yidaho on 2008-02-14
Tried the options stated but no luck.  Found my Vista disk and 'fixed' the MBR and decided to do a clean installation.  HA!

Boot from Live CD, first menu ran install option, blank screen and disk whirring for a while then nothing!

??

Anyone had this when trying to install Ubuntu 7.10 64-bit version?

---

