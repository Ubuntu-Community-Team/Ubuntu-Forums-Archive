---
title: "Can't boot linux after installing xp"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by sylvester.a on 2011-03-07
Hello everyone.

A few weeks ago, I installed xp because I needed microsoft flight simulator x and them suddenly I wasn't able to get in to ubuntu.
When I was installing xp, I had about 100 GB free space  of 150GB so I created a ntfs partition (on the free space) for xp and since them I can't get to ubuntu and I know it's there in the hard drive.

Can anybody please help me with this?

Please take a look to the pic attached.
[IMG]file:///C:/Documents%20and%20Settings/Silvestre/Desktop/Computer%20Management.JPG[/IMG]
Thank you,
Sylvester

---

### Post by ajgreeny on 2011-03-07
You need to restorer grub using your ubuntu (edubuntu) live CD.  See the enrties for grub2 in my signature and you will find how to do it in about three or four commands.

---

### Post by Sean Moran on 2011-03-07
By the look of the listing in the picture, you have a 42GB partition that is not being used for anything.  The second one on the list.

Win XP will wipe out GRUB, but ext2,ext3,ext4 partitions are not recognised, so everything should still be there.

Install Ubuntu on that 42GB drive, to fix things up, and the installer will replace GRUB and recognise itself, as well as the windows and linux systems on the othert partitions.

You might also want to split that 42GB space up a little, because Ubuntu only needs 4GB, and is happy with 8, and obese at 16Gb, but just to get the GRUB back again, just install somnething Ubuntu on the 42GB partition that uis currently unused.

Do it offline and it will only take 10 minutes or so.

---

### Post by sylvester.a on 2011-03-07
Thank you for your help.

I do have lot of important files in Ubuntu an XP, if I do what you advising me to do am I gonna lose any of the files that I've got in both OS?
It's really important to keep the my personal files in both system as I don't have any backup at all.

Thank you once again.

---

### Post by Sean Moran on 2011-03-07
> **sylvester.a said:**
> Thank you for your help.

I do have lot of important files in Ubuntu an XP, if I do what you advising me to do am I gonna lose any of the files that I've got in both OS?
It's really important to keep the my personal files in both system as I don't have any backup at all.

Thank you once again.

Best advice is to copy everything important to a DVD or USB flash drive first - your data is worth much more than any operating system.  

IF YOU HAVE THE TIME, COPY EVERYTHING of YOUR DATA to DVD or USB FLASH!

Either way, that 42Gb partition showed 100% free.  If you can see it and make sure it is as free as the picture told me it is, then there is no important data on that partition - it's 42GB empty.

From here, the only danger of losing anything is user error.  If you make a mistake.

You can install Ubuntu on that free 42GB partition if you select MANUAL partitioning (Advanced) when you do the installation.  Make sure to set THAT partitiion to EXT4, and the mountpoijnt to root (/), and I can't find the image in the midst of a reply, but make sure there is somewhere for SWAP space (you probably have already).  

Just be careful.  That 42GB of space looks to be free to delete and change and resize and anything. You can create the room to install Ubuntu with a root partition (/) and 1 or 2 GB partitiion for SWAP within that partition.  Be careful, but remember to always install Windows XP first in future, and then install Ubuntu.  Windows XP is very antisocial.

---

### Post by ajgreeny on 2011-03-07
**I hope I am not too late, but whatever you do, ****do not delete that 42GB partition.**  I suspect it is the ubuntu root partition, which Windows does not see at all, hence saying it is healthy, but unknown.

Simply do what i said in post 2 and you should be able to get your grub bootloader back again without a problem.

**Boot to your live CD/USB** and I think you will find that the supposedly empty partitions actually contain your Ubuntu files and folders.  The disk management utility of windows is worse than useless when dealing with linux partitions, as it can not recognise them at all, and can easily confuse people into deleting partitions that appear to be empty but are not.

---

