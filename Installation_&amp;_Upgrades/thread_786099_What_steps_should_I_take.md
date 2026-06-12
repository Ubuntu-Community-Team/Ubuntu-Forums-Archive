---
title: "What steps should I take??"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by R0Y_G_B1V on 2008-05-07
So I've just ordered my system, 
Dell XPS 1330
3GB RAM
2.4Ghz C2D
8400M GS
64GB Solid-State Drive,

and the only reason I didn't opt for the Ubuntu preinstalled was so I could grab the SSD :) ANYHOW, what do I do now to dual-boot Ubuntu and Vista? I'm planning on stripping down Vista as well so it doesn't take up as much space. I'm just not sure what to do as far as installing what first, and where, partitioning this and that, especially with the SSD.

---

### Post by fmonjaraz on 2008-05-07
Download the ISO from ubuntu for hardy heron.  Install it.  There is a part in the installation that deals with partitions.  There is a scrolling bar that allows you to choose how much space you want for Ubuntu and Vista.  If this doesn't work for you google Gparted.  Gparted allows you to modify existing partitions and make new ones.  For Ubuntu you would need to resize vista in order to have some space left for ubuntu.

---

### Post by fmonjaraz on 2008-05-07
Download and burn the ISO (ubuntu-live-iso).  The ubuntu live cd also allows you to make partitions necessary for ubuntu.  
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by dmj99 on 2008-05-07
Agree with the above.  I would try out the live CD first, to make sure everything is compatible.  The partitioner in the installation process should allow you to determine the size of your Ubuntu partition.  Personally, I find 5-10 GB more than adequate (unless you plan on collecting a whole bunch of photos or music).  The installer will put GRUB on your MBR to automatically arrange dual booting.

---

### Post by R0Y_G_B1V on 2008-05-07
Thanks everyone very much, I thought it would be more complicated than that.

---

### Post by Pumalite on 2008-05-07
With Vista, you need to allocate space for Ubuntu with the Vista partitioner first. You cannot partition with the Ubuntu CD.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

