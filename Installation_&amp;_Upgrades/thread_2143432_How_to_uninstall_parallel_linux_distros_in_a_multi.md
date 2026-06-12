---
title: "How to uninstall parallel linux distros in a multiboot environment"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by zuheyr on 2013-05-09
Hello,

I have a multiboot environment with several Windows versions around 12.04, as well as 2 flavors of mint and cinnamon 
which share the same home and have their own / and /boot as shown in the attached figure. 

I would like to:
*)  Remove mint and cinnamon distros, 
*)  Merge those partitions with my home,
*)  and, extend the home with the unallocated space.

Can I do that? Your thoughts please. Many thanks for reading. Kind regards,
Zuheyr

---

### Post by fantab on 2013-05-09
The best thing to do when multibooting with multiple distros is to have only "/" and NO shared /home.

Anyways. You can boot with Ubuntu LiveDVD/USB and 'Try Ubuntu". Open Gparted and Format un-needed install partitions, if you want to delete the partition then just do so. You can resize the /home partition as well.
It is however, recommended that you BACKUP /home partition first. 

Then boot in to Ubuntu and run update-grub.

---

### Post by zuheyr on 2013-05-09
Thank you very much for your prompt reply.

Yes I should not have shared /home but I just wanted to test Mint and was planning to do what I want to do now.

Indeed I simulated to delete those unneeded 4 partitions but it will not of course let me resize /home as I am using the Ubuntu now.
So I have to prepare the LiveUSB and I hope it will let me resize /home then.

It does not let me format the unallocated space saying there are too many primary partitions, so I do not know if I can extend home with an unallocated space?!

Many thanks again for your time.

Kind regards,
Zuheyr

---

### Post by fantab on 2013-05-09
No, you cannot resize partition while it is in use. Using a LiveUSB is the best thing to do. Yes, with 'msdos' partition table you can only have FOUR primary partitions. If you want more then you have make one of the primary partition into Extended and then create Logical partitions within it, like you have done. 

If it is not possibe to create partitions, then, I am afraid, but you may have to delete the Extended partition /dev/sdb4 (which will also delete your Ubuntu install). Then recreate Extended Partition from all the 'unallocated space', then go on and create smaller Logical Partitions. And reinstall Ubuntu.

My suggestion:
/dev/sdb4 Extended (all the unallocated space)
/dev/sdb5   2-4GB SWAP
/dev/sdb6   25GB Logical Ext4 "/" Ubuntu
/dev/sdb7   25GB Logical Ext4 (in case in future you want to install another Ubuntu version or flavor or another distro)
/dev/sdb8   All the remaining GB Ext4 (Simple Linux partition to house your DATA) No Mountpoint.
(We are not creating separate /home. Not having separate /home makes it easier to install and re-install Distros without worrying about DATA Loss).
OR
/dev/sdb8   remaining GB /home ext4.

My two cents...

---

### Post by oldfred on 2013-05-09
I think you should be able to expand the extended partition into the unallocated and then can change partitions at will inside the extended.
You have to click on swap and swap off as live installer mounts swap to speed things up.

If dual booting with Windows, I also suggest a shared NTFS data partition as fantab has suggested for a data partition. I have two data partitions, one NTFS and the other Linux.

---

### Post by zuheyr on 2013-05-11
Dear Fantab and OldFred,

Very sincere thanks to you. Fantab gave me reference material I will use in my all future installs :)
But at the moment I could not dare removing my existing ubuntu. 

So I tried and succeeded to:

*) remove those small partitions with the 13.04 Live DVD, 
*) extend the current home 
but
Oldfred: I could not do anything about the unallocated place as there were 4 primary sections. So 

I removed 1 partition on which there was a test (and silly) Windows8 install. 
And created a new shared NTFS partition out of the unallocated space. 

All fine, *but* my attempts to install 13.04 with unity which I liked very much failed, maybe because of my nvidia graphic card and I marked install proprietary software!?
I do not know, but this is another topic.

So, solved, many sincere thanks, I appreciated your help very much. 

Kind regards, Zuheyr

---

