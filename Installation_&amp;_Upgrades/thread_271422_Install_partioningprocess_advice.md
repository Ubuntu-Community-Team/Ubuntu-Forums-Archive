---
title: "Install partioning/process advice"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by Reub on 2006-10-04
Alright, I know there's been a good deal of discussion around a lot of these issues already, but I'm having trouble answering all of my questions.  I guess the thing is I'm looking more for advice on if what I want to do is "correct" rather than the step by steps on how to do it.  Thanks in advance for any help.

I'm brand new to linux.  I'm getting a big fat external hard drive that I should have by this weekend, so I figured now was the time to back up my data and try to get a dual boot going.

Here's my plan.  It's probably very uninformed, so feedback would be appreciated.

I'm running a Dell Inspiron 6000 laptop.  60 GB HD (and another 250 on the external) 2 GB RAM.

1.  Backup existing documents/data to external drive (After formatting into a few NTFS partitions.  I'm aware that Ubuntu doesn't really support NTFS writing, but I'm willing to take a crack at some of the experimental/beta drivers and then just reformat if things don't work out.)

2.  Use Gparted to reformat and partition the main hard drive as follows:
   15 GB NTFS for XP/Programs
   10 GB (linux filesystem can't remember the name) for Ubuntu/Programs (where my linux OS and programs will be?)
  750 MB (linux fs) for Ubuntu Swap
    5 GB (linux fs) for Home (which is where I keep my linux specific data files/documents?)
   25 GB NTFS The rest of the drive will be for Windows/shared data and documents.
   
3.  Reinstall Windows XP (real clean and stripped down).  Get all the drivers and basic programs installed.

4.  Install Ubuntu.  Get all the drivers and basic programs installed.

5.  Use System Resource CD and included utils to make an ISO of the installs and empty partitions.  Hopefully this will compress down a lot and I can burn it to one or two DVDs that will be bootable for system recovery.

6.  Proceed to installing all sorts of fun junk until my system is all gummed up and I have to do it all over.  

If you made it this far, thanks!  Feedback would be appreciated.

---

### Post by mark_g on 2006-10-04
Looks good to me. You could also use the original Ubuntu-cd to boot your system, mount your filesystems and then repair your system, but hey, do whatever you think is safest!

Good luck.

---

### Post by mmmichael on 2006-10-04
If you're only using 15 GB for linux (filesystem = ext3) you might want to leave your home directory on your root partition. Just format a 15 GB partition and when prompted to select a mount point choose / (root). Your home directory will be included in this partition if you don't select another partition with the mount point /home. 

If you want a seperate /home partition, I would suggest 7GB for / and 8GB for /home. I find that my /home partition fills up a lot faster than the root partition. I have root on a 13 GB drive and home on a 30 GB drive and both are half full.

---

### Post by Reub on 2006-10-04
Thanks for input, both.

@mmmichael

What sort of files do you have filling up your \home directory(or partition, or folder, or branch of file system...)?  Are many of them linux specific?  I hope to keep a lot of media files and the like that will be accessed by both XP and Ubuntu on that last, larger, NTFS parition, as long as I can get it writeable with Ubuntu.  If that doesn't work out, I'll either change it to FAT32 or do some resizing.  

Thanks again!

---

### Post by mmmichael on 2006-10-05
> **Reub said:**
> 



What sort of files do you have filling up your \home directory?  Are many of them linux specific? 

Besides documents, media and pictures, there are many configuration files. Many applications that are installed by the user will create hidden directories within the user's home directory. These include configuration files, application data, and even your email. This is because the system allows for different users to have their own set of applications and their own configuration preferences by storing these files in the user's /home directory.

---

