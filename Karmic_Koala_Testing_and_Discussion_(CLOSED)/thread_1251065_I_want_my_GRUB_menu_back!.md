---
title: "I want my GRUB menu back!"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-08-27
Latest GRUB update annoys me:

```
grub2 (1.96+20090826-3ubuntu1) karmic; urgency=low

  * 951_quick_boot.diff: New patch:
    - If other operating systems are installed, then automatically unhide
      the menu (LP: #411584).
    - Otherwise, if GRUB_HIDDEN_TIMEOUT is 0, then use keystatus if
      available to check whether Shift is pressed. If it is, show the menu,
      otherwise boot immediately. If keystatus is not available, then fall
      back to a short delay interruptible with Escape.
```

If I'm reading that right, there is currently no way to always show the menu (without hitting a key)? Make this poo go away!

**[COLOR="Red"]Solution:[/COLOR]**
Remove or uncomment the GRUB_HIDDEN_TIMEOUT line in /etc/default/grub (followed by a 'sudo update-grub').

---

### Post by NCLI on 2009-08-27
The menu will always be showed if either:

a) You have more than one OS installed
b) You set GRUB_TIMEOUT to more than 0.

---

### Post by MacUntu on 2009-08-27
I have GRUB_TIMEOUT=5, GRUB_HIDDEN_TIMEOUT=0 and no menu. That was working fine before the update.

---

### Post by dino99 on 2009-08-27
Here is mine, & grub menu always pop up with several distro

# This file is sourced by update-grub, and its variables are propagated
# to its children in /etc/grub.d/
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
GRUB_CMDLINE_LINUX="gfxpayload=true"

---

### Post by ranch hand on 2009-08-27
Comment out the "GRUB_HIDDEN_TIMEOUT=0" line.

---

### Post by MacUntu on 2009-08-27
Jup, that did it. Thanks.

---

### Post by claydoh on 2009-08-29
My problem is that I cannot boot to Karmic without  adding in acpi=off. I can't even boot without this, so  I can't even get to a point to be able to edit anything unless I boot to a livecd and edit files that way :(

---

### Post by MacUntu on 2009-08-29
> **claydoh said:**
> My problem is that I cannot boot to Karmic without  adding in acpi=off. I can't even boot without this, so  I can't even get to a point to be able to edit anything unless I boot to a livecd and edit files that way :(

Good point. You definitely should be able to access the menu after installation, so either this Shift key thing has to work reliably or the installer should add the Live-CD kernel   parameters to GRUB's default list. Maybe file a bug report?

---

### Post by ranch hand on 2009-08-29
You need to go to /etc/grub.d and create custom entries.

There area number of threads covering this.

---

### Post by MacUntu on 2009-08-29
> **ranch hand said:**
> You need to go to /etc/grub.d and create custom entries.

Why? /etc/grub.d is the place to go if you have installations that don't get picked up automatically or if you have special wishes like customizing GRUB's colors. The defaults for the kernel line are in /etc/defaults/grub and they should stay there. :P

---

### Post by claydoh on 2009-08-29
> **MacUntu said:**
> Good point. You definitely should be able to access the menu after installation, so either this Shift key thing has to work reliably or the installer should add the Live-CD kernel   parameters to GRUB's default list. Maybe file a bug report?


I probably will, as it is very tricky to get the shift key pressed at the right time before it tries to boot. And add to the fact that users may not know about using the shift key immediately :)

And the menu issue is kinda minor to the fact that the latest *.31 kernels won't boot without my adding in the acpi=off parameter :)

---

### Post by ranch hand on 2009-08-29
> **MacUntu said:**
> Why? /etc/grub.d is the place to go if you have installations that don't get picked up automatically or if you have special wishes like customizing GRUB's colors. The defaults for the kernel line are in /etc/defaults/grub and they should stay there. :P
Not really.  Grub.d is where all your editing of grub.cfg is done.

For instance, claydoh needs to add "acpi=off" and that can be done permenantly by adding a custom menu entry.

Another case is that you need to update grub for every new kernal update.  If you are using an OS other than the one you just updated you will have to boot to that OS to update.  On the other hand if you use a custom entry like this;
```

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva" {
set root=(hd0,12)
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}

```
it will boot every time no matter what kernal you are currently running.

Trying to keep up with the kernal on Mandriva is a nightmare, this is easy.  That is from my "01_custom" file.  I would recommend using a number between 06 and 09 to keep the 05_debian_theme file earlier in the order of usage.
EOF

---

