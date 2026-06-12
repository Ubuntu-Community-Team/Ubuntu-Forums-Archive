---
title: "/usr mount point lost  - cannot boot"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by buppaclaus on 2010-04-02
I've lost the /usr mount point and don't know how to get it back!!!

Due to root filling up I wanted to separate out /usr to it's own files system so I:

1. Created a logical volume for usr.
2. Created a temporary mount point, and mounted the new volume.
3. In single user mode copied the contents of the /usr directory to the new directory.
4. Edited the fstab appropriately.
5. Moved /usr to usr.old

I then rebooted WITHOUT first recreating the /usr mount point.

I can get into GRUB but cannot see any useful commands that could help me.

I'm now stuck.

I have tried using the AMD64 Alternative CD without success.  I am running a RAID 10 system and think this may be complicating the issue.

Any Suggestions??

---

### Post by oldfred on 2010-04-02
I assume you can still chroot into it from a liveCD or other install, the commands I show were for other problems, you should be able to just make your mount?:

Of course you must first know what partition you want to mount, in this example I'm using sda1:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get update
apt-get upgrade
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

