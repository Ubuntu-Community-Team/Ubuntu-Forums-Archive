---
title: "Installing over a different distro (and dual-boot with Windows)"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by Mangetout on 2005-09-28
Bit of a newbie question, so please be gentle with me.  I have only a little experience of Linux - I've installed and played with various different distributions and am more or less aware of the absolute basics.

I've got a couple of machines on which I have working installations of SUSE 9, dual-booting with Windows XP - this is all well and good, but I want to replace SUSE with Ubuntu, mostly because of the user-friendliness and ease of package installation.  I need to keep the NTFS/Windows partition, for a whole raft of not-very-interesting reasons, but there's no need to resize it, or touch it at all.

Am I right in thinking that the guided partitioning process during install will just detect the existing (ReiserFS) partitions that are already set up, wipe them and install Ubuntu in place of SUSE?  How much fiddling will be necessary to configure GRUB for dual-booting, or will the installer also handle this?

---

### Post by lisje on 2005-09-28
hey,

installing over SUSE is not that hard... you just tell the installer you want to partition yourself... your windows partition will be shown and your SUSE partitions...
you just select the SUSE partions and give them the right mount points (/ and /boot) and don't keep de info on them... 
swap normally is still ok&#233; and then you scroll down and tell the installer to write the changes to the harddisk... then the ubuntu install will proceed...

Normally your windows will be recognized by the installer and put into grub... so no worries there.

---

### Post by mister zed on 2005-09-28
Wow, this is _exactly_ what I am trying to do as well.  I can't believe my luck.  I can't get SUSE to work full screen on my machine and the Ubuntu live CD got everything working with zero effort on my part.  I was extremely impressed.  So now I want to install Ubuntu and I am terrified that I might make a mistake and have precious Windows data overwritten.  Mangetout, did everything work out fine for you?  Thanks.

---

### Post by Mangetout on 2005-09-29
OK; I did it and it works just fine; you just need to proceed very calmly and carefully through the (normal) install process, making sure you don't ever select anything that looks like 'wipe entire HD' and select guided partitioning instead - the guided partitioning gizmo recognised the existing partitions and knew to leave the NTFS partition alone.  It did need to be explicitly told to erase the contents of the existing ReiserFS partition and mount it to /, but apart from that, it was just a clickthrough.  Towards the end of installation, It kindly asked me if I wanted the boot menu to be written to the master boot record to enable multi-booting and again, this was a clickthrough.  Couldn't really be simpler - just pay careful attention at the partitioning stage.

I now have a dual-boot Ubuntu/WinXP machine.

Thanks **lisje**.

BTW; **mister zed**; it would be wise to back up all your data before you proceed; this is always a good idea, even if you're not expecting problems.

---

### Post by chettyk on 2005-09-29
One thing worth doing is putting **/home** on a separate partition. That way, you can install a new distro without losing your personal settings and data. Fire up the new distro and you are ready to go.

---

### Post by colini on 2005-10-07
Hi,

I am also considering installing over a SUSE 9.1 installation.  But instead of destroying the existing partitions I'd like to leave the /home partition as is.

/home is formatted as reiserfs.  Will the ubuntu installer allow me to leave this unchanged, and also configure itself to read the reiserfs partition.  Which filesystem does the ubuntu installer use by default?

thanks,
Colin

---

### Post by lisje on 2005-10-09
[QUOTE=colini]Hi,

I am also considering installing over a SUSE 9.1 installation.  But instead of destroying the existing partitions I'd like to leave the /home partition as is.

/home is formatted as reiserfs.  Will the ubuntu installer allow me to leave this unchanged, and also configure itself to read the reiserfs partition. [/QUOTE]

normally ubuntu will leave the partition unchanged... it should be able to read the reiserfs partition... it could be that you need to set the mountpoint to /home again

---

