---
title: "Black Screen With Blinking Cursor After Fresh Install"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2013-05-05
I just did a fresh install of Ubuntu Server 13.04 and each time I reboot I get a completely black screen with just a white blinking cursor in the upper left. No Grub, nothing but the BIOS splash screen, then this. I've done a successful install twice and each time it just boots to this screen. Everything I find on Google says to hold shift to edit the Grub menu but that does nothing, Grub doesn't show at any point.

I should mention this is a server which previously had 13.04 on it, I'm just wiping and reinstalling.

---

### Post by MAFoElffen on 2013-05-06
Hello again. Same box? Server only gives 2 seconds for the Grub2 menu as a default.

-What is it (CPU/Chipset) and what video GPU?
-Does it boot the "try" Live Image of the LiveCD? I remember you said it did...
-What version of... server right? Did you go with 13.04 or 12.04LTS. Last thread you said 13.04... which I left alone.
- On the "flashing cursor"... No status messages yet? No disk activity?
- If you do a <Cntrl><Alt><F1> or <Cntrl><Alt><F4> is there anything going on in those tty sessions?

From a LiveCD, do 
```

lspci -vnn | grep -i VGA

```
Then go to post 2 of my Graphics resolution sticky. (Link in my sig line) Follow the link to "Force Grub to show." Edit the system's /etc/default/grub file from the LiveCD. Go to Post 3 of that sticky and follow the instruction to mount and chroot into the sys. The do an "update-grub". The grub menu should then show... If it still doesn't, then reinstall grub from a chroot. You can always change it back after you get everything reloaded and configured on it. 

While you are booted on the LiveCD, have a look at the server's sys logs. See where it hung at...

Note- Server is set for 2 seconds, so that after a power failure it can come back up with not much delay... But with my servers, I figure another 5 seconds couldn't hurt. After a few years, I settled on 7 seconds as a default I can live with for that setting. Makes it easier to get to it if needed.

Since it's been having "diffugalties", maybe when the grub menu does come up (crossing fingers for you), then first boot, edit the boot line add add "--verbose single" to make sure you can see all the boot messages and confirm the kernel is booting without errors.

---

### Post by Maheriano on 2013-05-06
Looks like it was actually much simpler than that, it appears to have installed Grub onto the flash drive instead of the RAID disk in the machine.....for some reason. I booted into a LiveUSB with 13.04 desktop on it and ran boot-repair as per this link: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Follow all the default options, reboot and you will now have Grub and a usable system.

Thanks to everyone for the last 2 days of fixes, allowing me to have a working production server for this morning.

---

### Post by MAFoElffen on 2013-05-06
Good deal!!!. Please go back to the first posts of both threads... Select "Advanced Edit". At that menu, select the "Prefix" and change both from "ubuntu" to "Solved"...

That helps us, to know the problem was resolved and that person has been helped. It also helps other users later on when they search were specific problems found a solution.

If you ever need it, I came up with a "Linux Diagnostics Flow Chart" that I published in my Graphics Resolution Sticky. The link for that thread is in my sig line. That flowchart is halfway through Post #1. Helps when diagnosing what's wrong and to rule things out. Goes through all the layers from the boot loader through a desktop (if installed). I specialize in Linux Graphics Layer Issues... But after over 25 years of Unix and Linux, I've just been exposed to a lot of things. If you go to post 2, you'll find some tutorials for server related "graphics issues" that you might be interested in also. I'm in the process of updating and replacing that sticky... And the new sticky will have my server minimal X install script and my server custom console pallets for "setvtrgb()".

Good luck.

---

### Post by Maheriano on 2013-05-06
Other thread doesn't show me the drop down box the way this one does.

---

### Post by Maheriano on 2013-05-21
Hello again. I've discovered a few very strange things about this box as I just had to go down to the client site because it once again wouldn't boot past the blinking cursor. Here's what I discovered:
1. Rebooting the machine via SSH or locally will always result in a clean boot. No problems.
2. Shutting the machine off either via SSH, locally or by pulling the power cord will result in it booting to the blinking cursor, no GRUB.
3. Attempting to cold boot with a keyboard and monitor plugged in will usually result in a clean boot, no problems. I don't know why, as soon as I plug in the peripherals, it will then boot fine.

How do I fix this?

---

### Post by Maheriano on 2013-06-25
I've come to realize this must be an issue with the Ubuntu 12.10 server edition hosted here. I've downloaded it onto 2 separate flash drives and installed it on 2 separate Acer A100 server boxes. Both of them have exactly the same problem, it will not boot without a keyboard plugged into it. Is there any way to fix this? I can't have my client leaving his keyboard next to a headless server.

---

