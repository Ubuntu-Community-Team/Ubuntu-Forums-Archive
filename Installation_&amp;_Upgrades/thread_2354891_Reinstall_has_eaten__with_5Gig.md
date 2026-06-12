---
title: "Reinstall has eaten / with 5Gig"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-03-07
After what I thought was a clean reinstall of / boot up reports 34meg free.

Using a LiveDVD of 16.04.2, I reinstalled or so I thought, /

At reinstall time, I formatted / and left /home and /swap alone. On reboot I had no /home as it had no mount point, but the OS did come up. After some more fiddling, I found the blkid for /home edited fstab to try to fix my problem. On reboot, the OS now has my /home directories, files, docs, etc. but it's not where it should be. Looking at the drive from LiveDVD, GParted showed no mount point for /home or /swap. So I added mount points manually. Now when I power up, I get a message that / has 5 or 6 gig in it. 

I have a separate  /home and it was backed up and offline before this work began.

---

### Post by Paddy Landau on 2017-03-09
I'm a little confused — gparted doesn't provide mount points when you boot from a Live CD. The mount points are, as you mentioned, decided by [FONT=lucida console]/etc/fstab[/FONT] when you boot normally.

When you reinstalled, did you remember to tell the Installer about your [FONT=lucida console]/home[/FONT] and swap partitions? If you specify them (but ensure that you don't tick the "Format" box for [FONT=lucida console]/home[/FONT]), the Installer will add them to [FONT=lucida console]/etc/fstab[/FONT] automatically.

How large is your root partition? It might make things clearer if you post [FONT=lucida console]/etc/fstab[/FONT] here along with the results of both [FONT=lucida console]sudo parted --list[/FONT] and [FONT=lucida console]lsblk --fs[/FONT].

---

### Post by Mark_in_Hollywood on 2017-03-09
> **Paddy Landau said:**
> I'm a little confused — gparted doesn't provide mount points when you boot from a Live CD. The mount points are, as you mentioned, decided by [FONT=lucida console]/etc/fstab[/FONT] when you boot normally.

When you reinstalled, did you remember to tell the Installer about your [FONT=lucida console]/home[/FONT] and swap partitions? If you specify them (but ensure that you don't tick the "Format" box for [FONT=lucida console]/home[/FONT]), the Installer will add them to [FONT=lucida console]/etc/fstab[/FONT] automatically.

How large is your root partition? It might make things clearer if you post [FONT=lucida console]/etc/fstab[/FONT] here along with the results of both [FONT=lucida console]sudo parted --list[/FONT] and [FONT=lucida console]lsblk --fs[/FONT].

GParted, if asked to create, format and give mount points will do as I earlier described. Since this problem occurred, I have warning that there is xx megabytes of free space and do I want to examine the drive.

It has become easier to re-format the drive as a bare metal re-install.

Thank you Mr. Laundau. Thanks to the Linux Community for having a look here.

---

### Post by Paddy Landau on 2017-03-09
> **Mark_in_Hollywood said:**
> It has become easier to re-format the drive as a bare metal re-install.
I'm glad that you managed to find a solution. If you have further problems, please do post again.

---

