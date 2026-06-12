---
title: "Server 6.06.2 installation halts after hostname"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by Dok666 on 2008-04-07
Hello all

I'm trying to install Ubuntu 6.06.2 from CD but the installation halts without errors after I type in the hostname. Uptil then everything is fine

I have
[LIST]
[*]verified that the CD is correct
[*]checked my memory
[*]removed all unessesary hardware
[*]reset BIOS to defaults
[*]tried the LAMB install instead
[*]verified the CD on another computer
[/LIST]but nothing changes

The computer contains
[LIST]
[*]Athlon XP @ 1100MHz
[*]Asus A7N8X-X motherboard
[*]512 MB DDR512 PC3200 Matrix RAM
[*]GeForce FX 5500
[/LIST]
The hard drive already contains Windows XP but I would like to overwrite this and I'm guessing the installation will provide such an option later on.

I can boot the computer into Windows XP and verify using various system tools that alll hardware is working fine.

I do not have the option of installing any other version of Ubuntu as this is the version my host provider is using after they upgraded from Debian - but so far this seems like a downgrade :(

I need a local instance of the same OS for testing before deplyoing to a live enviroment.

I have searched the web and these forums but can't find any similar post...and if I can then noone is answering them.

Any help is appreciated.

---

### Post by Dok666 on 2008-04-07
I just tried installing the same CD on an old laptop. Same problem. The laptop can boot into Debian without problems.

---

### Post by Dok666 on 2008-04-07
Reburned the image to a new CD but still not working.

---

### Post by Dok666 on 2008-04-07
Problem solved by disconnecting network cable and manually configuring network after install. It is really stupid that Ubuntu doesn't timeout when scanning the mirror nor when searching for a default proxy...

---

