---
title: "NTFS hard drives do not recognize"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Pav3 on 2011-01-31
I've transferred two hard drives from another computer running Ubuntu 10.10 and they are not being recognized.

At one point, they were used in a raid but I've since unraided them by using them as separate drives.  

 using blkid, I found that the drives dont have UUID's but raid configs:


/dev/sde: TYPE="promise_fasttrack_raid_member" 
/dev/sda: TYPE="promise_fasttrack_raid_member" 

Gparted shows them as NTFS-3g, but I do not know how to switch them so they can be recognized as those drives. 

How do I get Ubuntu to recognize them as NTFS drives so I can put them into my media folder?

---

### Post by ronparent on 2011-02-02
Since the drives are no longer being used as raid, you have to explicitly erase raid meta data when they were raided. In a terminal write 'sudo dmraid -E /dev/sdx' where 'x' is the drive designation for each of the drives. For good measure you can afterwards 'sudo apt-get purge dmraid' but not absolutely necessary. The drives should now have reverted to their native state.

---

### Post by srs5694 on 2011-02-02
If you want to copy data from the drives, as it sounds like you do, you should *not* do as ronparent suggests. If you want to copy data, then you'll have to either use the original computer to read the data and transfer it to another disk or you'll need to get the new computer to recognize the RAID layout. The latter might not be possible if the first disk used a true hardware RAID configuration, at least not without moving the hardware RAID controller you used to control the drives to the new computer; those configurations are set up in the hardware RAID controller, and AFAIK Linux can't read them except via the hardware RAID controller used to manage the RAID setup, or a compatible model. If it was a motherboard software RAID (sometimes called "fake RAID") setup, you might be able to get it to work using Linux's RAID tools, but I'm not an expert on this, so I can't offer much in the way of suggestions. You might look for device files of the form /dev/md#, though, where # is a number from 0 up; or /dev/mapper/*, where * is anything except "control". If such a file exists, it might refer to the RAID volume(s) on the disks, assuming the computer doesn't have its own RAID (or LVM for /dev/mapper) setup.

If, however, you just want to use the disks as blank disks and don't care about any data they contain, then ronparent's suggestion sounds good to me.

If you need more help, I recommend you post additional information on how the RAID setup was created (software and hardware) and precisely what you intend to do with the disks.

---

### Post by Pav3 on 2011-02-02
"sudo dmraid -E /dev/sde1" did not work for me.  It gave me the 


ERROR: option missing/invalid option combination with -E

I wasn't sure to write sde or sde1 since gparted shows one of drives as "sde1", so I tried both.  /dev/sda (which is the other drive) gave me the same error. 

Originally, I used the drives as storage on a fake raid1 setup for a computer using windows vista.  Eventually, I got interested in using Ubuntu only to find out later that I cannot dual-boot windows and linux on a fakeraid setup.  I then dual-booted and switched off raid from my motherboard's BIOS. Both unraided drives worked fine under windows and ubuntu at that point. 

I have an extra computer only running 10.10 and decided to transfer those two drives from the other computer over assuming that ubuntu would recognize them, but it didn't.  The purpose of those two drives which had been already formatted to NTFS is for storage.

---

### Post by Quackers on 2011-02-02
If you've read srs5694's comments and still want to go ahead, you could try ```
sudo dmraid -rE /dev/sda
``` and then run it again for the other drive (/dev/sde, I believe).

---

### Post by Pav3 on 2011-02-02
sudo dmraid -rE  solved the issue.

thanks ronparent, srs5694, quackers

---

