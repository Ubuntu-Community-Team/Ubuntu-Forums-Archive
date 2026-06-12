---
title: "Ubuntu ISO image checksum error"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by rschreiber on 2008-11-30
I am new to Ubuntu (SUSE refugee) and am working on my first install. I downloaded ubuntu-8.10-desktop-i386.iso (732,766,208 bytes) and burned it to a CD using NERO8 Burning ROM with validation turned on. All went just fine. 

When I use the "Check CD for defects" i get this error:



With the progress bar at about 60% I get...
[COLOR="Red"]
Checking integrity, this may take some time
Check finished: errors found in 1 files!
Press any key to reboot your system[/COLOR]



I re-downloaded the .iso from another mirror, burned another CD  and got the identical results.

Any idea what is wrong with the image? I would think that this is failing all over the place?

---

### Post by oilchangeguy on 2008-11-30
> **rschreiber said:**
> I am new to Ubuntu (SUSE refugee) and am working on my first install. I downloaded ubuntu-8.10-desktop-i386.iso (732,766,208 bytes) and burned it to a CD using NERO8 Burning ROM with validation turned on. All went just fine. 

When I use the "Check CD for defects" i get this error:



With the progress bar at about 60% I get...
[COLOR="Red"]
Checking integrity, this may take some time
Check finished: errors found in 1 files!
Press any key to reboot your system[/COLOR]



I re-downloaded the .iso from another mirror, burned another CD  and got the identical results.

Any idea what is wrong with the image? I would think that this is failing all over the place?

make sure you are downloading from ubuntu's website. and burn the iso as an image at the slowest possible speed.

---

### Post by gpsmikey on 2008-11-30
The fact you see the same thing from two different mirrors is suspicious.  You say Nero burned and verified the burn, so that should be OK.  Did you try the MD5 sum of the downloaded ISO?  If they match, then it almost sounds like the check on the CD is bad, not your download/burn.  Double check the MD5 on the ISO - it sounds like you are burning from windoze - there are a number of md5 sum utilities for windows.

mikey

---

### Post by zvacet on 2008-11-30
I hope that you still have iso image on your HD.I that case download same iso with torent and point download to the folder where your existing iso is.Torrent will  check your iso for corrupted files if any and replace them with good ones.After that check [md5sum and disc integrity.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by ctarwater on 2008-12-01
> **zvacet said:**
> I hope that you still have iso image on your HD.I that case download same iso with torent and point download to the folder where your existing iso is.Torrent will  check your iso for corrupted files if any and replace them with good ones.After that check [md5sum and disc integrity.]("https://help.ubuntu.com/community/BurningIsoHowto")

I've been having a similar problem and tried that, but every time I point my torrent program to it, I get the oddest behavior!  My torrent progam (ktorrent) shows the file is 98% complete and then downloads the rest.  When I recheck the data it says it's 99.9% complete and downloads the rest. But every time I check the data it says some is missing.  I've tried opening it in other torrent clients as well (transmission, deluge)

I've tried downloading from various mirrors on the Ubuntu site, I've tried downloading torrents, and tried the above mentioned mixture of the two.

(I'm running Ubuntu 8.10, fully updated)

---

### Post by nvance on 2008-12-01
One more thing, when you are burning the iso image to cd/dvd make sure that you are using the slowest burn speed and not letting the burn app choose the speed.  I have had numerous iso burns fail due to this issue.  It will of course take longer to burn but it might resolve your check sum issue.

---

### Post by ctarwater on 2008-12-01
I haven't even tried burning it yet because the checksum keeps failing.

I'm actually trying to get the damned thing on a USB stick to install intrepid on the wife's 701 eeepc.

I've now downloaded close to a dozen iso images including the alternate install, both from the official site, mirrors, and torrents, with no success.

I've downloaded it to both of my hard drives to make sure it wasn't an hdd issue, but it still happens.

None of my other torrents have had any issues so I don't think it's a ktorrent issue.

I had one successful checksum check and I was so shocked that I tried it a second time and it failed.  I'm watching the torrent programs closely and it seems like it gets to 99.90% and says the download is complete.

Oi, anyone have any ideas?

---

### Post by dabl on 2008-12-01
I recall reading a post similar to this a long time ago -- a person repeatedly getting a md5sum error.  I don't think a cause was ever determined, but he ended up using a different PC and getting a good ISO file.

You might want to change the method by which you are doing the download (browser, ftp/gftp, etc.), the OS you are running to do it, the PC your are doing it with, and/or the ISP whose service you are using to get it.  Eventually you'll get a download that will verify correct.

---

### Post by ctarwater on 2008-12-01
thanks, now I'm trying the following:

unetbootin
downloading from the official site on my nokia N800
xp / work computer

I'll post results later.

---

### Post by forkandles on 2008-12-01
Personally I would use K3b or Brasero for burning the ISO image to a good quality CD.
See if you can download the ISO on another Linux user's pc using d4x (Downloader for X) and Flashgot.
I used to have problems with interrupted/bad downloads in the past but I have never had a single problem since using the above combo.

d4x is available via Synaptic.

Flashgot is available via Firefox Add-ons (Firefox > Tools > Add-ons (Search for Flashgot).

PS I used to use SUSE many moons ago. Once you get over this small problem, Ubuntu will seem like a piece of cake in comparison. I still wake up screaming at night when I think of YaST!
Synaptic is just the BEST package manager available.
Good luck.

---

### Post by ctarwater on 2008-12-01
thanks for the suggestions guys!

using netbootin to download and write the image to usb failed as well.

downloading to my N800 seemed to work (it passed the checksum) but when I transferred a copy to my desktop, the image on the desktop didn't pass.  So I just created a USB boot disk from the image on the N800 and it's over 50% done.

So for now, using a different machine/OS seems to fix the problem if anyone else encounters it.

What an odd problem though.

I'll just chalk it up to my luck.

---

### Post by osjak on 2008-12-16
I've got the same problem trying to download and install the past two releases of Ubuntu. After burning several bad CD's I simply started chacking the downloaded images with winMd4Sum. I would get different sums every time I downloaded a new image, non of them would match the one [posted]("https://help.ubuntu.com/community/UbuntuHashes") on Ubuntu website. I think I went through about 20 images total being puzzled how this can be.

Then I had found this thread. I decided to change the computer and downloaded images with my two Linux servers - one Ubuntu webserver and one Debian local file server. Both gave me correct md5 hashes at the end. My Debian hard drives are shared across local network via Samba, so I copied the verified image to my Windows box and checked its md5 hash. It was different from the original! I copied it back to Debian server and md5 hash changed again! This is a weird problem.

---

### Post by ctarwater on 2008-12-16
The source of my problem turned out to be a bad stick of ram so I'd recommend running memtest.

---

### Post by pietjanjaap on 2008-12-16
> **osjak said:**
> I've got the same problem trying to download and install the past two releases of Ubuntu. After burning several bad CD's I simply started chacking the downloaded images with winMd4Sum. I would get different sums every time I downloaded a new image, non of them would match the one [posted]("https://help.ubuntu.com/community/UbuntuHashes") on Ubuntu website. I think I went through about 20 images total being puzzled how this can be.

Then I had found this thread. I decided to change the computer and downloaded images with my two Linux servers - one Ubuntu webserver and one Debian local file server. Both gave me correct md5 hashes at the end. My Debian hard drives are shared across local network via Samba, so I copied the verified image to my Windows box and checked its md5 hash. It was different from the original! I copied it back to Debian server and md5 hash changed again! This is a weird problem.

I had the same problem, wen I copied a file over the network, sometimes I had a damaged file, but not a error. The avi file was damaged, 2 years later i played the file, and it was stuck in the middle of the file.
In windows there was a problem, it was my firewall, installed a different one and it was ok again.

How to check your firewall:
Download a dvd movie from usenet, the copie the movie(with par files) 10 times over the network, then do a par check on the 10 movies, then you can check if your network is working.

---

### Post by osjak on 2008-12-16
> **ctarwater said:**
> The source of my problem turned out to be a bad stick of ram so I'd recommend running memtest.
Thank you for pointing this out. It turned out to be my problem as well. I hope now all my computer ghosts are gone.

---

