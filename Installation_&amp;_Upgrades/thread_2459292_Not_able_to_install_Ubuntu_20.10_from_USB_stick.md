---
title: "Not able to install Ubuntu 20.10 from USB stick"
date: 2021-03-15
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2021-03-15
I've been doing USB stick installs of Ubuntu for over ten years now, and although there have been problems, I've never been stuck like this!

I downloaded the 64-bit ISO from distrowatch link, Ubuntu download mirrors, and saved it.

Then I create an install USB stick -- four times!  Twice, I used the startup disk creator in Linux Mint 19.1.  Twice, I did it here in Ubuntu 20.04: once using the Startup Disk Creator app (usb-creator-gtk) and once using the mkusb app.

All four times, I got the same result:
1) select usb stick from boot devices menu
2) screen goes black and the word "GRUB" appears
3) screen clears and GRUB menu appears with selections list
4) Choose the top selection  -- Ubuntu
5) Screen clears, get black screen with flashing cursor -- NOTHING ELSE
6) Screen stays this way until I get fed up and reboot -- have waited ten minutes and seen no disk activity and nothing on the screen
7) Reboot from USB stick
8) When GRUB menu appears, choose the second "safe graphics" selection
9) Same result -- flashing cursor, nothing else

Since I guessed the original ISO download was corrupted, I downloaded it again and went through all of this a second time -- same results

I really do NOT want to do an in-place upgrade because I did a lot of recent experimenting on 20.04 and it is generally a mess.  So, I wanted to start out clean with 20.10.

If I have to, though, I made an image backup using Clonezilla after I first installed 20.04, so I could restore to that and then do an in-place upgrade.

Or, I could do a reinstall of 20.04 and do an in-place upgrade from that -- as I booted from that USB stick and confirmed it works OK.

But ... all things considered .. I would rather do a clean install of 20.10.

I have done clean installs of Windows using ISO files that I mounted from inside Windows, but I don't know how to do the same in Ubuntu as the USB stick method has always worked in the past.

I'm looking for a way to install 20.10 without having to jump through all the hoops of reinstallig 20.04 and doing an in-place upgrade.

thanks in advance for any assistance

UPDATE: Sorry, but I've been away from this for a long time and only NOW remembered that by adding a stanza to the 40_custom file, I can boot the ISO directly instead of having to read a USB stick or disk.  So, I have done that and can now get into Ubuntu 20.10 and will install it when I have some time.

UPDATE2: That did not go well.  I booted into the ISO, started the installer, got all the way to Something Else, completed the entry to reformat the Ubuntu partition, chose the Linux drive for boot but then, I got messages about being unable to mount filesystems. and the installer hung on "detecting filesystems" until I shut it down.  The ISO is in a data partition on the Linux physical drive, but that partition itself is not mounted in Ubuntu.  

UPDATE 3: Installed from 20.10 DVD.  Installer said it failed due to being unable to find an ESP partition on the drive -- which is correct, given that the drive is formatted MBR.  But rebooting did confirm that 20.10 got installed.

---

