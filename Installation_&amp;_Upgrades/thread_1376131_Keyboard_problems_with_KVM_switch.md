---
title: "Keyboard problems with KVM switch"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by wws944 on 2010-01-08
Hi,

I have a Belkin Omniview SOHO 4-port KVM switch which accepts a PS/2 style keyboard and mouse, and provides a USB output to the computer.  I have been using this setup for years with several unix-like systems (e.g., Redhat, IRIX), and several Windows systems (NT 4, XP, Vista) with no problems.  However on my brand new ubuntu system, some (important!) keys on the keyboard are wrong.  In particular:

 ESC - dead
 Caps lock - dead
 left Ctrl key - dead
 backslash/vertical bar key - dead
 right Ctrl key - maps to Caps lock
 Alt keys - dead
 arrow keys - three are dead, left arrow sends '<'

I am sure there are others...

I have tried various settings of 'generic' keyboard mappings in the keyboard preferences to no avail.  FWIW, the keyboard is a Silicon Graphics keyboard that came with my SGI O2 many years ago.

If I plug a USB keyboard directly into my mother board, things work great.  The mouse and monitor also work fine through the KVM.

Any thoughts?

---

### Post by mystmaiden on 2010-01-10
I have a kvm switch with a ps/2 connection for mouse and monitor, when I plugged in a usb mouse - everything went whacky. I tried an adapter to plug the mouse in through the kvm and I also tried just plugging the mouse straight to the computer - no deal. It messed up the screen resolution and several other things. I gave up on the usb mouse and voila' everything went back to normal. Not sure if this is a related problem, but it seems it may be.

---

### Post by wws944 on 2010-01-18
I seem to have figured out a way to make things work.  Apparently, it is very important to make sure the KVM switch is set to the proper computer *before* powering up and booting the OS.  Otherwise, somewhere in the hardware discovery process, things get confused and the wrong keyboard settings are used.

---

