---
title: "No Network Devices After Ubuntu 9.10 Upgrade"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by larynx on 2009-11-26
I'm running Ubuntu 9.10 32-bit on a Toshiba Satellite M305-S4910 Laptop and the network devices are as follows (output from running lspci):
Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
Network controller: Intel Corporation Wireless WiFi Link 5100

After upgrading from 9.04 to 9.10 (that came with kernel 2.6.31-14) I suddenly can't use my network devices, when clicking on the Network Manager icon it says "No Network Devices Available" and when running the command "lshw -C network" it states that the devices are UNCLAIMED.

I searched and found a few suggestions, I tried booting up with the acpi=off parameter but that didn't work. I also tried upgrading to kernel 2.6.31-15 but no luck.

The only (temporary) solution I have found is booting up kernel 2.6.31-12 which solves the problem.

I definitely seems like a kernel issue but I don't see any solution to it, has anyone had any luck with it?

---

### Post by /usr/bin/hacked? on 2009-11-27
BUMP

I have the same problem with a new install.

---

### Post by Ciurica on 2009-12-02
I have the same issue on Toshiba U400-15N, no wired and wireless network. On 8.04 all worked just fine.
Kernel image 2.6.31-12 is on 9.10 CD or how can I install it on an no network system.

---

### Post by crash123 on 2009-12-02
I had a very similar problem with the toshiba m305-s4910. This is a bit of a story, but maybe it will be helpful somehow. I dunno. 

I was running a dual boot of x64 Vista and Ubuntu 9.04. Internet worked sporadically on ubuntu for about a day after installation. Then I installed updates (still for 9.04) and then both of my wireless cards stopped working. Only an ethernet connection would work. I posted on the forums about it like a month ago, got a suggestion or two, but nothing panned out. I even tried to boot in the earlier kernel before the updates, but with no luck. It said my network cards were UNCLAIMED, though they hadn't been before. Searching like crazy for solutions online, I saw lots of recommendations to try madwifi or ndswrapper, but I found little usable explanation of how to use either to fix my wireless cards. 

I then installed 9.10, hoping maybe my wireless would work there. Same problem. I had been planning on doing a fresh install of Vista anyways, so I then wiped my harddrive clean and reinstalled Vista.

Then I reinstalled 9.04 (for some reason), and still had no luck with the internet. Gave up, then last week, I booted into ubuntu again out of boredom, and all of sudden my wireless worked! I didn't do a single thing when I booted this time to try to get it to work; ubuntu recognized and used both network cards I have as if there had never been a problem in the first place. And it has worked ever since, both my Intel 5100 (the factory card) and my expresscard adapter, a belkin n1. I have no idea what the explanation is for this. 

Either way, I think this is an issue deserving more attention on the ubuntu site. Especially for newbies; I still am one.

Depending on your needs with ubuntu, I should also note I've also had no problems getting wireless to work when running ubuntu through Virtualbox. The emulator tells ubuntu you're using a compatible ethernet connection, so it works just fine :). This is what I've been using to run ubuntu lately.

---

### Post by larynx on 2009-12-05
Bump/Update...

Just updated to 2.6.31-16 and the problem is still present.

Does anyone know of a working solution?

---

### Post by /usr/bin/hacked? on 2009-12-06
I just used the ubuntu 9.04 and it worked just fine. I think I'll just skip the upgrade and go straight to 10.4. maybe that'll work.

---

### Post by odinb on 2009-12-10
Just updated to 2.6.31-16 today, and my LAN stopped working. Booted back into 2.6.31-15 and LAN is back.

Anyone know what happened, and if a fix for this is on its way?

My machine is the HP NW8440 (unfortunately with the crappy ATI card with no support from ATI/AMD anymore).

lspci gives:
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
and lspci -n
08:00.0 0200: 14e4:16fd (rev 21)

//Odin

Update:

Nevermind, after rebooting into 2.6.31-16 again, LAN is back.

Is this flaky or what? Hope it keeps working.....

---

### Post by ademey on 2009-12-19
Hi, 

I'm having a somewhat similar problem. 

My dell vostro 1000 laptop is set-up as dual-boot ubuntu 9.10 and windows vista. After logging in into windows and then starting in Ubuntu, often but not always, a command-line login is prompted and graphical start-up process only continues after 60 seconds. Then, when start-up is complete, LAN is broken.

After reboot, all is ok again...

---

### Post by larynx on 2010-01-12
Update...

Just updated to 2.6.31-17-generic-pae and the problem has been solved!

---

