---
title: "partition mistake on 13.10 install"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2013-11-05
I have dual boot windows/ubuntu 13.10 that i installed from dvd. During install it had a partition page option but i just clicked on 'continue' with what was on page. Now when i restart it tells me i do not have space for updates avalable. I was hoping to just use disk and start over with fresh install but it just uses same partition as first install. I see the 'other'  option at bottom that will allow me to repartition and i clicked on that option but i have no idea what to change or how to use the partition table page at all. Any tutorials out there?

---

### Post by Bashing-om on 2013-11-05
jesse c; Hi !

These links should provide:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[http://ubuntuforums.org/showthread.php?t=2126166&page=2](http://ubuntuforums.org/showthread.php?t=2126166&page=2)

Post back with any addition inquiries.

[INDENT][INDENT]I hope this helps
[/INDENT][/INDENT]

---

### Post by jesse c on 2013-11-05
12.04 tutorial is nice but slightly diff in 13.10 and im trying to change the existing partitions not create partitions. Is there a way to 'erase' my 13.10 install and start a fresh install and use the easy'drag and drop' partition changer that i failed to use on first install?

---

### Post by oldfred on 2013-11-05
Even if reusing an existing partition you have to click on the change button and just select format as ext4 and mount as / (root) for root. If swap exists it finds it. If you have separate /home or other partitions you have to mount & those also. If existing /home has data you DO NOT want to format it or you lose your data.

You can use gparted from live installer or download a separate liveCD of gparted or parted magic to erase existing partitions or create new ones.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)


 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by jesse c on 2013-11-05
thanks . The change of file system and mount point is something i did not see on the tutorial. Do i ihave to change the windows partition first (if so ?file system ,mount point for windows partition) OR does expanding Ubuntu auto maticly shrink windows partition?

---

### Post by oldfred on 2013-11-05
You should always use Windows to shrink the Windows partition and immediately reboot into Windows so it can run chkdsk or make other repairs based on its new size. Make sure you are not hibernated and if Windows 8 that fast boot is off.  If you have not rebooted to run chkdsk the installer may not see Windows as it will not correctly mount NTFS that needs chkdsk or has hibernation set.
Then you can run auto install or manual install if you want more than the auto install default of / & swap and default sizes.

I do not think you can mount Windows in the installer, (have not tried with newest version), but you generally have to edit fstab later.
Better to have a separate shared NTFS data partition. You can create in advance or leave room after your install. Then you can mount shared data read/write and mount Windows system partition as read only to reduce chance of damage. Linux NTFS drives exposes all the hidden files & folders that Windows hides normally and can lead to users accidentally damaging Windows.

---

### Post by jesse c on 2013-11-05
Wow. Thanks for reply but you just made it sound impossible for my skill (lack of) level. It seems ubuntu made it really easy to change partition during install of 13.10 with the drag and drop but i clicked 'continue' without thinking and now im stuck in ignorance. I have been dual booting every release since 7e.04 via OSDisc CD's and have had major problems (me) each time and thought i was getting the hang of things. Now ubuntu made it 'drag and drop' easy and i screwed up. This laptop may just stay Windows. My desktop is dual boot (since 7.04) and i NEVER open it in windows as it would have hours of 'updates' before i could use it.

---

### Post by oldfred on 2013-11-05
You can use the auto install. 
But many of the new UEFI systems complicated it greatly. 
With BIOS there was one option.
With UEFI you now have UEFI with secure boot, UEFI without secure boot, and BIOS/Legacy/CSM. But if dual booting with Windows 8 you need to install in UEFI mode.
And you still may have video issues and need nomodeset or other boot parameters.

---

