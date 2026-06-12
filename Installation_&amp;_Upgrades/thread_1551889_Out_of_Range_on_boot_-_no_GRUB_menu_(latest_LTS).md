---
title: "Out of Range on boot - no GRUB menu (latest LTS)"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by asciibaron on 2010-08-12
when the O/S boots, i never see a Grub menu, just an Out of Range message on the monitor.  i have tried many different key combinations to switch to a TTY but no luck.

to install i had to select "nomodereset" for the display to work properly from the LiveCD and if i can get to a command prompt, i can sort out the video problems (maybe). 

video card shows up as an ATI RS880 (Radeon 4200) when i run lspci from the LiveCD.

how can i get to a command prompt?  i can edit files on the hard drive when i boot from the LiveCD, so i'm kind of stuck.  the installer does not have a place to pass comments to the kernel from what i can see.

-steve

---

### Post by asciibaron on 2010-08-12
did some digging in another thread and found that holding <SHIFT> down will force the GRUB menu.  i'm in but i'm not finding the files that i would typically modify.  

> dpkg-reconfigure xserver-xorg the command yields nothing - i get no errors, but it does not run an associated wizard.  will poke around some more.

---

### Post by asciibaron on 2010-08-12
ok, i created a new xorg.conf file with the settings for my monitor....

to recap - 

hold <SHIFT> to force GRUB menu
boot in failsafe
modify /etc/X11/xorg.conf to reflect monitor sync rates and resolutions

type startx and i'm in Gnome.

when i reboot the computer, i'm back to the issue of Out of Range.

---

### Post by confused57 on 2010-08-13
What you can try is to press "shift" to get to the grub menu, highlight the first boot entry, press "e" to edit, then add nomodeset to the kernel line, then ctrl+x to boot.  If this works, you can check in hardware drivers if there is a proprietary driver for your video card.

If there isn't a driver, you can add nomodeset to the kernel line:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

See the above link & the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". The entry "acpi=off", if required, would also be an option entered on this line. 
```

---

### Post by asciibaron on 2010-08-13
> **confused57 said:**
> What you can try is to press "shift" to get to the grub menu, highlight the first boot entry, press "e" to edit, then add nomodeset to the kernel line, then ctrl+x to boot.  If this works, you can check in hardware drivers if there is a proprietary driver for your video card.

If there isn't a driver, you can add nomodeset to the kernel line:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)


i'm going play with the Grub config file and see what that gets me - i am unfamiliar with Grub 2 and didn't know to look for the file in /etc/default/grub - i was looking for menu.lst in /boot/grub

i'll see what i can come up with when i get home.

---

### Post by saxophobe on 2010-08-13
I was having this exact same problem on a Dell Precision T1500.  By using the Shift key to force a grub menu, I was able to edit the grub file from 'quite splash' to 'nomodeset', which loaded the low graphics mode for one session.  Once I was successfully booted from the hard drive, I installed the proprietary driver and rebooted.  For now at least, everything is cool!  

I hope this helps someone!

8-)

---

### Post by asciibaron on 2010-08-14
well, i decided to punt.  i went out and bought a new monitor.  the problem went away when i used my wife's LCD so instead of trying to rig the OS to play nice, i decided that my 6 year old LCD can go to my son.

here's the really cool thing - i'm dual booting with Win 7 and Ubuntu recognized the resolution (1920x1080) without doing anything - it took me 45 minutes to get the Win 7 to play nice with the display.  plus, Ubuntu looks gorgeous.

---

