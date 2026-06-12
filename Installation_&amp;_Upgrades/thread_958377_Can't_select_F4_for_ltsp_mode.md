---
title: "Can't select F4 for ltsp mode"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by Mip5 on 2008-10-25
Hey Gang,

I've searched around but haven't been able to find this anywhere. I'm trying to install ltsp 8.04 for a school on a dual xeon board with 4 gb of memory and scsi disks. If all goes well, I'll deploy similar setups across other schools in the district. I'm *really* excited about this.

When I boot from the CD, I'm presented with my language choice, but then can't select F4 to select the ltsp mode (the option "Normal" appears, but cursor keys don't change that - I can't see other options, and hence can't select them). All of the other F keys work (options are presented, and the cursor keys allow me to select them). The server doesn't have a cdrom player, so I grabbed one from an old machine, and plugged it into the IDE port on the board. I also tried using a usb dvdburner, and got the same results.

I've tried installing it without selecting that option, but have seen a few things in the logs that appear problematic (nbd can't parse config, dhcp-server3 fail, etc), so I'd rather get the install working using F4 than running around afterward and fixing the other stuff that didn't happen automagically - though I'll do that if I have to.

Any ideas as to why I can't press F4 on installation? I noticed that it failed as an option on both a 8.04.1 alternate CD, and 8.04 alternate CD. Is there anyway to get that install (and various config scripts that accompany that selection) via some other install option? I tried going through the expert install, but didn't see it.

Thanks a bunch in advance. I've been at this step for a week, but haven't been able to find anything in google.

M

---

### Post by Mip5 on 2008-10-29
Has no one else had this problem?

I've reburned the CD just in case something went awry, and even redownloaded it and burned that. Still, I get this error. FWIW, I get this error on different machines (3 of them).

Does anyone know of a way to select the F4 option during the install some other way (that is, by passing parameters after selecting another boot option)?

Is there a more appropriate place to post this question?

Thanks,

M

---

### Post by Mip5 on 2008-10-30
Got the word from a nice fellow on IRC edubuntu that I had used the wrong iso. I *thought* I needed the ubuntu-server iso since I was building an ltsp server. The alternate cd is the one that's needed. I just downloaded it, and booted a virtual machine from it, and indeed, F4 affords an ltsp option. 

Hopefully this will help someone else out there.

peace,

M

---

### Post by cariboo on 2008-10-30
The server cd gives you the choice later on in the installation with a screen where you can choose from different server options.

Jim

---

### Post by Mip5 on 2008-10-30
> **cariboo907 said:**
> The server cd gives you the choice later on in the installation with a screen where you can choose from different server options.

Jim

I looked for the ltsp option, and did not see it. I don't think it's there (at least not in the same form as are the options for dns server, file server, etc).

M

---

