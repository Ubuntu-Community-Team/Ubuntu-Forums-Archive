---
title: "Changing from Debian &quot;etch&quot; w/ RAID 1"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by rmjb on 2006-07-02
Hi, I'm new to Ubuntu, but it sounds interesting and I want to try it out.

I have a PC at home I use as a NAS currently running Debian "etch". Since it's my NAS I've implemented software RAID1 which has worked well for me. However, I want to know, if I install Ubuntu (or rather Xubuntu in this case) will it keep my RAID1? Will it keep my files?

I was planning do download the Xubuntu CD and just boot it in Live CD mode and test it out, but then I saw the alternate install CD should be used if you're going to do RAID so now I'm confused. Is the alternate CD also a Live CD??

I heard this board was very helpful so any advice you have to give would be great.

- rmjb

---

### Post by rmjb on 2006-07-11
Well let me respond to my own message to add to the collective, since it seems this forum is swamped with new users trying Ubuntu.

In my situation Debian was installed on a regular partition and the RAID 1 just contained my NAS files, i.e. not the OS.

The regular Xubuntu CD worked and installed. It did not see my RAID 1 right off, but all I had to do was install evms-gui (I think that's the name of the package) and this tool saw my RAID 1 virtual device. From there I converted it to an EVMS Volume and mounted it using the same tool and my files were all there.

After that I just had to put an entry in my fstab for it and the RAID 1 is now mounted on each reboot.

No need to tinker with mdadm (Linux Multi-Disk Admin utility) to recreate the raid, EVMS detected it and did it for me easily.

- rmjb

---

