---
title: "wubidr.mbr not found or corrupt"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by IamKobal on 2013-01-15
I tried using wubi to install ubuntu and it gave me the error saying that "wubidr.mbr wasn't found or is corrupt"

how can i fix this? i was looking around the forums a bit and saw that it didn't work with a UEFI win install. i got it confirmed by alienware that i have a BIOS install. (I have no idea what this means but i saw it on other posts so i figured i would include it in this post. i am a complete noob to this stuff in case you couldn't tell)

I am on windows 7 also. If there is anymore info that you need to help me, feel free to ask.

---

### Post by oldfred on 2013-01-16
I really do not know wubi. The issue is not UEFI per se, but gpt partitioning which Windows uses with UEFI. Ubuntu full installs work from MBR(msdos) or gpt partitions. 

       Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

    
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by IamKobal on 2013-01-17
> **oldfred said:**
> I really do not know wubi. The issue is not UEFI per se, but gpt partitioning which Windows uses with UEFI. Ubuntu full installs work from MBR(msdos) or gpt partitions. 

       Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

    
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
i did what both of those said to do and i still have the problem.

---

### Post by oldfred on 2013-01-18
You will have to download an Ubuntu ISO or the Secure remix ISO and create a DVD or Flash to work as a live flash system. Then run Boot-Info report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

