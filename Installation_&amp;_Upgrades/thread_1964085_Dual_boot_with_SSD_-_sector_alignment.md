---
title: "Dual boot with SSD - sector alignment"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by dudeeg on 2012-04-23
Hi!


I've just bought a 120GB SSD. I'd like to install both Ubuntu and Win7 on it.
I think if I put 70GB to win7 system and 50GB to Ubuntu, then it will be fine (data like video, pictures and such will be put into a normal HDD)



I've read on several forums that in case of SSD, the sector alignment is something that should be considered.

Could someone help me how to do this properly in case of this dual boot system?

Should I create the partitions for win7 and linux beforhand using a liveCD?
If so, the only thing that I should take care of that both the ntfs and ext4 partition start sector should be divisible by 8?



Second question:
If I install first the Ubuntu, and then later on the win7, then the win7 will overwrite somehow the boot section of the drive, so I should re-install the grub using a liveCD. Is that correct?


Thanks for your help!

---

### Post by darkod on 2012-04-23
If I am not mistaken, if you boot in live mode and use Gparted it will automatically start the first partition at sector 2048 which complies with the alignment requirements.

Also, if you prepare the ntfs partition in advance the win7 installer will not create the small system reserved partition and you save one primary partition.

To double check how Gparted created the partition you can check in terminal:
sudo fdisk -l (small L)

It will display the Start and End sectors.

Yes, the windows installation will overwrite grub2 on the MBR. You will need to reinstall it with the liveCD if you install (or repair) windows after ubuntu is installed.

---

