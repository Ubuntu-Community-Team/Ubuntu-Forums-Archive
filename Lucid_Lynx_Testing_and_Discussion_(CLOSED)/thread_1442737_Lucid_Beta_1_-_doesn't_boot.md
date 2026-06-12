---
title: "Lucid Beta 1 - doesn't boot"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by reuben on 2010-03-30
I upgraded using update manager from 9.10 on my spare desktop, to see if Lucid worked.

Unfortunately it doesn't - it freezes at boot.

I've tried all three kernels available, and they all freeze at the same point - after my disks are initialized (I presume from the console after udev has done its thing) during init-bottom. The last lines I see are:

sd 8:0:0:[0-4] [sdN] Attached SCSI removable disk

I've tried with noapic and noacpi in various combinations, but that doesn't help.

Any ideas on how to debug this from a livecd, and/or other grub options to try? I'll file a bug report once I get to the bottom of this.

---

### Post by Mark Phelps on 2010-03-30
Lucid is still in Beta, so you should post your beta-related questions to the correct forum: Development & Programming, Lucid Lynx testing.

I'm asking the Mods to move this thread to that forum.  Look for responses there.

---

### Post by mpbb77 on 2010-03-30
Well seems I m unlucky, apparently this bug is arising only on the last hours, just before my upgrade,  as there is no trace before.

Yes my machine is also seriously broken as I can t pass past initi bottom. I m already downloading the live cd in hope it can be fixed via chroot ...

BTW the only special thing I can say about my computer is that it has VT RAID controller and AFAIK the RAID mode is on even if there is only one hard drive. This setting cannot be changed on BIOS (Amilo FSC laptop computer). 

In the past this prevented me from being able to install opensolaris as it wouldnt recognize my drive as there was no driver for the raid controller, but I guess this is adifferent issue, I hope.

---

### Post by mpbb77 on 2010-03-30
> **reuben said:**
> I upgraded using update manager from 9.10 on my spare desktop, to see if Lucid worked.

Unfortunately it doesn't - it freezes at boot.

I've tried all three kernels available, and they all freeze at the same point - after my disks are initialized (I presume from the console after udev has done its thing) during init-bottom. The last lines I see are:

sd 8:0:0:[0-4] [sdN] Attached SCSI removable disk

I've tried with noapic and noacpi in various combinations, but that doesn't help.

Any ideas on how to debug this from a livecd, and/or other grub options to try? I'll file a bug report once I get to the bottom of this.


Also forgot to say its also SCSI connected hard drive

---

### Post by reuben on 2010-03-30
Mine is also SATA. I do have a RAID card which one of the drives is connected to. However I tried booting without the RAID card in the slot, and same deal, unfortunately. Please let me know if you figure out a workaround...I'll do likewise.

---

### Post by cph05a on 2010-03-30
I have this same problem. I did a clean install on a macbook pro 5, 5. It worked for a little while, but now it doesn't boot at all.

---

### Post by reuben on 2010-03-30
I filed a bug. [https://bugs.launchpad.net/ubuntu/+bug/552088](https://bugs.launchpad.net/ubuntu/+bug/552088)

I've been googling for hours and have found no fix.

---

### Post by garvinrick4 on 2010-03-30
See if removing plymouth for now helps.

---

### Post by VMC on 2010-03-30
Not knowing what drivers are involved (ati,nvidia,etc), you could try adding *nomodeset* to the linux line from grub boot menu. Remove *quiet* also to see other messages.

If that doesn't work try adding *single* and *--verbose* to the linux stanza. With verbose turned on you can then examine *syslog* for any telltail signs. *single* should get you to recovery mode. If it freezes then boot using livecd and examine the *syslog* of that partition.

---

### Post by mpbb77 on 2010-03-30
> **VMC said:**
> Not knowing what drivers are involved (ati,nvidia,etc), you could try adding *nomodeset* to the linux line from grub boot menu. Remove *quiet* also to see other messages.

If that doesn't work try adding *single* and *--verbose* to the linux stanza. With verbose turned on you can then examine *syslog* for any telltail signs. *single* should get you to recovery mode. If it freezes then boot using livecd and examine the *syslog* of that partition.


I ll try but it seems the problem is not on video mode rather on udev.

Seems either on usb ( i ve got error on  usb device if i plug a usb mouse) or raid ( when i hit ctrl alt del it mentions md devices).  .

---

### Post by zacbarton on 2010-03-31
Beta 1 didnt boot for me either due to my nvidia card not working with nouveau. I got it booting by adding "nomodeset xforcevesa" to the boot command.

---

### Post by azurehi on 2010-03-31
After upgrading from 9.10 and reaching the linux 2.6.32-18 kernel, I can no longer reach the desktop.  The login screen appears with my username and mouse cursor can be moved.  Upon hitting Enter, the screen for password appears but mouse cursor is frozen and nothing can be typed in to password box.  Within a few seconds there is reboot, with the same process repeated.  There is no way to get to the desktop.  This is true for each of the previous kernels.

Using recovery mode, allows entry of username and password at dos prompts but I do not know what to enter at the ~$ prompt.

Any suggestions appreciated.

---

### Post by reuben on 2010-03-31
Removing plymouth gets it a lot further. Now it's complaining about /proc/bus/usb not existing.

---

### Post by reuben on 2010-03-31
azurehi - you should probably post a new thread. 
It sounds a lot like your video driver isn't working.

---

### Post by reuben on 2010-03-31
My USB issue in fact went away. Hopefully it doesn't return. Now, it fully boots. Plymouth is indeed the issue, so the bug has been changed to reflect that.

By the way, for those who have the same problem, you don't need a live cd to fix this. In the grub menu, edit the "recovery" kernel line to say, instead of "ro single", "rw init=/bin/bash", and then boot. This will dump you into a bash shell. Type dhclient to bring up a net connection (in case apt-get needs it), and then do apt-get purge plymouth.

---

### Post by azurehi on 2010-03-31
I started a new thread:  lucid cannot login after upgrade from 9.10

---

