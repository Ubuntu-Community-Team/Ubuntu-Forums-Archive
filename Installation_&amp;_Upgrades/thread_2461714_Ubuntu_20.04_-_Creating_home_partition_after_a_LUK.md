---
title: "Ubuntu 20.04 - Creating /home partition after a LUKS installation"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by joe.ess on 2021-05-06
I am getting prepared to install Ubuntu 20.04 in the near future. My understanding is that the installer gives the Full Disk Encryption with LUKS option, which will preclude a "something else" option where a /home partition would be created at installation. I think the default here is to not create a seperate /home partition.......

I know there is no rule that says you must have a home partition, but it is a good idea. I haven't been using linux that long and am trying to learn what I can. Swallowing my pride, I'm concerned that I'm at the stage where mistakes will happen. I never used LUKS and read a little about it and am still trying to wrap my head around it. I have the time to learn these concepts before this installation and don't really know that one even notices LUKS that much in every day operations. It's my hope that I will be able to take advantage of its features as well as the advantages of having a seperate /home partition.......

It seems that I would let the installer do its LUKS installation, then immediately use the installation disk before populating the system to create a home partition by customizing the commands at [https://stephencox.net/blog/install-ubuntu-full-disk-encryption-home-partition.html](https://stephencox.net/blog/install-ubuntu-full-disk-encryption-home-partition.html) Do those commands make sense? (I didn't understand parts of it). Is there an easier way like a GUI interface? (My understanding is that Gparted cannot do these LUKS operations).I am open-minded to any alternatives.....

Any guidance would be greatly appreciated.

---

### Post by TheFu on 2021-05-06
You should know that the installer with LUKS encryption will also include LVM, so you'll need to learn that as well. LVM is a "Logical Volume Manager", so a single partition will be created and LVM objects will be placed inside that partition.  LVM is very powerful.  You probably won't deal with partitions much.  File systems and mount devices aren't using partitions under LVM. They use LVs, logical volumes.  Almost always, these can be thought of as really, really, flexible partitions, but we can change the size while the system keeps running sometimes.

The trick for LVM is to NOT allocate all the storage to LVs. Only allocate about 3 months of storage to each LV.  Increasing an LV size is 5 seconds of effort.  Reducing the size of an LV is 10 minutes, requires downtime (usually) and some file systems don't support reducing size at all.

To my knowledge, no GUI tools exist for LUKS setup or management.
To my knowledge, no GUI tools exist for LVM setup or management.
There is good news from this lack of GUIs.  That means almost any tutorial you find for either LUKS or LVM online, regardless of the distro, will be accurate.  LVM is LVM regardless of RHEL, Arch, Gentoo, Ubuntu, SuSE, Debian, or some other funky Linux distro. They are all the same. Find a tutorial, create a PV onto a partition, create a VG inside the PV, then create 3-10 small LVs, being certain to never use more storage than needed for the next 3 months and avoid using more than 80% of the storage for any SSD to increase the lifespan.  

You should plan on any modifications being done at a shell prompt.  For someone really new, I'd assume multiple mistakes will happen and data loss will occur.

When we are just learning, expect to make mistakes and need to reinstall 3-20 times.  Like anything else, practice makes perfect. Some LVM and perhaps LUKS posts:
[LIST]
[*][https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)
[*][https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
[*][https://ubuntuforums.org/showthread.php?t=2422831&p=13875938#post13875938](https://ubuntuforums.org/showthread.php?t=2422831&p=13875938#post13875938)
[/LIST]

LUKS does add a little overhead, perhaps 3%. It can be higher for systems with CPUs that don't have crypt support instructions built-in. In general, the only time I notice LUKS is at boot, when I have to use my Yubikey to unlock the storage before it will boot the OS.  I have 3 different unlock codes.  2 from 2 different Yubikey devices and one really, really, really, long, complex, not-sure-I-could-type-it passphrase. I dint' want to be locked out if one of the yubikeys is lost or stolen.  My LUKS unlock uses a challenge/response method, so someone else won't be able to crack into my system if they have one of my yubikeys.  Their answer to the challenge would produce the wrong response.

When learning LVM, I found it best to have a normal install inside a virtual machine, but to have 2 virtual-HDDs connected - one without LVM and the other with LVM.  Then I could learn about PVs, VGs, and LVs, in an environment that wouldn't lead to data loss.

Why do we not allocate all the storage to LVs?  Because LVM provides snapshoting, which is awesome for backups and before doing high risk changes, but every time we create a snapshot, more storage will be used to freeze all the current blocks on the LV being snapshot-ted.  This is a temporary increase, until we delete the snapshot. If there isn't empty storage to hold all the changed data, then snapshots can't be created and other less than ideal stuff can happen or be unavailable.

Sorry that I spend so much time on LVM, but that's the main thing you'll deal with post install after the LUKS stuff. We really don't change LUKS post-install, except to add more unlock codes/modes. There are 8 unlock slots for each LUKS encryption container. That can mean 1 per person, 1 for the company, or all sorts of combinations.  The unlock codes don't modify the encryption used on the entire disk, just the header. It is really brilliant.

---

### Post by joe.ess on 2021-05-07
> **TheFu said:**
> almost any tutorial you find for either LUKS or LVM online, regardless of the distro, will be accurate.   [indent]    I have concerns about the accuracy of [https://stephencox.net/blog/install-ubuntu-full-disk-encryption-home-partition.html](https://stephencox.net/blog/install-ubuntu-full-disk-encryption-home-partition.html) because it reflects what I'm looking to do, though not in Ubuntu 18.04. I'm not saying it's necessarily wrong; I just need help digesting what it's purporting to do. Based on TheFu's links, I'd like to partition 150 GB to home (possibly less as TheFu's advice would suggest) out of a single 1000 GB drive.[br][br] [indent]    lsblk & lvs commands could give me some sense of how that link's partitions & volume group NAMES apply to my situation.[br][br] [indent]    I don't understand a lot of that link's approach and am afraid to apply it as being gospel, so I guess I'm looking for the particular commands (substituting the NAMES involved) to simply "let the Ubuntu installer do it’s thing and then resize the root partition and add a home partition afterwards" using the install medium.[br][br] [indent]    From what very little I know, I noticed a few things about that link's approach: ...First it's decrypted & mounted, then he does an e2fsck integrity check. But "man e2fsck" says: [br][br] [indent]    Note that in general it is not safe to run e2fsck on  mounted  filesys&#8208;       tems.  The only exception is if the -n option is specified, and -c, -l,       or -L options are not specified.   However, even if it is  safe  to  do       so,  the  results  printed by e2fsck are not valid if the filesystem is       mounted.[br][br] [indent]    Then to resize the root LVM partition he uses resize2fs & lvreduce (to a specific size). But "man resize2fs" says: [br][br] [indent]     It can  be  used  to enlarge or shrink an unmounted file system located on       device.  If the filesystem is mounted, it can be  used  to  expand  the       size of the mounted filesystem.[br][br] [indent]    However, isn't it mounted in this case, so I thought resize2fs cannot be used to shrink in the case of mounted.[br][br] [indent]    "man resize2fs" says:       The  size parameter specifies the requested new size of the filesystem.       If no units are specified, the units of the size parameter shall be the filesystem blocksize of the filesystem...That link commands first specify 90 GB for the resize2fs on the file system, followed by lvreduce to a specific 100 GB on the filesystem, then he uses resize2fs with no units specified, so it would end up being the filesystem blocksize of the filesystem per the above "man resize2fs" quote.[br][br] [indent]    ONE OF the things I'm confused about is how these resize2fs & lvreduce commands hang together in reducing the size of the root partition...Their "create home partition seems okay with me, but along with The Fu's advice & what I'm trying to do I would use: [br][br] [indent]    "sudo lvcreate -n home -L150G ubuntu--vg" to end up with a large 150 GB home [could be less] (instead of "sudo lvcreate -n home -l 100%FREE ubuntu--vg").[br][br]  [indent]   Finally he moves home from root to new partition, edits the etc/fstab file, unmounts & reboots. (sounds reasonable).[br][br] [indent]    I'm reluctant to put blind faith in that link's instructions because of this lack of understanding. Does somebody have a better link or an easier way, or would I just be okay following along with that link's instructions?[br][br][indent]     Any help would be appreciated...PS: Please don't laugh at my trouble spacing paragraphs & BB code, but I needed to get this posted. Tell me what I did wrong & I'll edit out the distracting [br][indent] nonsense to get this into legible paragraphs.

---

### Post by joe.ess on 2021-05-08
I FOUND [https://askubuntu.com/questions/1017945/lvm-hard-disk-partitioning-after-ubuntu-installation](https://askubuntu.com/questions/1017945/lvm-hard-disk-partitioning-after-ubuntu-installation) FINALLY......Also I read somewhere there are 6 steps to reducing an LVM: 1)unmount the file system for reducing.2)Check the file system after unmount.3)Reduce the file system.4)Reduce the Logical Volume size than Current size.5)Recheck the file system for error.6)Remount the file-system back to stage.

---

