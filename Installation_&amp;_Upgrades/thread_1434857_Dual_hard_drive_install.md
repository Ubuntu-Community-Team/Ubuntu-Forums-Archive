---
title: "Dual hard drive install"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by holadebob on 2010-03-20
I am a noobie and have a question on installing Ubuntu Jaunty with two drives. I tried and ended up with a lot of problems because of mount point.

I have a 160Gig and a 40 Gig drive. I would like to install the system on the 160 Gig, and use the 40 Gig drive as a storage for backups or whatever. It appears in the installation process that I am required to use a mount point, which would then turn the drive over to the root system, which would not allow it to be totally available to me. I just want to format it to ext3 filing system. 

Coffeecat, if you are out there and see this, strange things are happening to the 40 Gig drive - it says it is using 2 gig, but it is totally empty of all system files, hidden files, trash, etc. and it is being imaged in the media folder in root. I believe I have messed this install up to the point of no return and think I should go ahead and start over - see if I can do it right this time. Thank you

---

### Post by srs5694 on 2010-03-20
I don't think you understand what a mount point is. In Linux, all disk space (aside from swap space and partitions you don't want to access) is accessible via a single directory tree. If you have multiple physical disks, or multiple partitions on a single disk, or even removable disks, these disks must be mounted at some point (hence, "mount point") in your directory tree. This is just a directory. For instance, you might mount a disk or partition at /home, in which case all the files in the /home directory will be stored on that particular disk.

Whether or not you as a user will be able to access those files depends on the permissions and ownership on the files and directories involved, no matter where the disk is mounted or even if the directory involved serves as a mount point. In the case of non-Linux filesystems, such as NTFS, the files' ownership and permissions may be set by the mount command used to mount the disk, but for Linux-native filesystems, ownership and permissions can be set by the chown and chmod text-mode commands or by GUI tools.

Thus, what you should do is decide how you want to access that space. If you want to devote that 40GB drive entirely to "backups or whatever," as you say, just ask yourself where in your directory tree you want those files to reside. Is /home/backups good? Perhaps /home/{yourhomedir}/backups, where {yourhomedir} is your account/home directory name? How about /other/junk? Just make your decision and enter the value you choose as the mount point. If you find that the mount point is owned by root and you can't write files to it as an ordinary user, just use chown, chmod, or a GUI tool to change the ownership and permissions on it. For instance, if you use /other/backups and your username is bob, you could type "sudo chown bob /other/backups" to acquire ownership, giving yourself the ability to write in that directory.

Even removable disks (floppies, USB flash drives, CD/DVD drives) are handled in this way. Most Linux distributions try to make these work more like they do on Windows by presenting desktop icons when you insert a device. When you double-click the icon, the desktop environment mounts the matching device at some point and gives you access to it. I'm not sure offhand if Ubuntu's default configuration would do this for partitions you've not otherwise described in /etc/fstab (including those you specify when you install the OS). If it does, then creating partition(s) and filesystem(s) on the disk when you install, but not specifying a mount point, will enable you to access the disk in this way. Deep down, this is really just like specifying a mount point when you install Ubuntu; the only difference is when and where the disk is mounted.

---

### Post by holadebob on 2010-03-20
Thanks SRS, I read it three times and I think I understand it. Can I give it a mount point anywhere in the directory tree? When I go to edit the partition on the installation program, it gives me a drop down menu of mount point choices. How do I assign it a different mount point like /home/backup in the partitioning part of the installation? 


You are reading from a guy that has got tech background and experience in early assembly, basic, and one semester of C back in 1981, so please go easy on the ole guy. Thanks

---

### Post by srs5694 on 2010-03-20
*Almost* any point is reasonable. You wouldn't want to use a mount point like /dev that has its own pseudo-filesystem attached to it. If you specify a standard directory (/usr, say) during installation, the installer will mount it and your partition will become the home for that directory.

It's been a while since I used the Ubuntu installer, so I don't recall precisely what it allows; however, most Linux installers generally give you some way to type in another mount point rather than select one of the predefined ones. If Ubuntu doesn't, you can skip giving the partition a mount point and instead add it to the /etc/fstab file after the installation is complete.

---

### Post by holadebob on 2010-03-21
The installation program refuses to continue without giving all partitions a mount point that is listed on the options on the drop down table. Maybe there is a way to bypass that - If I give the drive a mount point that is a folder in the system, such as /user/local, the installation loads the system files into that mount point, which would be my 40 G hd, and it would make my hd an integral part of the system, rather than an independent storage drive that I would like. If I go root, remove or copy the files from the hd (ie system root files), I've destroyed the system installation integrity. I think I have all this right, please correct me if it isn't.

---

### Post by holadebob on 2010-03-21
After all my questions, I am beginning to see that I need to learn more about the Ubuntu system, so I will bow out for now and do some studying.
Thanks for your patience.
Bob

---

