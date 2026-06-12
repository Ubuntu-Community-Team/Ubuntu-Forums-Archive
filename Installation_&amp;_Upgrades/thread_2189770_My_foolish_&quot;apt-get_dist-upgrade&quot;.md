---
title: "My foolish &quot;apt-get dist-upgrade&quot;"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by tcarney57 on 2013-11-23
Instead of just installing security updates, I foolishly did a "dist-upgrade" on my HP Pavillion dv6000 with Kubuntu 12.04 ("lsb_release -a" currently shows "Ubuntu 12.04.3 LTS") installed and running fine. Now it *mostly* runs fine, except I cannot get it to read (show up in Dolphin):
 
--usb drives ("thumb," "stick," etc.)
--the built-in SD card slot
--a usb plug-in card reader
--CD data disk
--camera-to-usb connection

It *will* print through a usb printer. It will also run the usual programs, access the web (wifi), etc.

"/dev/scsi/" is empty and "/dev/usb/" has one file of 0 (zero) bytes titled, "hiddev0," which was updated it seems a few minutes ago--about the time I last tried to connect a usb device.

The "/mnt/thumb/" and "/mnt/usb/" directories are empty.

"Settings--Removable Devices" shows "automatic mounting" enabled (box is checked), the "only mount . . . been mounted before" is *un*checked, but both "mount all at login" and "automatically mount . . . when attached" are checked (enabled). Everything in the "Device Overrides" list is checked for both "automount on login" and "automount on attach." It lists many but not all of the devices I've plugged in before.

Not surprisingly, the pop-up that asks what to do when a device is plugged in doesn't pop-up anymore. 

I have looked at dozens of postings on related problems, but I'm not finding anything that's worked so far. What do you all think I should do now?

Thanks!! --Todd

---

### Post by ian-weisser on 2013-11-24
Look at the bottom of /var/log/dmesg (the kernel log).
Plug something in that isn't working.
Close and reopen /var/log/dmesg . See the changes at the bottom? New entries.

Post all those new entries here. NOT the whole file. Just the new entries after you plug something in.

Did the update complete? Were there any update error messages?

---

### Post by tcarney57 on 2013-11-24
Ian,

Thanks for such a quick reply!

I do not remember any error messages when the update completed. Is there a way of getting at a log of that bash session?

Anyway, here are the log entries you suggested:

11/23/13 09:06:33 PM	usb 2-1	new high-speed USB device number 13 using ehci_hcd
11/23/13 09:06:34 PM	scsi14 	usb-storage 2-1:1.0
11/23/13 09:06:35 PM	scsi 14	:0:0: Direct-Access HP v100w 4096 PQ: 0 ANSI: 0 CCS
11/23/13 09:06:35 PM	sd 14	:0:0: Attached scsi generic sg2 type 0
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] Write Protect is off
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] Mode Sense: 43 00 00 00
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] No Caching mode page present
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] Assuming drive cache: write through
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] No Caching mode page present
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] Assuming drive cache: write through
11/23/13 09:06:35 PM	 sdb	sdb1 sdb2 < sdb5 sdb6 >
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] No Caching mode page present
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] Assuming drive cache: write through
11/23/13 09:06:35 PM	sd 14	:0:0: [sdb] Attached SCSI removable disk

These are all the lines since plugging in a thumb drive. Even I can tell it doesn't like something. What do you think?

Many thanks!!!  --Todd

---

### Post by Bucky Ball on 2013-11-24
First off, run 'sudo apt-get update' (this should ALWAYS be run before a 'sudo apt-get upgrade' command of ANY kind). Then run the regular 'sudo apt-get upgrade', NOT the dist-upgrade command. Reboot and see if this helps.

---

### Post by tcarney57 on 2013-11-24
Thanks, Bucky Ball!!

I did run the update before the dist-upgrade, but now I'll try your suggestion to run "update" then "upgrade" then reboot. I'll let you know.

Thanks!! --Todd

---

### Post by tcarney57 on 2013-11-24
Hi, Bucky Ball!

I reran "apt-get update" and "apt-get upgrade" and then rebooted. Unfortunately nothing has changed regarding my usb-device problem. I have two plugged in at the moment: an SD card in the built-in slot, and a 4GB thumb drive. Both seem to show up as links in "/dev/disk/by-label/" but they don't show up elsewhere. Bummer! --Todd

---

### Post by oldos2er on 2013-11-24
Which version of KDE are you using?

Try checking System Settings > Startup & Shutdown > Service Manager, is "Removable Device Automounter" enabled?

---

### Post by tcarney57 on 2013-11-24
InfoCenter says my KDE is 4.11.3. Automounting is enabled.  Thanks!!! ---Todd

---

### Post by oldos2er on 2013-11-24
Welcome. Would you please mark the thread as 'Solved' (under Thread Tools)? Thanks.

---

### Post by tcarney57 on 2013-11-24
Ann,

Actually, my problem is not yet solved. When I indicated in my last message that automounting is enabled, that's just what is shown in the Service Manager. It shows that it's enabled, but automounting is not actually taking place. It's still busticated.

You also asked about the KDE version. It's [COLOR=#000000]4.11.3. Any ideas? A few messages ago, I posted some lines from the kernel log that ian suggested. I'm hoping that might shed some light on this goofiness.

Thanks! ---Todd[/COLOR]

---

### Post by ian-weisser on 2013-11-24
The dmesg log shows that automounting seems to be taking place, but the fact is not reflected in your Desktop Environment.
I don't use KDE, so I *think* that 'kio' should be the culprit failing to show the automount on KDE...but debugging that is beyond my expertise.
I hope another community member with KDE experience can help.

---

### Post by oldos2er on 2013-11-25
> **tcarney57 said:**
> You also asked about the KDE version. It's [COLOR=#000000]4.11.3. Any ideas? A few messages ago, I posted some lines from the kernel log that ian suggested. I'm hoping that might shed some light on this goofiness.

Thanks! ---Todd[/COLOR]

I'm afraid I don't have any further suggestions, except to say if you don't find a solution here, try kubuntuforums.net.

---

