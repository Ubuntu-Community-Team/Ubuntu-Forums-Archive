---
title: "Installing from USB Thumb Drive"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by B4L1STA on 2006-09-29
Here's my situation:  I want to install Ubuntu from my USB thumb drive instead of a CD.  I don't have a CD burner or a machine with linux already on it to use.  

My machine has an AMD 64 3700+ (San Diego) motherboard with a DFI LanParty SLi-D motherboard (nf4 chipset) and a Seagate 7200.9 harddrive, currently with two partitions (one NTFS for windows and one fat32 that I made to store the ISO for the Ubuntu install with about 50 gigs left unpartitioned)

I started by downloading the boot.img.gz file from:

ubuntu/dists/dapper/main/installer-amd64/current/images/hd-media/

then extracting the .img file and using WinImage to write it to my USB drive (Corsair Flash Voyager 1gb).  When I boot, the system just says "boot error" and doesn't work.  

Next I repeated the same process, this time with the image found in the Breezy folder. It worked (i can get into the installer) except that it can't seem to access the ISO on my fat32 partition.  If I install from expert mode, it says "ubuntu-6.06-desktop-amd64.iso was successfully mounted" but then it tells me to check the CD.  

Anyone have any ideas?  Why won't the dapper image work (i've repeated the same process about 4 times now and it just won't work with dapper) and why can't it read the ISO even after it says it's been successfully mounted?

---

