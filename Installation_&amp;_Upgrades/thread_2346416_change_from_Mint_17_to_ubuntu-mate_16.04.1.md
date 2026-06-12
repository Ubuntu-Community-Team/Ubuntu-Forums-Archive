---
title: "change from Mint 17 to ubuntu-mate 16.04.1"
date: 2016-12-14
forum: Installation &amp; Upgrades
---

### Post by sam1951 on 2016-12-14
I would like to try Ubuntu 16.04.1 on one of my computers. Presently it boots Windows 7 & Linux mint 17. I have done some installations alongside Windows
before but it has been a while so I'm looking for a little help in advance. I've gotten the important stuff off the Linux partition but I want to make sure I don't harm
the Windows 7 stuff. Anyway, here is the plan:
1.) boot from a Gparted live CD and delete the extended partition (presently /dev/sda3) containing Mint. That would also get rid of swap (dev/sda6).
     Leave that newly created space unallocated.
2.) eject the Gparted CD, insert the Ubuntu 16.04.1 CD and reboot.
3.) there should be an option like "install Ubuntu alongside windows". It should install Ubuntu to the unallocated space, create a swap there and re-do grub
     so the new boot menu can boot Windows or Ubuntu.

Will the install CD create an extended partition for Ubuntu like it is for Mint now? I don't plan any more partitions on this disk since it's only 500G. System reserved,Windows7
and Ubuntu with swap would be 4 but I would rather the disk structure is the same as it is now. Just being a little obsessive, compulsive with that.

BTW just an aside, where did /dev/sda4 go ? Anybody see anything that will cause problems here? I tried to upload a screenshot but not sure it worked

Thanks in advance to any who can help

---

### Post by oldfred on 2016-12-14
Best to backup Windows also. You should have it backed up anyway.

Primary partitions are sda1 thru sda4, but you have only used 3, so sda4 is available.
Logical partitions always start at sda5, even if you made sda1 the extended then you would only use one primary and logical still starts at sda5.

You do not have to delete extended & logical partitions, if you want essentially the same size / (root) and swap.
Just use Something Else, choose(change) existing / as new / and reformat.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by sam1951 on 2016-12-14
Ok, so I don't need the Gparted CD. Choose "something else" instead of "install alongside" and the installer will allow me to choose
sda3 for Ubuntu 16 and swap ? Ubuntu 16 does not need unallocated space to install to?  It will just overwrite the Mint files and install
there? Device for bootloader installation will be /sda and it will put new the new grub files where the old ones are?
 I think I remember something from before about choosing only /sda for the bootloader. So at the end I have 3 primary partitions. System
reserved (sda1), Win 7 (sda2) and extended (sda3) containing Ubuntu (sda5) and swap (sda6) just like it is now but with Ubuntu swapped
for Mint?

---

### Post by oldfred on 2016-12-14
With Something Else that should work.

If you tick/check the format option on sda5, that will erase sda5 before installing Ubuntu.
And you normally install grub to drive's MBR or specify sda, not a partition like sda5.

---

### Post by sam1951 on 2016-12-15
Ok that sounds reasonably easy ---
/sda5 will be formatted to (ext4 I presume) erasing Mint and making space for Ubuntu
/sda6 is already there as swap so it will be left as is, or option to recreate as is
specifying only the drive (/sda) and not a partition (/sdxy) will put grub where it needs to be

I found some other suggestions poking around these forums

 1.) let windows check it's partition for errors
 2.) have only mouse, keyboard, display and printer connected during the install
 3.) use your Ethernet connection for connecting to the internet
 4.) try Ubuntu from the CD before the install to make sure your hardware will work

So the disk will have 2 primary and 1 extended partition. If I wanted to add another internal disk the Windows installation could use it.

Thanks oldfred, I will try this soon

---

