---
title: "Problems installing Ubuntu on ASUS n71 laptop"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by Inoki on 2013-05-03
Hi guys,

a friend of mine has issues installing **Ubuntu 13.04 x64** on an **[ASUS n71 laptop]("http://www.asus.com/Notebooks_Ultrabooks/N71Jq/#specifications") **(click link for specs). He gets the error message "Boot error" with a black screen. Please advise.

---

### Post by oldfred on 2013-05-03
Is this an UltraBook?
Where does boot error occur. Booting live installer flash drive or after install?

Boot error seems more like a message from UEFI/BIOS not from grub or Ubuntu. Did you verify that ISO downloaded correctly with md5sum and that you extracted it correctly to flash drive not just copy?

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Inoki on 2013-05-03
> **oldfred said:**
> Is this an UltraBook?
Where does boot error occur. Booting live installer flash drive or after install?

Boot error seems more like a message from UEFI/BIOS not from grub or Ubuntu. Did you verify that ISO downloaded correctly with md5sum and that you extracted it correctly to flash drive not just copy?

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Hi,

this seems to be an ultrabook, according to the link for specs. We did an MD5 checksum, the file is ok. This occured from both liveDVD and USB, he only got a black screen stating "Boot error", nothing else and right after setting the boot priority and re-booting, when it attempted to boot from the DVD / USB.

We used UNetBootin as well as several other options, tried different ISOs, different OSes, the same. If you click the link you get all the specs of the laptop. Link, this time in full format here: [http://www.asus.com/Notebooks_Ultrabooks/N71Jq/#specifications](http://www.asus.com/Notebooks_Ultrabooks/N71Jq/#specifications)

---

### Post by oldfred on 2013-05-03
UltraBooks have dual video, both Intel & nVidia.
After install you will need Bumblebee, but to boot you need either Intel video which usually works or nVidia setting of nomodeset. 
Does BIOS let you turn one or the other video off?

You will also have issues of RAID as Intel SRT uses RAID for the SSD.
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by Inoki on 2013-05-03
Thanks a lot, we will go through this, as this is extensive information requiring more time and we will get back with results.

---

