---
title: "Resizing '/' partition ( again ) ?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by m.letcher on 2008-11-01
Am I looking at a full install/update in order to adjust partition sizes  ??

I apologize in advance for a 'standard question', but would appreciate some experienced advice as there's probably an easy way to address this that I'm not considering.

Short Description: I set '/' part at 10 GB and /home at 35 GB. '/' is already at 80% full and I now realize I should have made it 20 or 25 GB as I don't really need all 35 GB in /home ( 15 GB min is probably OK actually ).

Am I looking at a full install/update following another re-partitioning ??


System: Dual boot Vista32/Hardy 2 internal/1 external drives, HPm8120n/Q6600/3 GB, NV8800GT, dual monitor,etc.

History: I'm in the process of updating to 8.10. After finishing the qrtrly Vista BU, I decided to adjust my Ubuntu partioning as part of the move to 8.10. So, I broke the 50 GB's for Ubuntu on the primary internal drv from 40/10 ('/',/swap) to 10/35/5 ( '/',/home, swap ) leaving plenty of room for more users and some more apps and personal kernel compiling experiments. Having run Linux in less than 2 GB partitions before ( way back when - needless to say ), 10 GB seemed plenty but hind-sight says no with all the new app's ( Office/Studio, etc ). My current target is 23/20/7 ('/',/home,swap ) but I'd like to avoid a complete re-installation. My live-CD's are for Feisty which then soak the network for updates ( which I'll be fixing this time ). I've been focused on getting Studio working with my HW and learning its tools and sadly neglected routine maintenance due to time constraints.My bad! But re-installs used to be pretty easy - a half day or so at worst.

Options:
1) Good - Dynamically adjust partitions. I've been using Vista to adjust part's to not hose Vista by doing it from Ubuntu. Vista doesn't let me do this either without data loss except occasionally for its own parts, but its part's are bigger and more troublesome. PartitionMagic,etc used to do this sort of thing, but I don't see a similar option for or within Ubuntu yet for even its own spaces. I might be able to copy /home dir into a tmp dir on '/' and its partition ( since it's still small ), delete '/home' part and resize the part's, but I'm pretty sure there will be problems particularly re-sizing swap or trashing '/'.

2) Bad - BU & re-install. Let 8.10 install, BU ( sbackup ?) everything to the ext drv ( I've got an unformatted 50 GB partition for Ubuntu reserved but still unused ), so it would need a format, etc. Then boot from CD into Feisty, restore to newly re-sized and re-formatted part's and see if GRUB is still happy and Vista didn't blow up again.

3) Ugly - Start over. Re-part in Vista, re-install Feisty, re-update, etc.

4) Magic - Mount /usr,/bin,/var, etc ( as needed ) onto the /home part but not dir. I suspect this can be done with a copy onto sda5 '/home' part ( sda3 is Vista's Recovery at end of vol though '/' is sda2 ) but I haven't worked through all the details.

5) Cash - Buy another external drv for the personal media bay ( I'm running short of USB's even with 2 hubs already ) dedicated to Ubuntu. But I'm not sure how GRUB handles an external boot drv which may or may not be present and don't really need more than the terabyte total I've already got and would still need the 10 GB NTFS part for sharing files with Vista ( sounds, graphics, video, etc ) on the 2nd internal drive.

Sorry for the length of the post, but this probably comes up frequently and will again in the future. I did search these and other forums and google around but didn't find anything that wasn't going to take a couple days to understand/implement. WUBI doesn't have these kinds of problems that I can see so far since its basically a handy toy, but I expect similar issues as I get Vista into a VirtualBox on Ubuntu ( I need drivers that aren't Ubuntu supported yet - midi,audio,etc). Ubuntu is already in a Vista VirtualBox unfortunately driver sharing is problematic.

Thanks in advance for any suggestions or help.

---

### Post by caljohnsmith on 2008-11-01
You should be able to just resize your Ubuntu partitions as you want to using the Ubuntu partition editor gparted from the Live CD. It's important to do it from the Live CD so that the partitions won't be mounted. You can access the partition editor via System > Admin > Partition Editor, and then in gparted you'll probably need to right-click on the swap partition on your HDD and select "swapoff". Then you can resize your partitions.

Afterwards, you'll most likely need to modify your /boot/grub/menu.lst, and also your /etc/fstab in order to boot into Ubuntu, because the UUIDs for Ubuntu partitions will change with the resizing. I can help you with that if you need specific instructions; but go ahead and resize your partitions first, and we can work from there. :)

---

### Post by m.letcher on 2008-11-05
Thanks for suggestions. I'm not in a big hurry yet. GParted seems like the way to go. I did find a little more info but its basically your path. I'll need to do the backup and make a new live-CD but thats overdue anyway.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by m.letcher on 2008-11-06
UUID errors now -- as you mentioned.

Ok, Gparted worked fine. Took a couple attempts to work around the extended partition, but joy eventually. It kept all files on '/' as well ( so it preserved some of the older RT kernels). GRUB seems happy as I didn't move the '/' partition - just extended it. I still need to clean up menu.lst but thats trivial. And Vista didn't throw fits. I did appear to lose the files on old /home partition but it may just not be getting mounted probably as it does show a 1/2 GB being used. Upon boot from the HDD, fsck does terminate with some UUID errors so I could use some help with that. I haven't tried a umount/mount cycle yet for the new partition but it shows up in fstab. I made a new liveCD for 8.10 so I can boot from it or the HDD though X and gdm stop with fsck, though they'll probably start as well if I just complete the boot manually and it remembered my old login/pwd. I can probably be fully recovered from the liveCD with a little advice. Oddly, I didn't appear to have any NVidia issues discussed elsewhere from the liveCD, so 8.10 still looks real clean to me though I didn't try to enable 3D effects. I'll start googling UUID's and see what I can learn.

---

### Post by caljohnsmith on 2008-11-06
From your Live CD, how about posting:
```
sudo fdisk -lu
```
And then for your Ubuntu partition, try:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with your Ubuntu partition; post the output of that as well.

---

### Post by m.letcher on 2008-11-07
I found a link on adjusting the UUID and got the 2nd partition mounted after using blkid and updating fstab from the liveCD. The UUID was new to me, but if it helps with removable storage so be it.

[http://onlyubuntu.blogspot.com/2008/10/some-tips-for-correcting-uuids-in.html](http://onlyubuntu.blogspot.com/2008/10/some-tips-for-correcting-uuids-in.html) ( there's better links for this )

[http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)

However, I then got the .ICEauthority and .dmrc problems mentioned in the earlier msg. So, I decided to just do a clean install on the new partitions. Joy, for a while anyway.

Today, I'm looking into the NVidia drivers which have problems transitioning to the restricted driver set. I've got a followup with Launchpad outstanding now as apparently this isn't too unusual.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/283747](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/283747)

I may do another re-install, and just not mess with the NVidia drivers since the install drivers seemed to work OK. While the acceleration 'flash' is nice it isn't necessary. Next is to start looking into Jack/Studio and see if I can get the MIDI up.

Thanks for your interest and help!

Closed and moving forward

---

