---
title: "Misleading option in Ubuntu 10.10"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by ksprasad on 2011-01-15
Hi,

 I lost my entire windows partition due to a misleading option in ubuntu 10.10 installation.

 There is an option to install ubuntu side by side. Once that option is selected it should never use entire disk for installation. But that is not the fact.

After selecting that option, it will display the largest partition available on disk. We can drag the pointer to select the appropriate size for ubuntu from that partition. But below, there is another option 'Select entire partition'. 

So 'Select entire partition' should select only that single partition showed above. It should not use entire disk. But it used entire disk (In my case). Isn't it wrong? 

Regards,
ksprasad

---

### Post by kansasnoob on 2011-01-15
> **ksprasad said:**
> Hi,

 I lost my entire windows partition due to a misleading option in ubuntu 10.10 installation.

 There is an option to install ubuntu side by side. Once that option is selected it should never use entire disk for installation. But that is not the fact.

After selecting that option, it will display the largest partition available on disk. We can drag the pointer to select the appropriate size for ubuntu from that partition. But below, there is another option 'Select entire partition'. 

So 'Select entire partition' should select only that single partition showed above. It should not use entire disk. But it used entire disk (In my case). Isn't it wrong? 

Regards,
ksprasad

Yes! I first complained about that just prior to 10.10 being released:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Followed up later on after that earned a "won't fix":

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

And later found that was a duplicate of this one:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106](https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106)

Besides filing and following up on bug reports I've even tried addressing the issue at the ubuntu-installer team and ayatana to no avail :(

I even started a thread here about that:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Your comments at Launchpad would be welcome!

---

### Post by ksprasad on 2011-01-15
Thanks for the info. 
Hope the issue will be resolved in the next release, Ubuntu 11.04

Regards,
ksprasad

---

