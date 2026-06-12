---
title: "Brightness keys don't work always"
date: 2018-09-12
forum: Installation &amp; Upgrades
---

### Post by janw-oostendorp on 2018-09-12
When I put in the live CD brightness keys worked, When it was done installing brightness keys worked.
This is about 3 weekes back.
After a certain point it stopped working.
So I fiddled with the *acpi_backlight=vendor* and *video*. *grub-update*, *grub-update2*, update-grub from recovery and a bunch of combinations.
After a certain point it worked again.
And then it broke agian. 
Last week was an update and the keys worked again. When I shutdown it got stuck on some process ( I can't recall which one )
And after that the keys where broken again. I tried a bunch of combinations again but nothing worked.

**Where do I start looking? **


I'm on Ubuntu 18.04 fully updated. [This is my laptop]("https://tweakers.net/pricewatch/1209821/hp-pavilion-15-cx0670nd/specificaties/") My */etc/default/grub* file looks like this:[URL="https://tweakers.net/pricewatch/1209821/hp-pavilion-15-cx0670nd/specificaties/"]

[/URL]```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

