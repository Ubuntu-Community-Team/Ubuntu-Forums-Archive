---
title: "Recovery solution for dual boot system"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by joe-moyers on 2013-11-17
I would like some advice from the collective concerning backing up a dual boot system. I am running Win7 Pro 64bit/ with Ubuntu 12.0.4 64bit LTS. Both systems are on a 500GB harddrive. I purchased a 3TB external drive for storage of backup files and copies of drive images for recovery. The system is working great except it looks like both systems are trying to backup the entire 500GB drive. Or, the Western Digital backup software is trying to backup one partition it recognizes as well as one it doesn't. What are your recomendations for backup? If I have to I could purchase a second harddrive and install Ubuntu on it. What would be the best solution?

---

### Post by oldfred on 2013-11-17
Often hard drive vendor's software is not a backup solution but a way to copy then entire old hard drive to your new hard drive.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

      
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

While a full image backup gives you a way to restore your system, it is only valid for a short time as you add, change & delete things all the time.
Since Ubuntu is easy to reinstall, my backup is everything I need to restore system after a new clean install, but not backing up system itself. I started with a simple rsync file & it has grown over time.

      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh


 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

   Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by joe-moyers on 2013-11-17
Thanks for the speedy reply. I didn't think I could clone and restore a drive with Linux and Windows on it. I will review all the information and clone my drive as well as setting up incremental backups. Thanks again.

---

### Post by oldfred on 2013-11-17
If you totally clone drive, you may not use old drive or have to totally reconfigure one drive or the other.

A cloned drive will have the same UUIDs and create lots of confusion. System may boot using one or the other drive as they are seen as identical. If not totally reformatting old drive change its UUIDS.

 # To clear cache and get new view:
sudo blkid -c /dev/null -o list


        Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by joe-moyers on 2013-11-17
What I should've said was create drive image instead of clone drive. I want to be able to overwrite my drive with a backed-up image in case of virus infection or damaged OS because of malware. (windows stuff) Would the drive ID cause issues in this case?

---

### Post by oldfred on 2013-11-17
Not sure, never used any of the clone type software. Normally it is intended to copy back into the same drive for fix and that works. If a full drive image I would think all internal structures are also copied and would be an issue if installed to another drive. You then would have to run several repairs and changes to make it work.

---

