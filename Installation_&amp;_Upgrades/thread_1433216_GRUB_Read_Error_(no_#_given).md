---
title: "GRUB Read Error (no # given)"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by InkyDinky on 2010-03-18
I've installed 9.10 from a live cd and grub is dead. This is what I see and what I've done so far.
9.10 is going on an old Toshiba Tecra laptop with Win xp dual booting on it.


At boot
```

Booting
GRUB Read Error
Insert system disk in drive.
Press any key when ready..

```
I then pop in the live cd and select "Boot from local disk"
The screen then says 
```
Booting from local disk.
GRUB loading

```

GNU GRUB version 1.97~beta4 shows up.  It shows 2.6.31-20-generic and 2.6.31-14-generic as bootable kernels as well as memtest and win xp.

 I select 2.6.31-20-generic and it boots just fine.

I have not gotten it to boot successfully without putting in the livecd.

I've tried the [ Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") How to reinstall GRUB2 with no success.

cat of /etc/default/grub
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

It seems odd that I get a Grub read error on normal boot, but then I pop in the livecd and still choose "Boot from local disk" and there isn't the error. Am I missing something?
Thanks,
Nick

---

### Post by InkyDinky on 2010-03-18
I got rid of the error message by entering the bios and changing the boot sequence.
It was previously set to boot cdrom->lan->??FDD->?HDD
I then set it so that it boot HDD->CDROM-> ???
This fixed the problem.

---

