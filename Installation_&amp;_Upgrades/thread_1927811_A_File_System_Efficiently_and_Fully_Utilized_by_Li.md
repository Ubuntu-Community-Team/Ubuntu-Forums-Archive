---
title: "A File System Efficiently and Fully Utilized by Linux and Windows?"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by Wusiki on 2012-02-18
Hello everyone,



I have been plagued by my Windows 7 boot not being able to read from and write to my EXT4 partitions.
I have to reinstall my entire system, and I would like to have Windows and Linux in dual-boot with my data, including "home" and "Users" folders, on partitions that both OS's can read from and write to, separate from the partitions containing the OS's.

Which file system, if any, may be fully utilized by both, Linux and  Windows, just as well as each supports its native file system, without  any practical file size limitations or excessive CPU requirements?
I have tested NTFS using a flash drive, and it appears that Linux has no problem writing and reading +4GB files to/from it (unlike the limitation of FAT32). However, I keep hearing that Linux does not like NTFS. What are those weaknesses I keep hearing about, if they still exist? If they still exist, would poor performance result from the "home" folder being placed on a NTFS file system?

Thank you!

---

### Post by darkod on 2012-02-18
As far as I know, Home (or /home) needs to be on linux filesystem. It can't be on ntfs.

Aside from that, you just need a ntfs partition that will serve as common data partition.

You can keep My Documents on C:, and the linux Home on linux. But I don't think you can do full integration if that's what you want. For example you can place the Firefox profile on the data partition and both OSs can use the same profile, etc. But not all is equal in windows and ubuntu so having centralized location for everything is virtually impossible.

For example I have different Documents folders, but all main data like videos, photos, movies, music, etc are on a ntfs data partition and accessible from both OSs.

---

### Post by Wusiki on 2012-02-18
I appreciate your reply. :)

I know that all my data could not be integrated; accessibility is the goal, which would be as you described:
> ...all main data like videos, photos, movies, music, etc are on a ntfs data partition and accessible from both OSs.

As much as I would like to have all of my profile data on the same partition for easy backing up and to have my linux profile data accessible to Windows, I could compromise. Because NTFS does not support Linux file permissions, I had concerns of whether or not I could put the "home" folder on a NFTS file system. (not to mention security concerns from allowing any Windows user to access all Linux user information easily.)

I will probably resort to backing up individual profile information on a file basis rather than partition image.

Thanks again.

---

### Post by oldfred on 2012-02-19
I am like Darko with a shared NTFS partition. But I now use XP so little, most of my new data goes into a shared /data partition.

I aggressively move hidden folders with lots of data like Firefox and Thunderbird out of home into either a NTFS /shared or /data, so my home now is only 1GB. My root is about 7GB and all my data is in /mnt/data(ext3) or /mnt/shared(NTFS).

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by mastablasta on 2012-02-19
> **Wusiki said:**
> Hello everyone,

I have been plagued by my Windows 7 boot not being able to read from and write to my EXT4 partitions.



you can use a separate NTFS parittion for data that bost systems can access.

additionaly there are tools that enable you to read EXT4 and possibly even write on it from windows. not sure about the write there...

---

