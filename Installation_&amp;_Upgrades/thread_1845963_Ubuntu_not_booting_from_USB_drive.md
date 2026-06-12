---
title: "Ubuntu not booting from USB drive"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by CosmicVoyager on 2011-09-18
Please ignore this thread. The Ubuntu installer does not even see the USB 3.0 drive.

New thread:

[http://ubuntuforums.org/showthread.php?t=1846060](http://ubuntuforums.org/showthread.php?t=1846060)


Greetings,

I installed Ubuntu 11.04 onto a USB drive, and restarted, but it does not boot.

I have USB HDD selected in BIOS.

What could be wrong?

Thanks

---

### Post by Rubi1200 on 2011-09-18
Hi and welcome to the forums :)

What exactly happens when you reboot? Error messages, a blank screen, hard-drive spins down?

How did you install the image on the USB stick? Which program did you use?

Also post the full specifications for the computer especially RAM and graphics card.

---

### Post by CosmicVoyager on 2011-09-18
"What exactly happens when you reboot? Error messages, a blank screen, hard-drive spins down?"

When I reboot it says "Loading Operating System..." for about a minute. There is no indication of drive activity on the drive's light.

Then it says "DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER"


"How did you install the image on the USB stick? Which program did you use?"

I installed to a USB hard disk drive from an Ubuntu 11.04 CD.


"Also post the full specifications for the computer especially RAM and graphics card."

Motherboard: Gigabyte P61-USB3-B3
CPU: Intel Celeron G530 2.4GHz
RAM: 4GB module
Graphics Card:MSI NVIDIA GeForce 8400 512MB
Hard disk drive: Western Digital My Book Essential USB 3.0

---

### Post by CosmicVoyager on 2011-09-18
I plugged the drive into a USB 2.0 port and it worked.

I plugged in back in the USB 3.0 port and I get something called GRUB.

Help.

---

### Post by CosmicVoyager on 2011-09-18
I swicthed back to USB 2.0 port and now that isn;t working either. It loads GRUB.

How is that possible? It was working. Nothing changed.

Anyone?

---

### Post by oldfred on 2011-09-18
i have seen issues with USB3 ports, not sure if it is BIOS, grub2 or both.

Plug into the USB2 port and run this from a liveCD/USB.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Or you can run this which will download script and can make some repairs.
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)

---

### Post by CosmicVoyager on 2011-09-18
Well, I have found that I can't install Ubuntu if the drive is in the USB port. It does not show up in the installer.

Started a new thread to focus on getting the installer to work.

[http://ubuntuforums.org/showthread.php?t=1846060](http://ubuntuforums.org/showthread.php?t=1846060)


"Plug into the USB2 port and run this from a liveCD/USB."

I'm guessing that will not help it install on the USB 3.0 port if isn't an option in the installer? I can't even install it.

---

### Post by CosmicVoyager on 2011-09-18
> **oldfred said:**
> i have seen issues with USB3 ports, not sure if it is BIOS, grub2 or both.

Plug into the USB2 port and run this from a liveCD/USB.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Or you can run this which will download script and can make some repairs.
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)


I find that all overwhelmingly complicated :-(

---

