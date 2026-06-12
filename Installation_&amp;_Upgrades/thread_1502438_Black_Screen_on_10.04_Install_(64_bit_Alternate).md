---
title: "Black Screen on 10.04 Install (64 bit Alternate)"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by lightnb on 2010-06-05
I'm attempting to install 10.04 64 Bit using the alternate CD on an Asus M4A88TD-M Motherboard. I'm using the on-board graphics, which is ATI Radion based.

I can run the Windows XP installer and the Ubuntu 8.10 Live CD / Installer without issues.

When attempting to install 10.04, the CD loads, and asks for a language. I choose English. I then get the menu with "Install", "Check memory", "Boot from first hard drive", etc. I choose "Install".

I get a blank screen with a blinking underscore in the top left corner for a few seconds, then the screen goes blank and stays blank. I have tried running the installer with the "nomodeset" option, and get the exact same result.

I have tried multiple CDs and CD Drives.

Anything else I can try?

---

### Post by davidmohammed on 2010-06-05
I presume you are definitely using the 64bit AMD alternate CD?

Have you tried "nomodeset xforcevesa" as your boot options?

---

### Post by lightnb on 2010-06-05
xforcevesa isn't on the F6 options menu... But I tried adding it manually after the "--" to no effect.

I tried installing with:

--nomodeset xforcevesa

and with:

--nomodeset --xforcevesa

Both of which do the same thing- a blinking cursor then a black screen.

I've used this CD to install on another machine (different hardware) successfully.

---

### Post by davidmohammed on 2010-06-05
add nomodeset xforcevesa before --

suggest also remove quiet splash

your boot line should look something like

.....initrd.gz **nomodeset xforcevesa** --

---

### Post by lightnb on 2010-06-05
Thanks! It appears to be working now. Am I going to run into other problems down the road though? Will I have to modify GRUB to use those boot options too? And will I still be able to enable advanced desktop effects?

Thanks again,
Nick

---

### Post by acrazyplayer on 2010-06-05
you may have to permanently change the grub entries by using "sudo gedit /etc/default/grub" and adding there what you did during your successful boot

---

### Post by davidmohammed on 2010-06-05
... agree you'll need to add to grub.

However, the option xforcevesa is just to get to a basic desktop - there will not be any fancy graphics etc.

As you have said you cannot boot with just nomodeset, then your issue is with the ATI graphics driver.

Can you confirm if this is a new install or an upgrade?

If its an upgrade the rename the file /etc/X11/xorg.conf to something else.

Can you then boot with just nomodeset?

If not, then is there any graphics drivers suggesting in administrator - hardware drivers?

If not, then please confirm the actual ATI graphics chip you've got

lspci | grep VGA.

Its likely you'll need to install a proprietary driver from ATI - the driver to be installed obviously depends on your graphics chip.

---

### Post by lightnb on 2010-06-05
Ok, finished the install, trying to do first boot.

I've modified GRUB via the "rescue a broken system" option on the CD to include "xforcevesa" option, and removed "quiet".

But it hangs with a blinking cursor after the message about loading the sata drives.

I can no longer enter rescue mode from the CD either, since after choosing rescue mode, it starts loading, then hangs with a blinking cursor too.

P.S. This is a new install.

---

### Post by davidmohammed on 2010-06-06
OK - once installed, put you CD to one side.

Just after the bios screen is displayed, press shift.  This will display grub listing all your kernels.  Press e.  On the line with quiet splash, insert the options

nomodeset xforcevesa

n.b.

you can delete quiet splash for the moment.

CTRL + X to boot.

---

### Post by lightnb on 2010-06-07
Got it working, thanks!

---

### Post by sailor420 on 2010-06-11
I had this same problem, and davidmohammed's instructions got me booting. Once I installed proprietary video drivers (nvidia in my case), the machine boots as normal.

Thanks!

---

### Post by tizo_rh on 2010-06-13
I have exactly the same problem with the alternate installer (64 bit version). My computer is an HP 550 notebook, and it works perfect with Ubuntu 8.10. In that OS, with lshw it says that the vga display is Mobile GME965/GLE960 Integrated Graphics Controller (Intel), and I think that the driver used is i915.

I have tried a bunch of parameters in the grub line, and a lot of combinations. Those were i915.modeset=1, i915.modeset=0, nomodeset, acpi=off, vga=771, simple, xforcevesa, deleting the quiet parameter, etc.

The behavior is:

 - If vga=771 is not present, after pressing enter to start the installer, a cursor can be seen blinking at top left corner for 3 or 4 seconds, and then a blank screen appear. I know that is a display problem because the CD continues working for a few more second, and the computer can be reset without problem with ctrl-alt-sup.

 - If vga=771 is present, the result is exactly the same, except that in the blank screen, a short red rectangle, almost as wide as the screen is seen in the top of it. Some white points blinking can also be seen before the red rectangle appears. It seems to me that is a typical graphical driver problem when starting X, but should alternate installer try to start X?.

The normal installer works fine, but I have to use the alternate one, as I need LVM support.

Thanks very much for your help.

tizo

---

### Post by tizo_rh on 2010-06-13
I could solve my problem with a somewhat tricky procedure:

 - Boot the live CD. From it:
  - Install lvm2 package.
  - Define my LVM partitions.
  - Run the installer.
  - Choose the new LVM partitions to install the system.
  - Install the system.
  - chroot to the new system (still from the live CD).
  - Install lvm2 in the chrooted system.
  - Restart the computer.

That is all. Thanks.

---

