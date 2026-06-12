---
title: "Strange trouble with user folders"
date: 2017-08-26
forum: MINT
---

### Post by jmh72 on 2017-08-26
Hi everyone, I'm having trouble with my user folders. I have four partitions. 1) Win7 2) Mint 18.2 3) Mint 18.2 4) NTFS storage.

What I'm trying to do seems like it should be simple. I want all the user folders to save directly to the 4th partition (NTFS). I changed the location of the user folders in Windows 7 without a hassle, and it still works. The first Mint install on partition 2, I edited user-dirs.dirs and changed $HOME to an absolute path on the NTFS storage partition. That worked... for a while. So now, I have two problems.

1) The changes I made to user-dirs.dirs on partition two do not work upon reboot. Instead of changing the path for those folders, I managed to make them disappear from Nemo, PCmanfm, and Caja all together.
2) The second Mint install on partition 3 would have none of it at all. Changing user-dirs.dirs did absolutely nothing to change the default path of that users folders. Even upon logout and reboot.

Does anyone know what I'm doing wrong? The objective is simple.

I want to designate premade folders on my storage partition as the default location for common user folders such as 'Downloads', 'Documents', 'Music', etc.

So, instead of a path that reads Documents = /home/user/Documents I want it to be Documents = /media/NTFS partition/user/Documents.

As far as I can tell, all the partitions are mounting properly, and all folders on the NTFS partition are RW by every installed OS and user.

---

### Post by ajgreeny on 2017-08-26
I think the best way to achieve what you want is with symbolic links from the Linux OSs to the folders in the NTFS partition; forget about the user-dirs.dirs as that is not the best way to proceed.

You will need to ensure that the NTFS partition is mounted automatically at boot of both Mint OSs to be able to do this or your symbolic links will be broken at boot until you mount the NTFS partition, but even then it may mount to a different mountpoint and cause other difficulties. Using /etc/fstab to automount at boot is the way to go.  Windows will find and use that partition without problem, as far as I'm aware; I no longer use Windows so I can not remember how you make sure files are saved to particular folders.

Find the UUID of the NTFS partition with sudo bllkid -c /dev/null then add a line to /etc/fstab in your Mint OSs with the following lines
```
#NTFS partition for data
UUID=[COLOR="#FF0000"]66E53AEC54455DB2[/COLOR] /mnt/storage  ntfs    defaults    0    0
```change what shows in red above to your own UUID.
Create the mountpoint folder with ```
sudo mkdir /mnt/storage
```
Now assuming you have the Documents, Music, etc etc folders in the NTFS partition you need to create symbolic links in your Mint OSs with ```
ln -s /mnt/storage/Documents Documents
```having first removed those named folders from your home in the Mint OSs.

Now all files will actually be in the NTFS partition but will appear in /home/user of each Mint OS, and Windows, Your Documents, or whatever it is now called.

---

