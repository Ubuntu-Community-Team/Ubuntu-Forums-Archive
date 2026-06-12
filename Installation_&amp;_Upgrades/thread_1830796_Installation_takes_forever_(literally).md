---
title: "Installation takes forever (literally)"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by mbuchoff on 2011-08-22
When trying to install Ubuntu, I continuously get stuck on the screenshot attached.  I've tried checking and unchecking all the options to no avail (I left it all day, morning to night and the spinning timer was still going.)  We are running two Geforce 9600GT PCI-e x16 512mb cards in SLI mode on a Asus m2n-SLI motherboard.  I suspect the graphics card has something to do with this as 3D wasn't supported when running natively on the DVD.

It's also worth mentioning we were able to run off the CD pretty well.

Thanks in advance and let me know if there's more information I can provide to help figure this out (as well as how to get this information).

[https://docs.google.com/document/d/1mSav9T-r9OIIuG4u75SSL3-G3Os9Z1YASEHG3FCnKB8/edit?hl=en_US]("https://docs.google.com/document/d/1mSav9T-r9OIIuG4u75SSL3-G3Os9Z1YASEHG3FCnKB8/edit?hl=en_US")

---

### Post by critin on 2011-08-22
You are sure you have the disk space required?  Why don't you begin the install again?
It doesn't take long to install if conditions are right.

critin

---

### Post by mbuchoff on 2011-08-22
Thanks for the reply.  I can't remember if the hard drive is 120 or 240 GB, but it's completely free (as in I told Ubuntu to reformat it.)  I'll post a screenshot when I get home, but I doubt that's the issue.

What might also be is that the particular computer I'm using happens to have 5 or 6 hard drives in it.  Does Ubuntu tend to have trouble under those conditions?

---

### Post by critin on 2011-08-22
No, but it needs to know where you want to install it.  Did you make it clear which disk to use?  Double check.

I always try the cd live, check the disk/partition through gparted for the correct place, then install from the desktop option.  Are you clicking 'install' from the boot-up?  That's tricky if you have more than one disk. (for me)

critin

---

### Post by critin on 2011-08-22
Formatting a disk that size does take a pretty long while, but it should be within an hour at the longest.  
critin

---

### Post by mbuchoff on 2011-08-23
When trying to reinstall Ubuntu last night, I realized that we had already installed XP to get the computer up and running.  Using Wubi to have the two coexist seems to be working fine, giving us a chance to try Ubuntu out before deciding whether we want to wipe XP in favor of it (I really like Unity, despite it's bad rep, so I'm leaning toward yes).

So at the moment this is a nonissue, but thank you for your quick and helpful response.  If I end up wanting to do a clean install, I'll follow your advise and reply to this thread on whether I was successful.

---

### Post by critin on 2011-08-23
Great!  My first experience with Ubuntu was with Wubi and I liked it.  Now they all go straight to the disks.  
I believe you can mark this tread solved by clicking on the 'Thread Tools' at the top.

critin

---

### Post by oldfred on 2011-08-23
Herman's site has lots of info on installing to a second hard drive. 

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

I have always had to add nomodeset to get my nVidia 9600 to work. Then I install the default nVidia driver and have had no issues.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mbuchoff on 2011-08-23
Thanks, olfred.  To my surprise, our video card actually did work; it just took an install, reboot, then Ubuntu to realize we needed to download 3rd party drivers, so really Ubuntu did all the work for us here.  I haven't tested whether we're getting use from SLI mode.

Also, I'll save that link dealing with two hard drives for if and when we decide to do a full install.  Thanks again.

---

### Post by mbuchoff on 2011-08-23
Have either of you figured out how to access the files in the Windows partition outside of Ubuntu?  I had to switch back to XP for a little bit in order to do this.

---

### Post by oldfred on 2011-08-23
With the same system or another?

I share a NTFS partition and suggest that you only read from another system partition. I have my Firefox & Thunderbird profiles in the shared partition so I do not have to reboot to have the same bookmarks or email.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by critin on 2011-08-23
I searched the software center for Samba and installed it.  Then I made sure my documents permissions were set and the share was allowed.  Permissions and share are both along the top when you click properties of documents. (and anything else you want to share)  

It was easy to see the windows documents through ubuntu, it took a little more work to see ubuntu from windows--but I finally got it to work.  lol

I use Sync on Firefox to keep all bookmarks, passwords, etc on all computers.  Mail is available wherever I am.  Msn Live and gmail.   Ubuntu is interesting to work with, but I can't get into the complicated end of it.


critin

---

