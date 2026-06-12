---
title: "Grub won't install on my Intel raid: Motherboard Gigabyte GA-P55M-UD2"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by lucasfxd on 2013-11-11
On Ubuntu 13.04 installation (and I think will happen in 13.10), I got an error when the program tries to install grub, and popup ask me to select another location. I have raid0, and even selecting the correct "/dev/mapper/......" won't install. The only solution was continuing the installation, then booting the Ubuntu via live-CD and using Boot-Repair:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)
```

Grub already has given me a lot of trouble... I think it should be a simple program to start the system, just that.

---

### Post by oldfred on 2013-11-11
Are you using the server install or 12.04 alternative installer. Alternative is being discontinued and they wanted to have LVM  and RAID in desktop but only LVM is now in 13.10. 

Server installer has the RAID drivers and you can add a desktop with that if you desire. 
Boot-Repair adds drivers so it should install grub to correct place.
But I do not know RAID nor LVM.

RAID 0 is not normally recommended.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

    
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by lucasfxd on 2013-11-12
Thanks. I installed using: ubuntu-13.04-desktop-amd64.iso
I like raid 0 for speed, and I have another 500GB hard disk just for my files, plus and external for backup. Planning to change my HDD raid to SSD raid...
Are you saying that installing the 13.10 server will work? Desktop will not? BTW, I'm dual booting with Windows 7 (already installed).

---

### Post by oldfred on 2013-11-12
Not sure about 13.10, would have to review the release notes. But previously when they annouced the discontinuance of the Alternative installer that was more for the few Desktops with RAID or LVM, they said they would add it to the standard desktop. 
I do notice LVM is now one of the default installs and some very new users see the ease of partitioning comment and just install with LVM, then do not know why standard partition tools do not work.
Any server install will work since you can install anything Ubuntu from any version. And the kernels are the same.
You may be able to just add the RAID drivers, but not sure if added to live installer, then whether the installer also sees them?? 

12.10 had this in the notes:
> 
[LIST]
[*]There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 

[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 
[/LIST]
[/LIST]



I see no mention of RAID? And not mention in 13.04 either.
[https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes](https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes)

---

