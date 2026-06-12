---
title: "Install Problems"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2011-08-06
I had Ubuntu 10.10 running fine on an Athlon 1.3 GHz with 512MB RAM and 40 GB drive for OS and 200 GB drive and another 40 GB drive as a file server for backing up data.

Last week I pulled a 40 GB drive and swapped in an 80 GB drive that had OSX on it.  On install, I formatted the 80 GB drive and set up to load the OS on it.  However I keeps crashing after a significant amount of files are copied over.  24 hour Memtest 86+ confirmed good memory.  I've been having problems loading Ubuntu 11.10 and 10.10 on this PC as well as an older one with only 192 GB RAM, and Lubuntu 11.10 also failed to load on that old PC.  So I re-downloaded and burned another 11.10 CD on my PC at work.  Why do they no longer have a Checksum string to verify a good CD?  That CD as well as the other copy both checked out on self test, but keeps crashing once I get farther into the install.  The floppy drive won't load disktools or Win XP install disks, so I burned an ISO disktools CD, but it wouldn't load either, so I suspect the floppy and the CD drives are failing.  I think the live CD installed enough to get a desktop and I ran disk utility, which reports all 3 disks healthy.  The filesystem properties show 2.6GB and 165 MB free, so I'm not exactly sure it's running Live CD or off a hard disk.

I was able to run Disk Utility which reported "Disk is healthy" for the 80 GB drive and all sections Good or N/A.  Check Filesystem returns "File system is clean".  I can't format the drive "... /dev/sda:   Device or resource busy".  I can't delete the partition "...refusing to delete a protected partition".  I can't Edit Partition "...MSDOS_MAGIC found".  I am able to format the volume, however.

I guess I can try installing Ubuntu on the 40 GB drive again and/or replace the CD and floppy drives, but want to make sure there is nothing wrong with the 80 GB drive.

---

### Post by HDTimeshifter on 2011-08-06
Well the CD and floppy drives were bad.  I replaced them with good ones.  Strange for both to fail at the same time.  In fact, I've never had a working CD or floppy drive fail before.  I had to throw out 2 floppy drives as a spare one also was bad.

So everything installed ok, but after rebooting, I think I get a Unity screen - purply-red with just a pair of arrows, a sound icon, and a red power icon in the upper right.  So how do I use Unity?  I can't get any menus or a file manager to pop up by clicking anywhere around the screen.  I also tried right and scroll wheel clicking all over the place including the top/bottom, right/left edges of the screen.  My main system was upgraded to Unity-less as a memory stick just happened to fail the day I upgraded to Natty and I haven't figured out how to manually select Unity (not that I really care as Gnome works fine for me).

---

### Post by HDTimeshifter on 2011-08-06
Rebooting resulted in normal startup with notification that the PC won't support unity.

However the 200GB drive is not showing up in Computer.

---

### Post by oldfred on 2011-08-06
Are you mounting 200GB with fstab so it is mounted on reboot or just using Nautilus to find it?

Post this, although it is more for boot issues it also shows the entire system and where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by HDTimeshifter on 2011-08-06
I got it to display by formatting the drive as NTFS.  I think it was "Unknown" before.  I then backed up all my data from my main PC running Ubuntu, but mostly former Windows data (Office and converted to LibreOffice files and pictures) before making the switch to Ubuntu 3 years ago.

On the other hand, I decided to format the 40 GB drive as EXT4, name it Linux Data to back up any Linux specific data, but can't see it in Nautilus even after creating a subdirectory and chmod g+w.  If that worked, I thought I would change the 200 GB format to a native Linux format rather than Windows only NTFS, which seems more limiting.

---

### Post by oldfred on 2011-08-06
I would suggest LinuxData or Linux_Data. If you use spaces you usually have to include quotes around a name with spaces so it knows the full name.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I learned a while back to stop using spaces. Use CamelCase or under_score or just onename. Windows will work without the spaces and it makes things a lot simpler in Linux.

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I just learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
gksudo gedit /etc/fstab
```
UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
```

Or if ext3 (change to ext4 if that and use your UUID)
```
UUID=13a684e4-2849-4566-9528-21cd07028a9a /backup          ext3    relatime        0       2
```

---

### Post by HDTimeshifter on 2011-08-06
Yeah, I should quit using spaces as it's a pain navigating them on the command line (TAB pre-fill shortcut helps).

I actually fixed the problem already, but somehow my post edit didn't take.  I used Disk Utility and reformatted or repartitioned (forgot where) checking the "Take Ownership" box.  Who the hell owns the drive if you don't "Take Ownership"???  Then created a top level folder and shared it.  I think Ubuntu doesn't like you sharing the drive itself - probably not recommended anyway for security purposes - too global.  So I no longer have to mess with the command line.  :)

I was able to copy a test file from my main PC to it in Ubuntu.  Then I booted my main PC to Windows 7 (other drive for dual boot), and I was even able to copy a file from the Windows C: drive to the EXT4 Linux Data drive!  Wow!  I'm going to reformat the 200 GB drive to EXT4.  The distinction between Linux and Windows files is becoming a blur - much easier than a few years ago, when I had to spend a few weeks hacking Ubuntu and Vista to get networking (Nautilus and Samba visibility) with Vista (XP was a breeze - Vista was a pain).

---

