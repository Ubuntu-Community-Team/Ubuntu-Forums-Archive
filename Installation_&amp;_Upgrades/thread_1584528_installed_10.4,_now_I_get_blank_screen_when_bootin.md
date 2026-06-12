---
title: "installed 10.4, now I get blank screen when booting linux"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by ducttapeandzipties on 2010-09-29
I had 9.10 on my asus eee900 running off the SD card.  I downloaded 10.4 and used unetbootn to make a usb key of it.  The install looked like it went fine but when I try to boot it all I get is a blank screen with a blinking cursor.  I tried installing it on the ssd and it boots and runs fine.  I can even mount the SD and see the install on there, so the card is fine and it is in fact installed, It just won't boot.  

Any ideas on where I should start looking?  I'm not sure what to check next.

---

### Post by ducttapeandzipties on 2010-09-29
When I boot the ssd I see the option for the intallation on the sd card but trying to boot it goes to the blank screen.

my /boot/grub/grub.cfg:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by ducttapeandzipties on 2010-10-01
Do I need to partition and format before I install?  The installer should take care of all that for me right?

---

### Post by Rubi1200 on 2010-10-01
What graphics card do you have installed?

---

### Post by dino99 on 2010-10-01
is it a dist-upgrade or a clean install: now grub2 is used and dont like menu.lst from grub1

you might have a driver issue, on the boot line add either: nomodeset, nolapic, noapic, noacpi, irqpoll
( edit (E) the boot line into grub menu to do it, then ctrl+x to boot)

---

### Post by ducttapeandzipties on 2010-10-01
This is a clean install via usb on an asus eee 900 netbook.  I'm not sure what video card is in this machine, but it worked perfect with 9.10.  And 10.4 installs and works on the ssd hard drive, but the problem is I need it on the SD so I can install windoze on the internal.

---

### Post by ducttapeandzipties on 2010-10-01
> **dino99 said:**
> is it a dist-upgrade or a clean install: now grub2 is used and dont like menu.lst from grub1

you might have a driver issue, on the boot line add either: nomodeset, nolapic, noapic, noacpi, irqpoll
( edit (E) the boot line into grub menu to do it, then ctrl+x to boot)

I'm not even getting that far.   As soon as the bios screen disappears it goes straight to the balck screen with blinking cursor.  It's as if the SD card is damaged or not set up to be bootable.   /var/log/boot says "(Nothing has been logged yet.)"  If I boot from the internal ssd, I can read the sd card and see the files there, the thing just acts like i'm trying to boot a drive that is shot.

---

