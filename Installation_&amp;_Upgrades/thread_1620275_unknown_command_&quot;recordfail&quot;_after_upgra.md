---
title: "unknown command &quot;recordfail&quot; after upgrading to 10.10"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by grr51 on 2010-11-12
Hi,

After upgrading from 10.04 to 10.10, the following message is displayed:[INDENT]**unknown command "recordfail"**
[/INDENT]In addition, for the OS selection menu, the specified timeout of 15 sec does not work anymore and screen resolution specified is not applied either.  See the attached "/etc/default/grub" file.

I can still boot Ubuntu, but Grub2 seems to have been damaged or modified during the upgrade process.  Any idea how to fix it.

Thanks,

grr51
---------------------------------------------------------------------------
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="15"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX="splash vga=795"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
# GRUB_CMDLINE_LINUX="true"

---

### Post by drs305 on 2010-11-16
I just stumbled upon this thread while searching for something else.

The behavior you describe is indicative of some of the upper sections of grub.cfg missing. These would include the definition of the recordfail routine and possibly the video module loading. 

If you post the contents of the boot info script from the following site we can see if your grub.cfg is intact.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Note:
Also, although I tested the way you have it and it still works (and I can see advantages to doing it this way), the normal method of dealing with the GRUB_CMDLINE with no options is just to leave it blank rather than comment it out:
> GRUB_CMDLINE_LINUX=""
I don't think it is causing your problem, even though the script will be looking for this variable as it builds grub.cfg.

---

### Post by grr51 on 2010-11-18
drs305, 
thank you for your reply,

I finally gave up trying to fix this problem and followed the advice that many have given, that is to do a fresh install.  So that solved my problem, although I then had to re-install some programs (e.g., Thunderbird, TrueCrypt, Wine, Sound Juicer ...).

Since I have separate partitions for root and home, all my settings were intact.  So it is not too bad. 

There always seems to be issues with a dual-boot configuration when updating Ubuntu, although I never did anything unusual with my system.  Anyway, hoping the next update will be smoother.

Thanks again,

grr51

---

### Post by drs305 on 2010-11-18
Sorry you had to reinstall. Hope this one works out better.

---

