---
title: "Ubuntu gone, can't get into Windows"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by mailbox on 2006-06-21
Well, I installed Ubuntu 6.06 off a normal Desktop CD onto my primary slave drive. Previously, I had two seprate installs of Windows 2000 SP4, one on the primary master and the secondary master (a SATA drive). The secondary master install is hardly ever used, though.
After installing, I played around for a few hours, installed/updated/rebooted a few times, and everything was working fine. I decided to go onto my main Windows install to start to grab files and such to migrate over. I noticed that loading Windows and logging in (especially the "preparing network connections" and "applying security policy" bits) took an amazingly long time. After I'd been in Windows for about five minutes, a window popped up saying something to the effect of "Windows has prepared your new hardware for use" (this is one of those moments where your heart sinks).
Now, for some reason, when my computer boots, grub pops up with choices for two Ubuntu installs (two 'normal boot's and two 'recovery mode', or whatever they're called). This is strange, considering I only had one install, and all four of these get me nowhere. I can still (technically) get Windows to load, although It never lets me login; It goes through the "preparing network connections" and "applying security policy", but then the login window never appears.

I booted from my Windows install CD and tried fixmbr in the recovery console, but that didn't help me at all. I tried a repair of the Windows install, but that did no good either.
I'm looking to just get Windows working again so I can get all my data off it before I try another install of Ubuntu. Any help would be appreciated.

---

### Post by rowanparker on 2006-06-21
Do you have important files you need?
If so, use a Live CD to back up those and then reinstall.
If not, reinstall.

Unless you can elaborate more on what happens when you choose any of the 4 Ubuntu's in Gurb.

Rowan.

P.S. > Now, for some reason, when my computer boots, grub pops up with choices for two Ubuntu installs (two 'normal boot's and two 'recovery mode', or whatever they're called). This is strange, considering I only had one install, and all four of these get me nowhere. You have two because you have a newer kernal than the orginal one, this is completely normal.

---

### Post by bodhi.zazen on 2006-06-22
Please post the contents of your /boot/menu.1st file (from Ubutnu).

Your first step should be to backup any data from the Windows partiton. As has been suggested, use a Live CD (Ubuntu or otherwise).

Second re-format the Ubuntu partiton as a FAT or NTFS -> re-try Windows

If that fails, make a grub boot floppy disk:

[http://www.linux-sxs.org/administration/grubflop.html](http://www.linux-sxs.org/administration/grubflop.html)

Boot to the Floppy.

At the Boot prompt follow the GRUB format to boot Windows:

root=(hdx,y)
makeactive
chainloader +1
boot

If windows does not boot at that point you are beyond my help and may need to re-install Windows (which may or may not wipe all your data).

Good luck

---

