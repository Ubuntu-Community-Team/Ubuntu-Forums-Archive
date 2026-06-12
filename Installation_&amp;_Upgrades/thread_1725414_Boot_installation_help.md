---
title: "Boot installation help?"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by Corp.Samich on 2011-04-09
Hey all.

I have a Nvidia Gfx card, started using Nomodeset, Didn't work, Tried it with Noapic, and it worked. 

Now here's two questions:
1: Will noapic affect my install, and will I have to continually use it?

2: at my install screen, when I'm told to enter my name, Do so, fill all fields, and my install bar says Ready when you are, I can't continue. (Box is greyed out) Help with a fix?

Edit: 2 is fixed.

---

### Post by dabl on 2011-04-09
If the "noapic" boot option is needed to show the display correctly, then it will not cause any problem on your installed system.  However, once you install the OS, if you choose to also install the proprietary Nvidia driver, you might find that you no longer need the noapic boot option.

---

### Post by Corp.Samich on 2011-04-09
Alright, Install completed, booted from Hdd, and now all I get is a code and stuff saying 'Gave up waiting for root device. Common problems: boot arbs
Check rootdelay
Check root
Missing modules

ALERTA /Dev/disk/by-uuid/36450524-a0e6-4438-a83f-c90b9ae57167 does not exist. Dropping to a shell!

Busybox v1.153.3 (Ubuntu 1:1.15.3-1) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) _'


Can't enter anything on this screen. Help from here all?

---

### Post by Quackers on 2011-04-09
What happens if you type EXIT and press enter?

---

