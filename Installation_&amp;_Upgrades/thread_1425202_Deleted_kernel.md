---
title: "Deleted kernel"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by slowpoke115 on 2010-03-08
Hey all, I have a 'silly friend' who deleted various older kernels via the command line using rm - now evidently, despite the most up-to-date kernel being present the machine doesn't boot. This originally happened due to a full distro upgrade, followed by a botched poulsbo kernel-header install and then the removal of previous kernels (for some unusual reason the oldest kernel was automatically booting, i suspect due to it having functional display) 'my friend' now has nothing, computer won't get into anything, not even grub. 

I suspect the solution is to boot using a live cd, mount the fs and to do an apt-get install kernel blah (generic ofcourse) and then to auto update 'my friends' grub. Can someone confirm and also advise on any problems 'my friend' is likely to face. I reckon the poulsbo graphics problems are at the core of this entire problem.

Thanks :)

p.s the silly friend is me...

---

### Post by oldfred on 2010-03-08
If kernel is the issue these are the commands I saved to chroot into a system. If you know which older kernel you need you can download that also.

Of course you must first know what partition you want to mount, in this example I'm using sda3:

sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt

#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
sudo apt-get install grub-pc  #make sure grub is updated 

#When done:

exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by slowpoke115 on 2010-03-09
> **oldfred said:**
> 
sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt

#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
sudo apt-get install grub-pc  #make sure grub is updated 

#When done:

exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

That worked a treat, some steps not needed (sudo not needed if using chroot, also mounting /dev causes errors as stdout goes to /dev/pts which is read only). Having said that, I copied and pasted most of this and got a functional system so the steps suggested do not change the outcome. Also "Then run whatever other commands needed" could of been interperated anyway, but instead you went a step further and gave me some suggested commands. I'm VERY VERY thanful :)

---

