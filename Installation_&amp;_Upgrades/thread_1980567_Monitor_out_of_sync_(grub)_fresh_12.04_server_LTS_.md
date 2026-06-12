---
title: "Monitor out of sync (grub?) fresh 12.04 server LTS install"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by philvdb on 2012-05-15
Dear all,

I have spent all day trying to install 12.04 server at this university machine (a little dated hardware, Fujitsu Siemens Primergy TX200 S2).

Installation goes smoothly all the way, four SCSI drives with an ext3 root partition on sda1, sda5 is the logical swap partition and sdb1 through sdd1 are bundled into a RAID5 array.

So far so good. Upon rebooting after installation I get one second of "GRUB loading" and then the monitor goes out of sync. I have tried any combination of keys I can think of (simply "Enter" won't do the trick either I'm afraid) but I can't get past an out of sync screen. Holding down (yes, the left) shift through the entire boot process gets me nowhere either.

Of course, I have googled and of course I have found that I should be uncommenting the "default resolution" from /etc/default/grub. And I tried my very best to do this. Using an even more dated Knoppix live CD I could edit the file, but it only has Grub 0.something which only lands me on "/boot/grub/stage1 not read correctly". I was even desperate enough to try installing Lilo, but that old version apparently capitulated with this new kernel version.

During one of the about twelve installations of 12.04 server today I went into a console right after grub was installed and edited /etc/default/grub to include a resolution default, being unable to update the grub installation (i. e., run grub-install) at that point though, this didn't make a dent either.

Now I'm completely out of ideas.

Can someone please help me? Is there any way to change the grub configuration during the Ubuntu installation process?

Edit: now saw the sticky post and I guess I will have to buy more blank dvds and burn a current ubuntu live disk - unless someone can show me a way to do this with the regular 12.04 server install CD?

---

### Post by oldfred on 2012-05-16
Welcome to the forums.

I do not know servers. But the server & alternate installers are not liveCDs.

But always suggest having a current version  liveCD or USB or repairCD for every version installed. I now prefer USB flash drives as all my computers boot flash,  and have multiple ISO on one flash drive including Ubuntu and several repair ISO.

I think you could chroot from you Knoppix as then you would be working from inside your install. But it probably is easier to have a liveCD.

---

### Post by wilee-nilee on 2012-05-16
If you change that resolution you can run a update grub from a chroot to set it to boot with that resolution.

As suggested above the correct or at least a ubuntu live cd will make this easier a chroot goes like this. XX is the HD and partition

                                    [FONT=Verdana, sans-serif][SIZE=1]```
sudo mount /dev/sdXX /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``` [/SIZE][/FONT]Then run```
update-grub
```then crtl-d to unmount the chroot and reboot.

---

### Post by rooijan on 2012-05-22
FYI I had a problem with a fresh install of Ubuntu 12.04 server.  I use Drac to remotely control the server console and it gave me "Out of Range" errors.  I tried a lot of things but finally nomodeset worked as this link explains:

[http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation)

My change:
# grep nomodeset /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
# update-grub

Tinkering with these two options did NOT work:
# grep GFX /etc/default/grub 
#GRUB_GFXMODE=800x600x16
# grep console /etc/default/grub 
#GRUB_TERMINAL=console

---

