---
title: "Serious problems after latest updates 20111803"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by valem on 2011-03-19
Hello, I am very new to Linux, Ubuntu and this forum ...

I am running Ubuntu 10.10 and I have been keeping it updated via update manager.
Last night the update manager popped up and I selected to update all required updates without checking what the updates were.
While shutting down I noticed that I needed to reboot to complete the update, so I rebooted.
After reboot the wireless network card disappeared. So I moved the PC and plugged in the ethernet cable. Oddly sometimes it shows disconnected for no reason and I have to reboot.
What's even worst is that Ubuntu now locks up completely within 15 minutes of a reboot.
None of the alt+sysrq commands do anything!

How do I find out what the updates were and is there any way to I revert my system back to pre updates without having to reinstall ? Everything was running perfectly smooth!

Thanks!
Vale

---

### Post by mikewhatever on 2011-03-19
To find out what the updates were, open Synaptic Package Manager, click File->History. I think the kernel was updates, so you could try using an older kernel by holding the Shift key right after the BIOS screen, and selecting a different Ubuntu entry from the menu.

---

### Post by valem on 2011-03-19
In the Synaptic Package Manager, the latest History entry is for March 15. I am very sure that last night (March 18) the Update Manager opened up with items listed in it, and I clicked on "Install Updates" My time and date are correctly indicating today is March 19.
Also the "shut down - restart - logout etc." button was red instead of white (I didn't know why, now I know it was because of the reboot request)

Now I am going to reboot and will hold "Shift" ...

Here's the uname -a info:


vale@vale-desktop:~$ uname -a
Linux vale-desktop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

---

### Post by valem on 2011-03-19
All right, I rebooted, selected 2.6.35-27 and both wireless and wired internet worked again.
Rebooted again, this time I let it boot without interfering to 2.6.35-28 and like magic the wireless network card is "alive" again.
I have no idea what happened, but next time there are updates I am going to make note what is being installed.

Thanks.

---

### Post by mikewhatever on 2011-03-19
Odd indeed.:confused:

---

### Post by meirion on 2011-03-21
I had a similar issue.. (or at least equally odd)
I run Ubuntu 10.04. I just did an update. The following were installed / upgraded...

Commit Log for Mon Mar 21 18:55:03 2011

Upgraded the following packages:
libpam-smbpass (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
libsmbclient (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
libwbclient0 (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
linux-generic (2.6.32.29.35) to 2.6.32.30.36
linux-headers-generic (2.6.32.29.35) to 2.6.32.30.36
linux-image-generic (2.6.32.29.35) to 2.6.32.30.36
linux-libc-dev (2.6.32-29.58) to 2.6.32-30.59
samba (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
samba-common (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
samba-common-bin (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
smbclient (2:3.4.7~dfsg-1ubuntu3.4) to 2:3.4.7~dfsg-1ubuntu3.5
tzdata (2011c-0ubuntu0.10.04) to 2011d-0ubuntu0.10.04
tzdata-java (2011c-0ubuntu0.10.04) to 2011d-0ubuntu0.10.04

Installed the following packages:
linux-headers-2.6.32-30 (2.6.32-30.59)
linux-headers-2.6.32-30-generic (2.6.32-30.59)
linux-image-2.6.32-30-generic (2.6.32-30.59)

I lost my wireless keyboard and mouse, and my touch sensitive screen.  
I was using kernel 2.6.32-29 (I think) and was upgraded to 2.6.32-30. 
If i use 32-29 they all work OK if I use 32-30 they don't.

Does anyone have any ideas?

---

### Post by valem on 2011-03-21
> **meirion said:**
> I had a similar issue.. (or at least equally odd)
I run Ubuntu 10.04. I just did an update.

I lost my wireless keyboard and mouse, and my touch sensitive screen.  
I was using kernel 2.6.32-29 (I think) and was upgraded to 2.6.32-30. 
If i use 32-29 they all work OK if I use 32-30 they don't.

Does anyone have any ideas?

In my quest to figure out what's going on, I found out that some of the drivers have to be re-installed after updating to a new kernel.

/valem

---

