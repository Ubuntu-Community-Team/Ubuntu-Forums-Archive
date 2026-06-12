---
title: "Ubuntu 10.04 dual boot with Win7"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by TM720 on 2012-01-04
Hi all,

I've been trying to help a co-worker get Ubuntu to dual boot on her laptop with Windows 7.

Since Windows7 was already on there, I put in the Unbuntu install disk and apparently it did not see the Windows 7 partition because it now is only running Ubuntu with no signs of Windows 7.

I'm not sure where I went wrong here. I've done this before on my own computer, albeit it is older than the one I'm currently working on but I have done this successfully before.

Part of the original issue was that our fantastically clueless IT manager put windows on a single 20 GB partition, which quickly filled to capacity. She then wanted to run Ubuntu and got Wubi, but she didn't realize for the applications she was running that Wubi would basically fail miserably because of its inherent limitations. She is trying to work with 3D movies through a projector...

So I recommended making a separate partition for Ubuntu alone.

We made 120 GB partition for Ubuntu separate from the windows partition, but Ubuntu's installer didn't see that which surprised me.

Obvious we are going to have to start over here...

Installing Windows 7 first, and then Ubuntu on a separate partition...

How do I make sure this works right?

Also, 10.04 network applications do not work at all after install. Even an Ethernet cable is not recognized by this.

---

### Post by darkod on 2012-01-04
First sit down and calculate how much space of the hdd you want dedicated to win7, and how much to ubuntu. If you are installing win7 from dvd you can select the partition size, if you use a recovery partition it will do it how it's designed to do it.

If installing with the dvd make sure you create the win7 partition with the size you want it allocated. Don't let it take the whole hdd. If there are any partitions, delete them all and then create one ntfs with the size you want for win7. Leave the rest of the disk as unpartitioned. DO NOT create ntfs partitions for linux, it doesn't install on ntfs.

After that, boot the ubuntu installer and just select the Use Largest Available Free space option when asked where to install. It will use the unpartitioned space and create the root and swap partitions itself.

If you need more specific partitioning layout you will have to use the manual option when installing, not any of the auto ones.

It's very weird that the wired connection doesn't work. Usually most wired adapters work out of the box, depending on the adapter.

---

### Post by Jahid65 on 2012-01-04
Please use gparted (recommended) or disk utility (installed by default) from the Ubuntu Live CD to make partitions. I have had issues with windows default partition manager.

What I always do is to make an ext4 file-system with gparted first. Then I click the installer application & install Ubuntu 

 For Lan card, it should work out of the box. What chip/adapter the lan card is using ?

But it will be better to test with the latest version or you can wait for the next LTS release which will 12.04 & will be supported for 5 years.

---

### Post by Mark Phelps on 2012-01-05
Like Vista, Win7 can be finicky when trying to install it into partition made from OUTSIDE Windows.  While it should work OK, sometimes, it does not.

The following is a bit complicated, but it has the advantage of NOT creating a second, largely unneeded, Windows BOOT partition (which Win7 installer does automatically), and allows the Win7 installer to format its own partition -- which works best in the long run:
1) Don't know how your drive is formatted, but you need to start with a 30GB NTFS partition, followed by a 20GB Linux partition, followed by the rest of the drive formatted into a single NTFS data partition.  You can do all of this by booting from an Ubuntu desktop CD and using the Disk Utility.
2) Once that formatting is done, REMOVE the initial NTFS partition -- that's right, remove it.
3) NOW, boot using your Win7 DVD and install to the initial free space.  That will create a new NTFS partition in that space
4) You can now either install Ubuntu reusing the Linux partition previously created, or you can remove that partition and let the Ubuntu installer format it.  But -- be careful.  It's easy to accidentally format the WRONG partition in the installer and wipe out Win7.
5) When done installing Ubuntu, it should have detected Windows already on the drive and built a GRUB menu for you containing the different OS entries.  When you reboot, you should get that menu.

---

### Post by darkod on 2012-01-05
> **Mark Phelps said:**
> 
2) Once that formatting is done, REMOVE the initial NTFS partition -- that's right, remove it.
3) NOW, boot using your Win7 DVD and install to the initial free space.  That will create a new NTFS partition in that space


From my experience of installing win7, this way it will create the system reserved too. Any type of install where the win7 installer needs to create a partition from unpartitioned space, will create the small partition.

The only way to avoid it is to have an existing partition. Even if you format it, doesn't matter, as long as it you don't create it with the installer.

---

### Post by Mark Phelps on 2012-01-05
> **darkod said:**
> From my experience of installing win7, this way it will create the system reserved too. Any type of install where the win7 installer needs to create a partition from unpartitioned space, will create the small partition.

Then ... our experiences differ, because I've only had the Win7 installer automatically create the BOOT partition when the drive was blank.  But then, I have been installing Win7 prior to SP1.  Maybe that is something they have changed.

---

### Post by darkod on 2012-01-05
> **Mark Phelps said:**
> Then ... our experiences differ, because I've only had the Win7 installer automatically create the BOOT partition when the drive was blank.  But then, I have been installing Win7 prior to SP1.  Maybe that is something they have changed.

Weird. In my case it was also win7 prior to SP1.

---

