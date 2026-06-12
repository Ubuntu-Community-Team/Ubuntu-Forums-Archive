---
title: "Dapper won't boot, endless boot cycle!"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by garton on 2007-01-14
I just installed Ubuntu 6.06 on a AMD K6-2 500 machine. The installer CD boots fine and the installation was successful. However, when I try to boot the machine it fails. This is what happens;

1. All BIOS info is printed and control is handed over to GRUB
2. GRUB does the countdown thing (3... 2... 1... and so on)
3. The default boot sequence is automatically selected and initiated
4. The GRUB info is printed to the screen, ending with the "boot" command
5. No splash screen is shown
6. The machine is restarted, and this cycle is repeated infinately

I've done the following:

- Ran memtest from the install CD, no errors
- Still, tried with a few different RAM-sticks, no change in behaviour
- Entered the GRUB console to see if GRUB could, in fact, access the hard drive, which it could, I could look at files and everything
- Removed the "quiet" and "splash" options from the GRUB config before booting, to see if the kernel ever prints anything at all, which it doesn't. Nothing at all. The last thing I see before the machine reboots is the GRUB "boot" command.

More info:

The ISO I installed from was ubuntu-6.06.1-server-i386.iso, downloaded from [http://ftp.port80.se/ubuntu-cd/6.06/](http://ftp.port80.se/ubuntu-cd/6.06/)

Any ideas?

TIA!

EDIT: Of course, I have also tried the "recovery" boot option in grub, which gives the exact same result as the non-recovery option.

---

### Post by happy-and-lost on 2007-01-14
For a start, if you want a normal desktop install, you want the ubuntu-6.06.1-desktop-i386.iso

The one you're trying to install is the server edition :)

---

### Post by garton on 2007-01-14
> **happy-and-lost said:**
> For a start, if you want a normal desktop install, you want the ubuntu-6.06.1-desktop-i386.iso

The one you're trying to install is the server edition :)

I know that. It's a server I want, not a desktop.

---

### Post by icefaerie on 2007-01-14
I've had this same problem (I even filed a bug report about it, but AFAIK it's not been fixed) on my server.  The solution I used was to do the server install from the alternate CD.  Apparently the LAMP install does that endless-boot-cycle behavior on some older motherboards.

---

