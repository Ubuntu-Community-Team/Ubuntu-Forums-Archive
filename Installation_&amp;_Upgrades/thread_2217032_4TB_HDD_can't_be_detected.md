---
title: "4TB HDD can't be detected"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by ram13 on 2014-04-15
ubuntu 13.10 server installed on USB stick.

recently I bought a 4TB WD Green drive and I made a single partition as ext4 using ubuntu (I google on how to do) and mounted it. It was working fine and I dumped 1.5 TB of data. Afterwards I just disconnected the hdd for the purpose of reinstalling ubuntu server.

After reinstalling ubuntu server 13.10 on a usb stick I plugged my 4TB HDD and the hard drive can't be detected any-more (sudo fdisk -l showed only the usb volume). The more surprise comes with the live CD which again doesn't detect my 4TB!! But on the system I have windows (on different HDD) which can detect the ext4 4TB HDD and I also checked on my other desktop (MAc) where can I also be deteced!!

what is wrong with ubuntu and it is not detecting my 4TB HDD? may be the single partition is an issue? or ext4? can you help to find a solution, thanks.

---

### Post by oldfred on 2014-04-15
You do not use fdisk on gpt partitioned drives. Fdisk will only show the protective MBR. Gpt drives have a protective MBR with one gpt partition entry so older tools like fdisk recognize that it is already partitioned.

If not sda, change to correct drive:
       sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

    
If you do not have have gdisk, you should. It is the fdisk for gpt drives.
sudo apt-get install gdisk
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

