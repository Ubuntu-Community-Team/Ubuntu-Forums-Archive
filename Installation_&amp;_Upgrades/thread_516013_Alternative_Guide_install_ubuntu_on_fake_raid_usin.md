---
title: "Alternative Guide: install ubuntu on fake raid using graphic installer"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by idanool on 2007-08-02
**** Please note that I'm really a newbie in linux, so I suggest someone more experienced then me would check this out first... :)  ****

Based on FakeRaidHowto.

I tried to install ubuntu 7.04 on my fake raid (nvidia) using the 
FakeRaidHowto Guide: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto).
it was much more difficult then regular installation using the graphical installer,
and in the end I couldn't get ubuntu to run X...

I thought of an alternative way to install it. for me it was much easier, but you'll need another non-raid drive for the installation process. so I wanted to share it with you :)

here's what I did:
1. install ubuntu regularly on a non-raid drive.
2. after the installation went successfully I duplicated all the linux partitions (root,boot,swap etc..) into my raid drive using Acronis Disc Director for windows (you may use other partition duplicator).

3. then all I needed to do install dmraid and grub on my raid and change fstab entries to the partitions on my raid.

Boot the Ubuntu CD and select Start or Install Ubuntu
Go to System > Administration > Software Sources and add the universe software repository.
Go to Applications > Accessories > Terminal and run

sudo su
apt-get install dmraid
dmraid -ay 
#(write down your raid path, something like "/dev/mapper/nvidia_aicgefgf")

#write down your relevant raid partitions numbers (/ /boot and so on) 
fdisk /dev/mapper/nvidia_aicgefgf #change to your raid map
p
q

#Mount the Temporary File Structure - details on FakeRaidHowto.
mkdir /target
# change your raid partitions numbers here
mount -t reiserfs /dev/mapper/nvidia_aicgefgf8 /target
mount -t ext3 /dev/mapper/nvidia_aicgefgf6 /target/boot

# install dmraid on the our new raid partition
chroot /target
apt-cdrom -m add
apt-get update
exit
sudo mount -t proc proc /target/proc
sudo mount -t sysfs sysfs /target/sys
sudo chroot /target
sudo apt-get install dmraid 

#then check the raid path name here again (after we chroot /target), this is the path we need to install grub to. (this is not mentioned on FakeRaidHowto, but it was different path for me then the original path)

#configure grub - again for details, take a look at FakeRaidHowto
grub
device (hd0) /dev/mapper/nvidia_cgcbiiag # this it the new raid path I mentioned above. this is the only place where I used this path.
root (hd0,5) # "/boot" partition number. it's the number you read at fdisk minus 1
setup (hd0)
quit

# ** Configure the Bootloader as in FakeRaidHowto.

#change the mount points to match your new raid partitions.
exit  # exit chroot /target
gedit /target/etc/fstab 

reboot

that's all. 
I hope I didn't forget anything ... you're welcome to change/correct this guide if you feel like.

---

