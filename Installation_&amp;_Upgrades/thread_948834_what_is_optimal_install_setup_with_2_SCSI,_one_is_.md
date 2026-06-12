---
title: "what is optimal install setup with 2 SCSI, one is faster but has limited space?"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-10-15
I have finally solved my multi- OS booting woes and am ready to re-install Ubuntu Studio Hardy LTS. I plan on using it for multimedia purposes including video editing/encoding, using Wine and also want to web browse with the most speed possible.  I have an HP workstation circa 2001/02 with SCSIs and adaptec controller at UltraWide 160 and one recent 500 GiG IDE drive (with /boot partition incl. "master" grub with chainloading, other linux OS and various data partitions). I have only 11 GiG free space on a SCSI (Fujitsu man3367MP, 36 GiG) with Windows on the first partition, but I can squeeze in another 2 GiGs if necessary.  My other SCSI (2cnd on the controller chain) is an 18 GiG Seagate Barracuda 36ES,LVD with slower rpm (7200 vs 10000) and the average access r,w(8.5/9.1 ms) is almost 2X slower than my Fujitsu drive.

I was thinking of setting up / on fastest SCSI and /home on slower.  I already have 2 GIGS swap on both slow SCSI and IDE.  I can select to put swap priority on the faster drive; in this case this would be the IDE- (with more heads, and, since I would be rendering the video files to /home- the drive not being written to can access swap faster).  

I have an ext3 data partition on my IDE, which I would like to render or process my files to, but I noticed that some applications such as DVD ripper (forgot the exact name) force me to write/render/encode to my /home. Should I set my swap priority equal in case I can render to my IDE drive? 

*here is an excerpt from a swap HOW TO:*


[I]"Imagine replacing the entry for the swap partition with these three lines:

/dev/hda6   none    swap    sw,pri=3    0	0
/dev/hdb2   none    swap    sw,pri=2    0	0
/dev/hdc2   none    swap    sw,pri=1    0	0

This configuration would cause the kernel to use /dev/hda6 first. it has the highest priority assigned to it (pri=3). The maximum priority can be 32767 and the lowest 0. If that space were to max out, the kernel would start using /dev/hdb2, and on to /dev/hdc2 after that. Why such a configuration? Imagine that the newest (fastest) drives are given the highest priority. This will minimize speed loss as swap space usage grows.

It is possible to write to all three simulataneously. If each has the same priority, the kernel will write to them much like a RAID, with commensurate speed increases.

/dev/hda6   none   swap   sw,pri=3   0   0
/dev/hdb2   none   swap   sw,pri=3   0   0
/dev/hdc2   none   swap   sw,pri=3   0   0"
[/I]


One last issue is the /temp files, as some of these video production apps. require a large /temp, but fast access speed is also desired! So do I make another partition just for /temp on the fast SCSI (is 2 GIGS enough for video editing?) or should I make a new (logical) partition on my IDE for /temp? 
 
I am a little confused, since I am completely new to video editing; all I know is that it's better to write/render the files to another drive than the "system" drive. So I don't know if /temp is considered a "system file" and thus should _not_ be on the same drive as where I might potentially render my video files to! 

*If I chance a certain setup now* and discover ways of improving it later by moving folders and creating diffrent partitions, is it just a matter of changing my entries in /etc/fstab or will there be many more steps?

Perhaps the diffrence in speeds are not worth a complex set-up, as a beginner and amateur anyways, I just want to optimize considering my hardware limitations(I am stuck with an older but pretty decent nv video card and 1 GIG RAM) and especially, I want to avoid dreaded system freeze/crashes!!!

So if anyone can set me straight on all this, it would be appreciated!  



:guitar:    :KS                                   :KS   :guitar:

---

