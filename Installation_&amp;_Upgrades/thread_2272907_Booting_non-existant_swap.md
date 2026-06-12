---
title: "Booting non-existant swap"
date: 2015-04-09
forum: Installation &amp; Upgrades
---

### Post by taylorzac42 on 2015-04-09
I have a fresh install of Ubuntu 15.04 beta 2 on a new ssd that is taking forever too boot. I've looked at the boot logs and it appears its trying to boot a swap partition that doesn't exist. I have no swap space. I'm not a complete noon but I've never dealt with the issue before. Suggestions? I haven't had to deal with a 20+ boot in years and its killing me.

---

### Post by dino99 on 2015-04-09
Please post the output of:
- sudo blkid
- cat /etc/fstab

the later needs to match the uuid of the first command

if you miss that swap partition, you can create one: [http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation](http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation)

---

### Post by taylorzac42 on 2015-04-09
This is 'blkid'

/dev/mmcblk0: PTUUID="f348c572-d8ef-7f41-881f-4221479da197" PTTYPE="gpt"
/dev/mmcblk0p1: UUID="10D3-3B59" TYPE="vfat" PARTUUID="c24dcef2-dbb8-4f93-aabd-78c837ee31c7"
/dev/sda1: UUID="2d99cdbf-0589-4e00-af3b-f3c43dccc69e" TYPE="ext4" PARTUUID="d8f7a8b6-01"
/dev/sda5: UUID="2b16c7bb-5dff-4b2f-8c37-c96ce3b99b30" TYPE="ext4" PARTUUID="d8f7a8b6-05"
 Heres the fstab

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2d99cdbf-0589-4e00-af3b-f3c43dccc69e /               ext4   noatime, errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=423f30bc-dd6e-422e-9d04-6bde6e0db2dd none            swap    sw              0       0

Now I see that it is showing a swap partition during installation. Its not there and it shouldn't be. So how do I make this right? Thanks for the quick response BTW

---

### Post by dino99 on 2015-04-09
why that 'vfat' partition ? what kind of installation is it ?

blkid is not showing a 'swap' partition, so create one as explained into the link first posted

note: i've no clue about ssd installation with 'gpt' so google around 'ubuntu ssd installation'

some related threads:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
[http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)
[http://www.leaseweblabs.com/2013/07/5-crucial-optimizations-for-ssd-usage-in-ubuntu-linux/](http://www.leaseweblabs.com/2013/07/5-crucial-optimizations-for-ssd-usage-in-ubuntu-linux/)

After reading these howtos maybe the best is to redo a clean installation to get the best results

---

### Post by taylorzac42 on 2015-04-09
The vfat is just an SD card. I don't have a need for a swap partition. I have 4gb ram and never get to more than 40% usage. Plus swap is a big no no with ssd. I may just do a complete reinstall. I've had a lot of weird issues since the install that I've never run into before. I just hate doing huge writes over and over again on a new drive.

---

### Post by oldfred on 2015-04-09
The quick fix is just to convert fstab line to comment by adding # to beginning of line like all the other comments.

       sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
or 
sudo nano /etc/fstab

I now use gpt on all new drives and most new flash drives. It just is slightly better than the old MBR(msdos) partitioning.

---

### Post by grahammechanical on 2015-04-09
New installs of 15.04 default to using SystemD instead of Upstart. Some have found OS loading times to be much quicker but when my long standing install of Vivid Veret switched over to systemd I was getting 80+ seconds to get to the login screen. SystemD was failing to load some kernel modules.

I am not saying that this is your situation. I am only saying that 15.04 brings with it a change to the init system and systemd in Ubuntu is still being refined. Today's update included one for systemd.

It is my understanding that when we install Ubuntu using either the Install Alongside option or the Erase Disk and install Ubuntu option that the installer automatically creates a swap partition.

If we use the Something Else option then the installer will use any existing swap partition or none at all if we do not designate a partition as swap. So, if you do decide to reinstall make sure that there is not a swap partition on that SSD and then use the Something Else option but do not set a partition with a mount point of swap.

Regards.

---

### Post by dino99 on 2015-04-09
> **taylorzac42 said:**
> The vfat is just an SD card. I don't have a need for a swap partition. I have 4gb ram and never get to more than 40% usage. Plus swap is a big no no with ssd. I may just do a complete reinstall. I've had a lot of weird issues since the install that I've never run into before. I just hate doing huge writes over and over again on a new drive.

please read the last link posted above into #4 to set the best boot paramaters into /etc/fstab

---

