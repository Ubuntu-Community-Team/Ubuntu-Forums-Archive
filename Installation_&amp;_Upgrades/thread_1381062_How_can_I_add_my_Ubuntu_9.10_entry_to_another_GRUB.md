---
title: "How can I add my Ubuntu 9.10 entry to another GRUB setup?"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Zachs Kappler on 2010-01-14
My problem is this, I decided to try Pardus since I had the disk space available and learned that it never created a entry for Ubuntu 9.10 64-Bit. I have tried many different boot options and have only gotten it to show the first black and white bootsplash but never can continue to boot. Is there a option I am forgetting to add via Pardus's GRUB editor or is it something else?

---

### Post by oldfred on 2010-01-14
I am not familiar with Pardus. Does it use grub2? Ubuntu's grub legacy was modified to use ext4 partitions but not every distribution did that since grub legacy was not centrally maintained anymore. You may not be able to boot Karmic if it is ext4. There may be a way with chainbooting but grub2 is better at finding other installs automatically in most cases and can be manually updated easily if not found automatically. I would use Karmic's bootloader and use it to boot into your other distribution. But then we are Ubuntu centric here.

---

### Post by Zachs Kappler on 2010-01-31
> **oldfred said:**
> I am not familiar with Pardus. Does it use grub2? Ubuntu's grub legacy was modified to use ext4 partitions but not every distribution did that since grub legacy was not centrally maintained anymore. You may not be able to boot Karmic if it is ext4. There may be a way with chainbooting but grub2 is better at finding other installs automatically in most cases and can be manually updated easily if not found automatically. I would use Karmic's bootloader and use it to boot into your other distribution. But then we are Ubuntu centric here.

Okay, how would I go about installing GRUB2 over the GRUB Legacy setup? I know how to install legacy, but i've read it's a different process this time.

Also Ubuntu's documentation on upgrading GRUB didn't work, Pardus must have done something to it that prevents the upgrading process to find it.

---

### Post by oldfred on 2010-01-31
On the pardus page I found it mentions both grub .97 and 1.97?
[http://distrowatch.com/table.php?distribution=pardus](http://distrowatch.com/table.php?distribution=pardus)

to reinstall grub2 with the karmic livecd where X & Y are drive & partition for Karmic use fdisk if unsure:
$sudo mount /dev/sdXY /mnt
$sudo mount /dev/sdXZ /mnt/boot  ##only if you have a seperate /boot partition which could of course be on another drive as well
sudo grub-install --root-directory=/media/sdXY /dev/sda
$sudo grub-install --recheck --root-directory=/mnt /dev/sda


To reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

there are several ways simple, full chroot:
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I would expect grub2 to find the pardus install and allow you to boot that.
sudo update-grub

---

