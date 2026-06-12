---
title: "Newbie needs GRUB help"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by newbie001 on 2008-04-26
Ok, not a total newbie.  An old loadlin user.  :-)

But this is my first time installing any Ubuntu.  Heron(AMD64).

I have /dev/sda dedicated to WinXP.
I am loading Heron on /dev/sdb.

1. I told the installer to put the bootloader on /dev/sdb.

2. I rebooted to WinXP (default boot volume is /dev/sda) -- good.

3. I restart the box and drop into BIOS setup and select /dev/sdb for boot.  Yes, I am paranoid.

4. Exit BIOS, continue booting from /dev/sdb.

5. GRUB offers me several boot choices for ubuntu and even offers to boot WinXP for me.  Cool.

6. If I select any ubuntu boot, grub gives Error 17 (can't mount selected partition).

7. If I select WinXP, grub gives Error 13 (invalid or unsupported executable type)

I'm reading the grub docs for how to check the menu, and what I really want to do is drop into a minimal shell that will let me see /etc/fstab.  I haven't figured out how yet with grub.  Am I on the right track?  Can someone give me a boost?

Thanks!

---

### Post by a10waveracer on 2008-04-26
So the problem is that you've switched around how grub is accessing the harddrives.  You have two choices:

1) Drop into the grub prompt and reinstall it from there (and therefore reinstall it onto "sdb" and have that be the first drive)

2) Reinstall Ubuntu and install Grub on "sda"

In my overly humble opinion, I would just recommend installing it on sda.  You seem to know what you're doing in terms of linux and the overall idea of bootloaders, so it isn't a far stretch to say that you could manage to pop in your windows install CD and repair the windows bootloader if it completely messes up.

Either way, here's a neat little link that tells about your problem and proposes some solutions.  If you need more help, let me know.

[http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard](http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard)

---

### Post by newbie001 on 2008-04-26
Thanks, a10.

Ah.  Grub is smarter than me.  It must have noticed the boot order set in BIOS and, when I switched it, realized that I had pulled a bait-and-switch.

I'll read the link you cited.  Paranoia got the better of me.

Thanks!

---

