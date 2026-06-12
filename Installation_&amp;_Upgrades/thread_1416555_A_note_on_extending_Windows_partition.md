---
title: "A note on extending Windows partition"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by kat3c on 2010-02-26
Just thought I'd post a note on how I, temporarily, screwed up my new dual boot install, others might benefit from my newbieness/knuckleheadery.
 
After partioning and fresh installing Windows 7 and Karmic, I decided I should have made the Windows partition larger. No problem, as right next to it I had put an NTFS partition for storing data as the first logical partition of the other extended partion that has Ubuntu. I'll just shrink that.
 
So, I boot to gparted livdCD. Sillly me, I clicked on the data partition, then deleted it. D'oh! I am a newbie, so at the time, I didn't realized that would screw up booting by renumbering the other partitions (what was sda5 was gone, so now what was sda6 became sda5, and so on down the line). Anyway, now I went to extend the Windows partition. But I couldn't. At all. After messing around (mostly staring) for a while, I hit on the fact that you have to shrink the WHOLE extended partion (by shrinking the left hand side to the right) that is right next to the Windows partition to make the unallocated space truly unallocated. Before, it was unallocated but within the extended partition. Now, unallocated space that was not part of any partition was in-between the Windows and the extended partition. 
 
I then could extend the Windows partition using the truly unallocated space. Had to reformat the shrunk data partition back to NTFS as well.
 
Then I quit gparted. On booting, or not booting as it was, I got some kind of "unrecognized files" error, and then just "Grub rescue" with a blinking cursor line. Uh oh. Booting back to the gparted LiveCD showed everything was still there, with the new sizes. After staring at the screen, the renumbering thing hit me, as the first newly shrunk logical partition was now sda8, with sda5 after it. I couldn't figure out how to renumber the partitions, so I just booted to the Ubuntu install USB and reinstalled Ubuntu. Grub reinstalled and used the new numbering configuration. All's well now.
 
So, if you're extending a Windows partition, don't just delete the first partition next to it if it's a logical partition in a multi-partition extended to make it unallocated space, shrink the whole extended partition, and unallocated space after the Windows partition is freed up.

---

