---
title: "Ubuntu 12.04 ALTERNATE Raid 0/Partitioning/Grub Issue"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by Rep99099 on 2012-05-06
Hi I have Windows 7 on a Raid 0 setup. I had two 75gb raptor drives lying around and decided I'd raid 0 them and put ubuntu on them. I successfully had ubuntu 11.04 running on this setup without any issues. I decided to wipe it out and do a clean install of 12.04 64bit. 

I create my raid 0 array with bios which I guess is 'fakeraid' and began installing ubuntu, it asks for the raid detection. i say yes and it detects my raid array (isw_hggiefegf_Seconday_Ubuntu) I then create 2 partitions, 138GB ext4 mount / for the os install (isw_hggiefegf_SecondaryUbuntu1), then another partition, 10GB for swap (isw_hggiefegf_SecondaryUbuntu2).

Install begins, and when asking to install Grub I give it location: /dev/mapper/isw_hggiefegf_SecondaryUbuntu (ive also tried installing grub to the ubuntu1 partition which yields the same result), it installs and installation completes. When it reboots i dont get the grub loader screen but a Grub Rescue thing. i can restore win7 bootloader then hit f8 ad boot into ubuntu where everything seems functional but nothing from software enter will seem to install.

It kinda makes me think the raid 0 setup is messed up and causing all kids of problems.

Do i need to setup SoftwareRaid within the ubuntu installer? if i do this do i need to create my raid0 array in bios or leave them as individual drives then set them up in ubuntu?

Keep in mind my win7 and ubuntu are o seperate raid 0 arrays.

Ive been a this almost all day yesterday. Ive done alot of googling and searching on here but m internet is being slow this weekend which makes things frustrating.

---

### Post by darkod on 2012-05-06
If they are on separate arrays, swraid is a much better option. Gon into the raid bios and destroy (delete) the array. Set the sata mode to AHCI for these disks. Not sure if you would still need to kill the meta data from live mode:
sudo dmraid -E -r /dev/sdX
sudo dmraid -E -r /dev/sdY

After that all fakeraid data is gone. Be careful to use it on the correct disks.

Fire up the alternate installer and create your raid. Note that I think you need separate /boot partition outside of the array if using raid0. I guess that is because it doesn't like the boot files being split on the disks. So, you can have a raid1 array for /boot, or not even an array, just a partition on one of the disks.

---

### Post by cmont899 on 2012-05-06
If doing fake-raid you may want to consider using software raid in the installer or using LVM, you will have more control from the OS than with most fake-raid controllers.

---

### Post by Rep99099 on 2012-05-06
cant set sata option to ahci for certain disks, either all ahve to be raid or ahci :/

---

### Post by darkod on 2012-05-06
Someone else mentioned that too, and that there was another option called Raid Ready that makes the disk connected to that port same as AHCI while the others remain in raid.

Can you set something like that for those two ports?

Otherwise, refer to the board manual. There has to be a way. Maybe just some of the ports are raid capable. In that case, even if for them you have raid selected, disks in other ports will be none-raid.

---

