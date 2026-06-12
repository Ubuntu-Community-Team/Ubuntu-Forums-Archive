---
title: "Pre-existing partitions"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by stratprof on 2009-11-21
Hello, all.

I ran UNR on my Acer Aspire One (ZG5) without a problem.

Updating to 9.10 was my first Linux upgrade and I did so on the first day it was available. I didn't realize, though, that the upgrade would be the "full" Ubuntu.

My system began slowing down significantly. Firefox became unusable. Rebooting would give only temporary respite.

I discovered that Xubuntu could be installed through Synaptic. The transformation went without a hitch. Overall performance seems to be much improved.

I'm wondering, though, if I should go through the hassles of removing Xubuntu and install UNR.

I'd welcome some forum advice.

Thank you in advance!

---

### Post by T1Oracle on 2009-11-22
As long as you keep your /home folder replacing Xubuntu with UNR should not result in any lost files.  You may lose some programs but you will end up with a faster system with a GUI that is more suited to the screen dimensions of a netbook.

UNR is really good especially 9.10.

---

### Post by stratprof on 2009-11-22
Thank you. I will follow your advice re moving to UNR but have one related question. (It pertains to the title of this thread.)

I'm coming from the Windows world: disks with no partitions and installations overwriting pre-existing information.

I'm still a bit "challenged" when it comes to updating the system but I've concluded things don't work in the Windows-way. Here's the process that I think I need to employ:

[LIST=1]
[*]Delete the existing Linux partition with gparted (keeping the Windows partition untouched on the hard drive)
[*]Launch the UNR installation process and, when presented with the option, let the new partition be installed "side-by-side."
[*]Specify, if needed, that the size of the new partition should be the same size as the deleted partition.
[/LIST]
This should create a UNR partition where the current Xubuntu resides. Right? 

Am I missing an easier or more effective way?

Again, many thanks for your input.

---

### Post by darkod on 2009-11-22
Since you already have linux partitions in place, and if you are happy with their sizes, do not delete the linux partitions first.

I understand you are new to all this but don't be afraid. It doesn't bite. :)

The instructions might sound complicated but once you have the screen in front of you, you'll manage it, trust me:

1. Boot with UNR and selecting Install Ubuntu option.
2. In step 4, when asked where to install, select Manual Partitioning.
3. The partition management will open listing all partitions on the drive.
4. First select the partition that was your / and click the Change button at bottom.
5. By default there will be selection Do Not Use Partition. Change that to the filesystem you want to use, recommended ext4.
6. Tick the Format box.
7. Select the mount point as /.

That's it. Do the same procedure for your swap partition. Note that swap doesn't have format box, not needed.

If you have separate /home partition do the same, mount point this time is of course /home, BUT if you want to KEEP your current files in /home do NOT select format. If you want everything gone from /home too, format it.

That's it. If at any moment you get confused with the process just click Quit and it will quit the installer without any damage to the system.

PS. And since you are replacing your system you might want to check out Ubuntu Desktop 32bit instead of UNR. I have a netbook and haven't used ubuntu before. I went for UNR automatically because it is netbook version but I hated the menu layout. Two days later installed desktop 32bit over it. It doesn't work slow at all. The good thing about the Try Ubuntu option is that you can see how it looks. Unless you are aware of the difference already. UNR looks quite different as menu layout compared to desktop.

---

### Post by stratprof on 2009-11-22
Some guidance into a process that I've found utterly mystifying! Thank you!!

To make sure I don't mess up, I'd like to share the disk structure with you. 

The disk identifies the following partitions:
/dev/sda
/dev/sda1 fat32
/dev/sda2 ntfs
/dev/sda5 ext3
/dev/sda6 swap

sda1 is the recovery partition for XP. (I've sadly needed to access it when I first fumbled with Ubuntu installations and reinstallations. The disk got terribly messed up.)

sda2 is the XP partition.

sda5 is Ubuntu (the one I want to change to UNR)

sda6 is, as the name indicates, the swap.

Your advice said: "First select the partition that was your / and click the Change button at bottom"   This newbie's question is: which is my /  ?? 

[When I look at the partition table, none of the partitions has a mount point entry. I followed your clear instructions, steps 5 thru 7, using sda5 as the one to modify. The process that I started entered / as the mount point for sda5. I didn't complete the process, though, as double-checking with you seems to be a wise precaution.]

Was I about successfully modify the Linux partition? Or was I about to trash the whole disk -- for what would be the third or fourth time in its short history?

Thank you once again for your assistance. I'm truly grateful.

---

### Post by darkod on 2009-11-22
You were right, sda5 is / (root), or in windows terms, C:.

Click on the Change button, change the Do Not Use (maybe it's put for protection from mistakes) to ext4, tick format, and select the new mount point the same as old one, /.

For sda6 also click Change. Change the Do Not Use into swap area, there is no format box, and mount point is swap.

That's it.

---

### Post by stratprof on 2009-11-22
It worked! Perfectly!!

If the process you shared with me is documented anywhere else, I've never found it. 

You saved me tons of grief. Thank you!!!

---

### Post by darkod on 2009-11-22
No problem. Enjoy it.

PS. You can mark your own thread as Solved looking above the first post there is Thread Tools. You can do it there. It's helpful for others.

---

### Post by stratprof on 2009-11-22
Done. Thank you once again.

---

