---
title: "dual boot ubuntu 10.04 and windows 7 on HP pavilion a6750t"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by CWB33 on 2010-08-03
Absolute newbie to Ubuntu....I spent all weekend trying to install Ubuntu 10.04 on my HP pavilion a6750t, but had no success. the problem as I understand it is with the raid setup on the system. I have two drives on it set up in a raid 0 configuration, I want to keep my Windows 7 on it and install Ubuntu too, any advice on how to successfully do this would be greatly appreciated.

---

### Post by ajgreeny on 2010-08-03
Use the Alternate Install CD to do the job.  I think that is the only way to deal with a raid setup.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by ronparent on 2010-08-03
I would advise any newbie not to try installing 10.04 to a raid. It is doable but if you don't understand the pitfalls and traps it may be more trouble than it is worth. 

You could perhaps easier do the install on an external usb drive to play with it awhile. If you are serious that would also give you a chance to research the raid issues before committing your self to it.

---

### Post by Mark Phelps on 2010-08-03
> **CWB33 said:**
> Absolute newbie to Ubuntu....I spent all weekend trying to install Ubuntu 10.04 on my HP pavilion a6750t, but had no success. the problem as I understand it is with the raid setup on the system. I have two drives on it set up in a raid 0 configuration, I want to keep my Windows 7 on it and install Ubuntu too, any advice on how to successfully do this would be greatly appreciated.

Before you install Ubuntu, be sure to open the Win7 Disk Management utility and shrink the Win7 OS partition to make room for Ubuntu.  Don't format the resulting free space but leave it unallocated.

Also, be sure to use the Win7 Backup feature to create and burn a Win9 Repair CD.  You will need this later to repair the Win7 loader if that becomes damaged as a byproduct of the Ubuntu install.

Only then, boot into your Ubuntu CD and select the "largest free space" option and let it do the partitioning.

---

### Post by ronparent on 2010-08-03
Mark is correct up to installing. What he suggests would work for a non-raid external. BUT, if you insist on installing to a raid, ask for more help.

---

### Post by CWB33 on 2010-08-03
Thanks you all for your advice. I must say that I did try installing using both the Live CD and the Alternate CD. I had no success in both instances. I think at this time, given my level of experience I will take your advice ronparent and wait until I know more. Lastly, am I better off using Virtualbox or installing to an external USB drive? which option gives me the better experience?

---

### Post by ronparent on 2010-08-03
I personally prefer the usb drive approach. It makes the OS transportable between multiple computers.

---

### Post by MoToast on 2012-10-17
Related but more basic question.  I am desperately trying to get ubuntu 10.04 to dual boot with Windows 7 on my new HP h9-1270t.  It came with Windows.  I got the 10.04 CD created and restarted with the disc in the drive.  Ultimately, I had to hit Esc during normal booting so that I could change the boot order to hit the CD/DVD drive first - annoying but tolerable.

At any rate, I've tried this now several different ways with the same darn result.  I get ubuntu installed, restart the computer and...straight to Windows.  No linux, no grub, nothing but Windows.

I'm sure I'm not doing something right in creating my partitions and which partition should be the linux boot partition.  

Questions:

Which partition should be the ubuntu boot partition (the newly created sda4 partition)?

If you are going to simply re-direct me to a link - I sure hope it is a really good and recent one as I swear I've visited a ton and no luck.

That last bit said - I'll take what I can get. 

Thanks

---

