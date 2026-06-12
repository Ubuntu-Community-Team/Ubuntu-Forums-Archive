---
title: "Feisty upgrade using LVM and new drives."
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by chris_andrew on 2007-03-19
Hi,

My /home partition is getting a bit tight.  I will shortly be upgrading to Feisty.  I have some spare HDD's.  Can I add these to my box, and then use LVM to increase the size of my existing /home?

I guess I'll have to do a fresh install, as "dist-upgrade" will not give me the option to reconfigure my partitions.

Has anyone tried this, or can anyone offer advice?

Thanks,

Chris.

---

### Post by jspaces on 2007-06-02
> **chris_andrew said:**
> Hi,

My /home partition is getting a bit tight.  I will shortly be upgrading to Feisty.  I have some spare HDD's.  Can I add these to my box, and then use LVM to increase the size of my existing /home?

I guess I'll have to do a fresh install, as "dist-upgrade" will not give me the option to reconfigure my partitions.

Has anyone tried this, or can anyone offer advice?

Thanks,

Chris.

Hi Chris, the volume has to be set up in the LVM volume group to allow expanding the capacity. The old home folder should be mounted as old_home or something similar then set up the LVM during the fresh install with the new home folder inside the volume group. Once completed you then can copy the contents of the old home folder into the new one. If you want once the data is safely off, the old home folder can be deleted and then the free space can be assigned into the LVM volume group increasing the space available.
Hope this helps.
Jeff

---

