---
title: "ec2 ubuntu instance"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by framallo on 2011-05-07
Hi,

I'm trying to create a new ubuntu instance on amazon ec2.

But After I set it up the instance is not longer accessible.

Basically I use this AMI
==============================================================================================
| Region   | us-east-1                                                                       |
| AMI      | ami-7000f019                                                                    |
| manifest | [https://console.aws.amazon.com/ec2/home?region=us-east-1#launchAmi=ami-7000f019](https://console.aws.amazon.com/ec2/home?region=us-east-1#launchAmi=ami-7000f019) | 
==============================================================================================

But after I change the /etc/fstab is brakes an doesn't work anymore.
Basically I move the sda2 from /mnt to /home. 
Then I move /home/ubuntu to /mnt/ubuntu and reboot.

Eventually I have this error:

cloud-init running: Sat, 07 May 2011 17:37:35 +0000. up 7.62 seconds
An error occurred while mounting /home
mount: unknown filesystem type '*'
mountall: mount /home [460] terminated with status 32
mountall: Filesystem could not be mounted: /home
Press S to skip mounting or M for manual recovery


Any ideas?
Thanks!

---

