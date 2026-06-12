---
title: "Dual Boot 12.04 &amp; 10.10  - single drive"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by steve7777777 on 2012-05-28
Currently I'm on 10.10 EOL and would like to install 12.04 on the unused partition sda3.
I have two additional large drives for data currently in use.


From GPARTED:

/dev/sda1-ext4 286GB mount point: /
/dev/sda2 EXTENDED [COLOR="red"]12GB[/COLOR]
/dev/sda5 linux-swap 12GB
unallocated 5.69MB
[COLOR="Red"]/dev/sda3-ext4 168GB[/COLOR] <target for install> mount point: /media
unallocated 2.49MB

The drive is backed up with Clonezilla. Can the linux-swap be shared between the two installs? 
Is there anything useful to do with the unused 12GB sda2? 
Any advice, recommendations or warnings before I take the plunge?
Where should grub2 be installed? The goal is to eventually get rid of the 10.10 on sda1 and only boot to the 12.04.

Thanks!

---

### Post by oldfred on 2012-05-28
The extended is a container for logical partitions. Your extended right now is just the container for swap and is the same size as swap. How much RAM do you have? Generally the rules on swap have changed. When you only had 256KB or 512KB you needed 2X RAM. Then with 2GB or even 4GB you needed the same size as RAM in GiB. You really only need the same size as RAM if you want to hibernate when you gets lots of RAM as you hardly ever use swap.

I also keep all my data in /mnt/data(ext3) or /mnt/shared (NTFS) separate data partitions, so my / (root) is only 25GB with about 7GB used. How much of your / are you showing as used with gparted or df -h?

You want to use manual install or Something else and choose which partition to use as / and what format (ext4). It should automatically find you swap and reuse it. You would only need separate swaps if you hibernated, but hibernation with multiple operating systems can be risky.

If you have any data in sda3 as currently mounted /media, then you have to back it up as the new install will totally overwrite it.

---

### Post by steve7777777 on 2012-05-28
I use one partition for / (root) and home. 8GB RAM and I never hibernate so the swap I have is more than adequate. I'll continue to use ext4. I'll try "something else" install. As I mentioned everything should be backed up with Clonezilla and the partition is empty so no need to back that up. I just want to make sure that after the install I can boot into either the 10.10 or 12.04. I've read to keep GRUB where it is. Once everything is working - the 12.04 on sda3, I'll get rid of the 10.10. 

> **oldfred said:**
> The extended is a container for logical partitions. Your extended right now is just the container for swap and is the same size as swap. How much RAM do you have? Generally the rules on swap have changed. When you only had 256KB or 512KB you needed 2X RAM. Then with 2GB or even 4GB you needed the same size as RAM in GiB. You really only need the same size as RAM if you want to hibernate when you gets lots of RAM as you hardly ever use swap.

I also keep all my data in /mnt/data(ext3) or /mnt/shared (NTFS) separate data partitions, so my / (root) is only 25GB with about 7GB used. How much of your / are you showing as used with gparted or df -h?

You want to use manual install or Something else and choose which partition to use as / and what format (ext4). It should automatically find you swap and reuse it. You would only need separate swaps if you hibernated, but hibernation with multiple operating systems can be risky.

If you have any data in sda3 as currently mounted /media, then you have to back it up as the new install will totally overwrite it.

---

### Post by oldfred on 2012-05-28
You can install the newer grub from 12.04 or not. It does not give a choice to not install, so you have to install to the 12.04 partition even if you do not use it. 

Then in your old install this should add the new entry

sudo update-grub.

When you want 12.04's grub in the MBR:

sudo grub-install /dev/sda

But if you install grub to some place else than sda, it has an entry on where to reinstall.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by steve7777777 on 2012-06-11
> **oldfred said:**
> You can install the newer grub from 12.04 or not. It does not give a choice to not install, so you have to install to the 12.04 partition even if you do not use it. 

Then in your old install this should add the new entry

sudo update-grub.

When you want 12.04's grub in the MBR:

sudo grub-install /dev/sda

But if you install grub to some place else than sda, it has an entry on where to reinstall.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Fred, thanks! I ended up installing 10.04 on my spare sda3 partition. As instructed for GRUB I chose sda. 

To save time I reinstalled the applications using instructions found [**here**]("http://sosaysharis.wordpress.com/2012/05/02/upgrading-to-ubuntu-12-04-the-way-i-did-it/") - created a Pack File:

```
sudo dpkg --get-selections "*" > pack_file
```

Everything installed perfectly from the pack file, so all I had left was to copy over profiles from the old to new, and do fresh install of VirtualBox (from the Oracle site), Webmin, etc. I'll soon install 12.04 on the sda1 where the 10.10 currently is.

I tried out Mint 13 Maya, and no fault of Mint but my old smb.conf from the 10.10 didn't work with the Mint. My guess is the newer kernal. Something I don't like about Mint, which is probably a benefit for everyone else, is with the different versions - Cinnamon, Mate, etc the support community is a bit fractured. I still think that Ubuntu has the best and largest community support (no offense to crunch bang, or other distros) and that's the most important thing for my needs. I may not be thrilled with Unity, but I'll get used to it. Thanks again for the help!

---

### Post by oldfred on 2012-06-11
I am still trying Unity on one of my test installs, but changed my working install to gnome-panel or fallback which is almost the old style gui.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

