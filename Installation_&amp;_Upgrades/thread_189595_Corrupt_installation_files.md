---
title: "Corrupt installation files"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by ejl on 2006-06-05
Trying to do a clean install of 6.06 on a Averatec 6100 series laptop. Downloaded the alternate image file, verified the checksum, and burned the image to disc using CD Recording wizard. System reboots to the splash screen ok and all seems ok until it starts to download lib files at which point I get a warning that libxxxxxxxxxxxx.deb was corrupt. If I continue I'm told that it couldn't download package libxxxxxxxxxxx. This action continues until the install seems to hang (at 6%). Previous releases of Ubuntu installed without problem.
I have downloaded the current image four times, verified it four times and burned it four times. Each time the installation proceeds to the same point and hangs. Any thoughts?

---

### Post by TeeAhr1 on 2006-06-05
This may be completely unrelated, but it's something you can try.  (This is gonna sound just dumb as hell, bear with me)

Turn off the screensaver on the Live CD before you begin installation.  The screensaver turns on during install, which moves some data on the disc, which will hang the whole works.

My apologies if you've already read the sticky and tried this, but if not, it's worth a shot.

---

### Post by stevekl on 2006-06-05
I have the same problem.

I downloaded the alternative install iso, burned it, etc, and I get corrupt packages.

It seems to be a problem with the alternative install. Rather than downloading it again, I am going to just install with the breezy install CD and dist-upgrade from there.

---

### Post by nacnud on 2006-06-06
[QUOTE=ejl]Trying to do a clean install of 6.06 on a Averatec 6100 series laptop. Downloaded the alternate image file, verified the checksum, and burned the image to disc using CD Recording wizard. System reboots to the splash screen ok and all seems ok until it starts to download lib files at which point I get a warning that libxxxxxxxxxxxx.deb was corrupt. If I continue I'm told that it couldn't download package libxxxxxxxxxxx. This action continues until the install seems to hang (at 6%). Previous releases of Ubuntu installed without problem.
I have downloaded the current image four times, verified it four times and burned it four times. Each time the installation proceeds to the same point and hangs. Any thoughts?[/QUOTE]

I've been having the same problem with a Dell Inspiron 600M.  I've tried numerous times with different cd's and different images.  Each time it tells me some other package is corrupt.

I'm using the alternate cd because I have existing NTFS and FAT32 partitions.  Worked fine with Breezy.

---

### Post by howzat on 2006-06-08
I have the same problem with both the ubuntu-6.06-alternate-i386.iso and the xubuntu-6.06-alternate-i386.iso. 
Md5's match and I have burnt the cd's at various speeds with the same result. At 6% ubuntu has 5 or 6 corrupt packages and xubuntu has 2 or 3. 
Breezy installs no problem ](*,)

I'm installing on a HP e-vectra 128mb ram

---

### Post by jkahan on 2006-06-10
I am having the same at about 96%, md5 is good and I have run media check which verifies the cd is OK. It is complaining about package.gz being corrupt even when it is pulling off of the net.

---

### Post by coolguy2k on 2006-06-12
Same problem (6% thinger), reburned twice, downloaded and burned another time same problem.

However, when i went into VMWare and mounted the ubuntu image in my windows and installed under VMWare it worked flawlessly, after the physical cd's also didn't work in VMWare, same same as the real install.

to recap: install stops at 6% under three different disks and two different downloads of the alternative i386 disk - same problem with the install in VMWare, then i tried to mount the image and boot from the image - perfecto!, still the same problem later though when i try and do the real install.  

what the deal

---

### Post by coolguy2k on 2006-06-13
update:  so i did the check disk for errors and keep on coming up with (something along the lines of): md5 error or cdrom error.

why the f$$$ can't i burn this right?  Am i burning it wrong - i burnt the first three through the image burning wizard in alcohol then tried the last one in nero image burner thinger 

can anybody just tell me i'm f$$$ing retarded and don't know how to burn this image thus not install dapper? or is my image bad (although i tried two different downloads, one from bittorrent one not)?  

a little help pretty please

---

### Post by ejl on 2006-06-13
Finally got an install. Downloaded, verified and burned the Live CD. Tried to install from there. It would start and then hang. Tried a number of times and each time it went a little further until finally it installed completely. Did an update, modified my display drivers and the network interfaces file (to get my wireless running) and all seems well. I still have no idea why I could not install from the alternate image download.

---

