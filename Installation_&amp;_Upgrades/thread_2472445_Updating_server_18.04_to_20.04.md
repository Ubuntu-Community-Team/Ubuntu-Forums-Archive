---
title: "Updating server 18.04 to 20.04"
date: 2022-02-27
forum: Installation &amp; Upgrades
---

### Post by kristjk on 2022-02-27
Hello.

I have an Ubuntu 18.04.6 LTS (GNU/Linux 4.15.0-169-generic x86_64) running with Plex server (which is the main reason for the server) and I was wondering if updating to 20.04.04 LTS would mess with the metadata of the Plex server?  Or can I just run do-release-upgrade and everything should work as before ?

Best regards,
Kristjan

---

### Post by rsteinmetz70112 on 2022-02-27
End of Standard Support for 18.04 will end in April 2023. I routinely do-release-upgrade on my servers but I have not experience with Plex.

---

### Post by TheFu on 2022-02-27
> **kristjk said:**
> Hello.

I have an Ubuntu 18.04.6 LTS (GNU/Linux 4.15.0-169-generic x86_64) running with Plex server (which is the main reason for the server) and I was wondering if updating to 20.04.04 LTS would mess with the metadata of the Plex server?  Or can I just run do-release-upgrade and everything should work as before ?

Best regards,
Kristjan

That's the theory, but reality is often different.  Always, always, create backups of anything you cannot lose before starting the 3-hour upgrade process.
My plex server is on 18.04 still. When I move to 20.04, I will likely switch to Jellyfin instead for better privacy. I've been running both for about 3 months on the same system. My 20.04 will be a fresh install to a new SSD. I plan not to touch the existing storage (30+TB). Here's the initial layout:
```
NAME                         SIZE TYPE FSTYPE   LABEL      MOUNTPOINT
nvme0n1                    465.8G disk                     
&#9500;&#9472;nvme0n1p1                   50M part vfat     EFI        
&#9500;&#9472;nvme0n1p2                  600M part ext2     BOOT-A     
&#9492;&#9472;nvme0n1p3                  465G part LVM2_mem            
  &#9500;&#9472;vg00-swap                4.1G lvm  swap                
  &#9500;&#9472;vg00-root                 35G lvm  ext4     root       
  &#9500;&#9472;vg00-var                  35G lvm  ext4     var        
  &#9492;&#9472;vg00-home                 25G lvm  ext4     home
```

I'm getting close to the install.  /var is sized larger than normal to hold 1-2 play virtual machines. I actually mount the metadata storage for media servers into separate LVs.
```
NAME                         SIZE TYPE FSTYPE   LABEL      MOUNTPOINT
  &#9500;&#9472;istar--8TB--B-plex_varlib
  &#9474;                           90G lvm  ext4                /var/lib/plexmediaser
  &#9492;&#9472;istar--8TB--B-jellyfin_varlib
                              90G lvm  ext4                /var/lib/jellyfin
```
After it is done, looks like there will be plenty of room to move the /var/lib/jellyfin LV back the the NVMe storage.

---

