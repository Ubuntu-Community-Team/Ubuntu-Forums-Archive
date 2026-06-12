---
title: "Vista Ubuntu"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Tlingit on 2007-11-03
Hello,
I have looked everywhere I want to create a separate partition for ubuntu. I am working on dual booting Vista and Ubuntu Till i know Linux as best as i can. If i partition my hard drive can i bring it back to the way it was . I read some were some time the if i formated the hard drive in NTFS that i could not undo it. same with fat32. sence this pc came with Vista the hard drive is NTFS.
Also what format should i format for Ubuntu?
 

This is what i plan to do.

Partition in windows Vista(to the format i find i should use)
Stick the cd in for Ubuntu and install it on the partition? 


Good idea? 

can i put it back to way it was if i do that

---

### Post by cuby on 2007-11-03
Hello!
For Ubuntu, you can create a partition in EXT3. 
While in the live CD (using the GParted program) or during the ubuntu installation (select manual in the disk selection part) you can resize the NTFS partition of vista and create a new one for Ubuntu.
This way, you will have the 2 systems.

As usual, you **should** perform a backup in DVD or in another hard drive, before attempting any of this.

---

### Post by Pumalite on 2007-11-03
With Vista; use the Vista partitioner and set Page File to '0'.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
(return Page File to previous value after installation)

---

### Post by Tlingit on 2007-11-03
Hello,


Pumalite I have been looking at those pages but i was not sure if any of those could be undone. If i format in fat32 will i be able to move back to NTFS if possable. I read that windows cant go back in time to fat 32.

---

### Post by Pumalite on 2007-11-03
After you allocate space with the Vista partitioner, when you install Ubuntu, the installer will format that partition to ext3 mostly (/swap has it's own format)

---

