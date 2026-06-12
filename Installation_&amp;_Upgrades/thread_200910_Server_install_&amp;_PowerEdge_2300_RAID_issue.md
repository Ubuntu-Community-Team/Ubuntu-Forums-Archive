---
title: "Server install &amp; PowerEdge 2300 RAID issue"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by keram on 2006-06-20
I am wondering if there is anyone else out there that may have figured out how to get around the RAID controller issue on a PowerEdge 2300 server. The problem I am having is that the installer will not see the HDs. I get it to the point where I see the "Partition Loader..." bard get to 100% & then screen changes & that is it. 
Any help will be appreciated.
Thank you
Mark

---

### Post by Gorlaz on 2006-07-07
Hey Mark,
The only way I've been able to get one of these to boot was to disable the adaptec raid and route the scsi hdd plane directly to the mobo. You'll then need to do the raiding in Ubuntu rather than via hardware.

---

### Post by ebozzz on 2006-10-23
> **Gorlaz said:**
> Hey Mark,
The only way I've been able to get one of these to boot was to disable the adaptec raid and route the scsi hdd plane directly to the mobo. You'll then need to do the raiding in Ubuntu rather than via hardware.

Hi there,

Can you elaborate on what you did to get your install completed? I am attempting to do the same thing on a PowerEdge 2300 but I am stuck at step 5 with no progress.

---

