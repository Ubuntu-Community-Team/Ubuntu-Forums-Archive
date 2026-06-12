---
title: "Troubles with Drivers on a HP Pavilion dv5000 running 14.04"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by edoardo3 on 2014-04-30
Hello guys,
I have recently installed the new lubuntu version on a HP Pavilion dv5000, with acpi=off noapic and nomodeset since it's a very old pc, but i'm having tons of troubles with the configuration of some drivers. I'd be very grateful if someone could help me.
 Now i'll try to explain everything and, please, forgive my poor english. I'll try my best :)

I don't know if it's useful, but anyway the pc was running Windows XP before.

The main problem is the one about the wi-fi drivers (the laptop uses a b43-Broadcom wi-fi) which at the start i couldn't find in the "addictional drivers" section. After many tries working with the terminal i could finally get it in the window so i switched it on and just rebooted the pc. After the restart i went to the addictional drivers window to check it out and, best part, the broadcom driver had magically disappeared, and of course the wi-fi didn't work. Again, i tried with the terminal, but nothing happened. So i just left the pc untouched for a day. Today i restarted the pc and just for curiosity i checked the addictional drivers section and, yeah, the broadcom driver was there, smiling at me and turned off. So i switched it on (And while i did it i noticed the wi-fi led turning on so it is working) and i waited for the loading bar to fill. At the end of the process i closed the addictional drivers windowbut this time, instead of restarting the pc, i just opened that window again. And yes, no more Broadcom driver.

Another problem is with the touchpad of the laptop. The first day i installed lubuntu it didn't work, then, today, when i started the pc after a day of non utilising it, it worked. after the first restart it didn't worked again. Nice!

Finally, the last problem, is the one about turning off the pc. It just doesn't turn off. Even with sudo shutdown -h or anything else it goes in the lubuntu screen and just doesn't halt. So thanks to the internet i tried modifying the grub file with very poor results. Here the grub file i'm using right now. 
> [B]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=bios "
GRUB_CMDLINE_LINUX="acpi=off noapic nolapic nomodeset"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'[/B]

What i thought at first is that there was some low energy mode going on, which de-activated all the drivers that are giving me those troubles, that's why i tried to acpi=off & co. at the boot. But no improvements yet. 
So yeah guys i think that's all, hope you can find something new to try. I hope i have been clear enough and, again, forgive my english if it's not perfect. If you guys need more technical info just let me now and i'll do everything i can.
Yeah, sounds like a fine challenge for you guys!

_UPDATE:_
 [B]
Wireless[/B]: Actually works, it seems i installed other drivers which were not useful then i just apt-get purge them and now the wi-fi is working fine. I have another problem about the wi-fi but i'll post in the right section if i can't solve it by myself. Thanks for the help ubfan anyway.

**Shutting Down/Restart**: It seems that if i go in the login screen and i press Reboot the pc actually reboots, strange because if i normally reboot during the session it always gets stuck in the lubuntu screen.

---

### Post by ubfan1 on 2014-04-30
On a wired connection (which should work), run 
sudo apt-get install linux-firmware-nonfree
And the b43 driver should work.  Clean out any leftover broadcom configuration which suppresses the b43 driver by removing any broadcom packages you might have installed, and check that in /etc/modprobe.d the exact line "blacklist b43" does not exist in any file.

---

