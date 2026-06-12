---
title: "Create ISO installation from installed Ubuntu 14.04"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by tbaror on 2015-05-05
Hello All,

I have installed for our organization monitoring system (icinga2) with all necessary package ,
 and the system is configured as we wish after long installation process.
We have  few remote offices we would like to deploy this same system . 
My question is what is the best way to create from current installation  kind of iso that could be mounted on USB and installed on existing  system Ubuntu 14.04  x64 based ?
Is there any tool available for such task ? 

Please advice
Thanks

---

### Post by Bucky Ball on 2015-05-05
You could try Clonezilla. Start here:

[https://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](https://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

... and then, page two is:

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

There's also [Systemback]("http://sourceforge.net/projects/systemback/"), but I've never used that.

Have a search as there's probably others.

---

### Post by TheFu on 2015-05-05
You can treat it like any other system backup and restore. There are many ways - images, restores procedures, "linux from scratch" which lets you create your own distro. There used to be a tool to make a re-installable image for Ubuntu. Don't know what happened to that tool - perhaps it wasn't updated for UEFI. I dunno.
I use something like this for backup/restore. [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) This method doesn't require the source OS be powered off. 

For image-based cloning, there is clonezilla, partimage, fsarchiver, and dd/ddrescue - others. These all require the source OS be unused (off) to avoid file corruption during the transfer. That is hard (impossible?) to automate for nightly backups and disruptive to production systems. When I need to move an install from disk-A to disk-B, I use rsync, then run grub-install/update-grub onto the new disk.  That assumes it is a physical install which doesn't happen very often. We've been doing virtual machine stuff since around 2007 for almost every install. For VM migrations, we use live migration methods or just restore from a recent backup as outlined above.

You'll want to setup remote management, so something like puppet or ansible can be used to maintain the system config. Ansible is great for most situations and only takes about 30 min to start managing 2-500 systems.  No agents need to be deployed, just ssh - which you want anyway.

If you don't have remote access to the deployed systems, perhaps doing an install to a HDD, removing the /etc/udev/ network rules is all you need.

Many people are deploying stuff like this using virtual machine images or containers, like docker.  Whether that makes sense or not is something only you can decide.  I know that many commercial software vendors are releasing demos as "VM appliances" to avoid the configuration nightmare that their systems.  Then at the deployment location, they just need to run KVM or VirtualBox and "import" the appliance. There are lots of pre-built appliances for download. Just be certain to remove the udev net rules so eth0 will be used, not eth1 ... eth9. That can be confusing to noobs, though it shouldn't cause issues for the OS.

Guess the real answer is - there are many different ways and you will need to decide and find the best way for you, the people at the remote location and support people who will get the phone calls for help.

---

### Post by tbaror on 2015-05-09
Thanks for the answer 
I just used system back its works great
cheers

---

