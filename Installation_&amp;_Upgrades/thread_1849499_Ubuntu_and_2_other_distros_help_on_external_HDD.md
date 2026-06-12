---
title: "Ubuntu and 2 other distros help on external HDD"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by Jack_Coleman on 2011-09-24
Hi, i recently ordered a Seagate Expansion 750gb USB 3.0 hard drive and i want to put 3 distros on it, Ubuntu, Fedora, and OpenSuSe. i want to put them on the Drive because i go to many different computers and i would like to not have to use windows.

What i want basically is for the 3 distros to share my /home folder. (like sda1 is boot, sda2 is swap, sda3 is home, and then the others are the distros)

Anyway i want to have the hard drive contain the 3 distros and then an extra partition with a couple hundred gigs extra for other files, is it possible to have the extra partition in FAT32 and the linux ones in ext4 so i can see the extra one in windows. also im not sure how to make it use one bootloader.

Any help?

---

### Post by mejo on 2011-09-24
> **Jack_Coleman said:**
> Hi, i recently ordered a Seagate Expansion 750gb USB 3.0 hard drive and i want to put 3 distros on it, Ubuntu, Fedora, and OpenSuSe. i want to put them on the Drive because i go to many different computers and i would like to not have to use windows.

What i want basically is for the 3 distros to share my /home folder. (like sda1 is boot, sda2 is swap, sda3 is home, and then the others are the distros)

Anyway i want to have the hard drive contain the 3 distros and then an extra partition with a couple hundred gigs extra for other files, is it possible to have the extra partition in FAT32 and the linux ones in ext4 so i can see the extra one in windows. also im not sure how to make it use one bootloader.

Any help?

Hey Jack,

If you really want to install three different Linux distributions in parallel - I don't get why you would want to do that - then you should create a single partition for every one of them. In case you want to share your /home folder, you need a fourth one. I suggest that you give at least 15 GB to each system partition, and the rest to the home partition. Maybe you want to use lvm instead, which supports logical volumes, and these can be resized more easily.

I wouldn't use FAT32 as fstype for your home folder. It might lead to problems, as FAT doesn't support file owner and privilege settings on filesystem level.

The bootloader is no problem. You should install into the master boot record (MBR) of the disk. But don't try to manage the bootloader from more than one systems, it will lead to problems. I suggest that you install and manage the bootloader with your prefered system.

---

### Post by oldfred on 2011-09-24
Welcome to the forums.

While you can have one partition for all the /home users, you have to use different userIDs so they do not conflict. Each distribution uses different versions, config files, and UID/GID settings that add to sharing issues. Often the best is just to use NTFS  for a shared data partition (not /home) as it does not support any permissions or ownership and then can also be shared with your Windows partition. Do not use FAT32 as it cannot have a file over 4GB and does not have a journal so repairs are difficult. Then just keep /home inside each install.

Which ever system you install last will be the last installed to the MBR unless you specify otherwise on where to install the boot loader (grub or grub2). Ubuntu's grub2 includes an os-prober that finds most other installs and lets you boot them. The legacy grub is not so good and you usually have to manually add boot stanzas.

I believe Fedora's default is to install a separate /boot and put the install in a LVM which adds some complications (and some potential flexibility). Some suggest when installing to not check the LVM option.

---

### Post by OpenJacob on 2011-09-24
Unless you are using Unetbootin or another portable bootloader you might have trouble getting the other systems to boot. You can also have a look at thumbdrive Linux and other portable Distros that might work better as a live system.

As for the 3 distros Ubuntu, Fedora, and OpenSuSe you might already know that SuSe and Redhat's Fedora use the same packages (RPM)so it might be a bit redundant to use them both. Also you can install YUM on Ubuntu to get some of your .rpm apps working without a reboot.

I have a portable drive running Debian, Gentoo and Slax for some variation that I use for diagnostics by the way.

---

### Post by garvinrick4 on 2011-09-24
@Jack_Coleman
 Have been there and done that and listen closely to what oldfred says in post #3.
With different UID's was not compatable using same /home. I understand Fedora
16 is going to 1000 UID which is the same as Ubuntu. Enjoy your Ubuntu.

Install Ubuntu first and when installing Fedora and OpenSuse (both have anaconda installer)
choose not to use LVM or [COLOR=Black]do not install grub[/COLOR] at all. When done installing boot back into Ubuntu
and "sudo update-grub and will put in Ubuntu's grub2 (grub-pc) as a menu entry and in config file.
Just always use your Ubuntu install as control over booting. 
Fedora and OpenSuse both use grub legacy as boot loaders and do not play well with the newer and better grub2.
You will have to dist-upgrade Fedora by fresh install if want to go from 15 to 16 or 16 to 17 because as oldfred stated
it is used to a /boot partition which it also uses to dist-upgrade with. (pain in the rear) 

Keep it simple and clean and all will be fine: UBuntu first, no LVM and grub-legacy at install of other two and not using same /home because of permission problems (different UID's 1000 and 500)

---

### Post by Jack_Coleman on 2011-09-24
ive heard in other places that if i install ubuntu last and use different usernames for each distro i shouldnt have any problems, because ubuntu will overwrite the mbr with grub2 and automatically add the other distros to the list. i also shouldnt have any problems with config files because of different usernames ("jack-suse", "jack-fedora", and "jack-ubuntu"), is this correct? if so, is this how i should do it?

p1: Distro (ext4)
p2: Distro (ext4)
p3: Distro (ext4)
p4: /home (ext4)
p5: Other Data (NTFS)

How do i make them share the same /home, is it a simple settings change?

---

### Post by oldfred on 2011-09-24
You share the partition but not the data since you have different users with different UIDs & GIDs users & groups.

You can install grub legacy to the partition boot sector of the install, if you want for the other distributions. That gives you another way to boot (chain load). Grub2 does not like to be installed to a partition as it is less reliable in a partition boot sector and works best if just in a MBR.

---

