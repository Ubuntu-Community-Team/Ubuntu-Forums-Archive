---
title: "dual boot 12.04 - boot fails after running update manager"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by aa4bb on 2012-05-30
I have a HP tx2500 Vista laptop to which I added 10.04 in dual boot config and ran it successfully for two years.

This week, I installed 12.04 in a new partition (vista and 10.04 retained), Everything worked perfectly and the boot menu showed 12.04, 10.04 and vista and would load into any of the three.

I ran update manager this morning. It called for a reboot. When the boot menu came up, it showed 10.04 and vista, and looked like the boot menu I had with 10.04, but 12.04 was not on the menu.

I booted 10.04 and looked at the HD with disk utility. The 12.04 partition shows up and is the correct size and designation  /dev/sda7.

I don't know where to go from here.

---

### Post by Shadius on 2012-05-30
> **aa4bb said:**
> I have a HP tx2500 Vista laptop to which I added 10.04 in dual boot config and ran it successfully for two years.

This week, I installed 12.04 in a new partition (vista and 10.04 retained), Everything worked perfectly and the boot menu showed 12.04, 10.04 and vista and would load into any of the three.

I ran update manager this morning. It called for a reboot. When the boot menu came up, it showed 10.04 and vista, and looked like the boot menu I had with 10.04, but 12.04 was not on the menu.

I booted 10.04 and looked at the HD with disk utility. The 12.04 partition shows up and is the correct size and designation  /dev/sda7.

I don't know where to go from here.

The first thing I would try is running:
```
sudo update-grub
```
to update the GRUB menu

---

### Post by aa4bb on 2012-05-30
Thanks, Shadius. That did restore 12.04 to the boot menu. It's down at the bottom now, so I have to figure out how to move it up to the top so it will be the default.

---

### Post by drs305 on 2012-05-30
> **aa4bb said:**
> Thanks, Shadius. That did restore 12.04 to the boot menu. It's down at the bottom now, so I have to figure out how to move it up to the top so it will be the default.

Your earlier installation is still controlling grub. To get 12.04 to take control of the boot (and put it at the top of the menu), run the following command *while running 12.04*. It assumes sda is your primary boot drive. Do NOT use the partition number in the command:
```

sudo grub-install /dev/sda
```

This will write information in the MBR to look at your 12.04 partition for the Grub files rather than your earlier one.

---

### Post by aa4bb on 2012-05-30
drs305:

Perfect! Thanks very much!

Please indulge me one more related question. When Update Manager runs, it sometimes makes a new entry to the boot menu. From appearances, that seems to be when a new version of the kernel is installed. It's not really a problem, except after many updates, the menu is long and looks messy and when I do have to boot Vista, I have to scroll way down the screen. 

Is there a reason to retain all those old entries, and if not, an easy way to remove the outdated ones?

---

### Post by drs305 on 2012-05-30
> **aa4bb said:**
> drs305:

Perfect! Thanks very much!

Please indulge me one more related question. When Update Manager runs, it sometimes makes a new entry to the boot menu. From appearances, that seems to be when a new version of the kernel is installed. It's not really a problem, except after many updates, the menu is long and looks messy and when I do have to boot Vista, I have to scroll way down the screen. 

Is there a reason to retain all those old entries, and if not, an easy way to remove the outdated ones?

:-)  

Glad you asked.  Grub 1.99 introduced the 'submenu' concept. It's the version in 12.04 but not in 10.04. When there is more than one kernel on the main OS, it puts the older kernels in a submenu so the main menu doesn't continue to grow. Only the most recent kernel (and recovery mode) are displayed for the current OS.

For 10.04, you really don't need more than one older kernel. If you remove them, the menu will shrink. The most 'comfortable' way to remove the older ones is with Ubuntu Tweak while running 10.04. And don't forget to run "update-grub" within 10.04 after doing this.
Here are the appropriate links:
[https://help.ubuntu.com/community/Grub2/Submenus]("https://help.ubuntu.com/community/Grub2/Submenus")

[HOWTO: Remove Older Kernels via GUI ]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by aa4bb on 2012-05-30
Again, right on the money! Many thanks, drs305!

---

