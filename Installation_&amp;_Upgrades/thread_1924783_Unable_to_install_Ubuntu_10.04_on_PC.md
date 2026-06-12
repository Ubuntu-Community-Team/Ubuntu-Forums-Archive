---
title: "Unable to install Ubuntu 10.04 on PC"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by rmcellig on 2012-02-13
I am trying to install Ubuntu 10.04 on my wife's PC. She is currently using Windows XP Pro. I would like to install Ubuntu side by side or by creating a new partition to install it in.

I am unable to re size her PC using Gparted. I have the drive unmounted. the re size option is there but I am unable to click and drag the drive to make room for a new partition.

I notice from the screenshot that it is recommended to run chkdsk /f to check the drive. How do I do this if I boot from the XP Pro install CD. 
I would really like my wife to try out Ubuntu. Right now I have her using Puppy Linux 5.2.8 until I can get Ubuntu working and installed properly. 

My wife still needs her PC to run office (her work place, not the application) based apps that she uses all the time.

---

### Post by ajgreeny on 2012-02-13
Here you go!

You don't run it from the Windows CD, but from the command prompt.

Goodness me!  A _*Command prompt*_?  That sounds just like Linux, doesn't it?

[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

---

### Post by MAFoElffen on 2012-02-13
> **rmcellig said:**
> I am trying to install Ubuntu 10.04 on my wife's PC. She is currently using Windows XP Pro. I would like to install Ubuntu side by side or by creating a new partition to install it in.

I am unable to re size her PC using Gparted. I have the drive unmounted. the re size option is there but I am unable to click and drag the drive to make room for a new partition.

I notice from the screenshot that it is recommended to run chkdsk /f to check the drive. How do I do this if I boot from the XP Pro install CD. 
I would really like my wife to try out Ubuntu. Right now I have her using Puppy Linux 5.2.8 until I can get Ubuntu working and installed properly. 

My wife still needs her PC to run office (her work place, not the application) based apps that she uses all the time.
What the last poster meant and what GParted was telling you...

Yes, the partition the XP is on has errors.  Startup XP. Click on "Start". In the search filter type "cmd" > cmd.exe should appear > right click on it. select run as adminstrator.

The window with a command prompt should appear > type " fdisk /f " Press <Enter> It will try to correct the errors. When it finishes, reboot and do it again, reboot. Do it until there are no errors reported by fdisk...

On your resize, I suggest you start out w/ 8GB for the ext4 and 2GB for Swap. That is usually my minimum for an install for a customer.  Any thing less is starting out in a constrained  space. (JMHO)

Sometimes when you resize a NTFS partition with GParted, windows will complain about the file indexes being off. Then you have to rebuild the indexes.  Most people suggest resizing a Windows partition with Windows, that way it keeps or rebuilds it's own indexes while it's resizing.  I do it both ways, but I know what to expect.

Note- Libre Office and OpenOffice both are compatible with MS Office formatted documents.

---

### Post by rmcellig on 2012-02-13
I'm in safe mode now running chkdsk /f. Taking forever. I should be good to go after that? Fingers crossed. Will post back with results. I mentioned Libre Office but what happened was that her place of work offered their employees Office Professional for something like 11 dollars and they need to use it because that's what they use at work :( 

Oh well. At least I am having fun with Linux!!

---

### Post by kittyhawk63 on 2012-02-13
I would recommend you use Wubi to install Ubuntu 10.4. It will be installed like a program in Windows. You can delete it at any time like you would uninstall any other program. Why not use the latest Wubi Ubuntu 11.10 install?

---

### Post by MAFoElffen on 2012-02-15
> **rmcellig said:**
> I'm in safe mode now running chkdsk /f. Taking forever. I should be good to go after that? Fingers crossed. Will post back with results. I mentioned Libre Office but what happened was that her place of work offered their employees Office Professional for something like 11 dollars and they need to use it because that's what they use at work :( 

Oh well. At least I am having fun with Linux!!
Been a couple days now. I've been waiting to see if chkdsk finished and corrected your errors so that you could continue... Have you continued yet?

---

### Post by rmcellig on 2012-02-15
Still no luck. I ran chkdsk four times. Ivhave no problems booting into the Windows side. I wonder if there is anything else I can try short of reformatting the drive. In the meantime, I am using Puppy Linux (frugal install), with no problems.

---

### Post by MAFoElffen on 2012-02-15
> **rmcellig said:**
> Still no luck. I ran chkdsk four times. Ivhave no problems booting into the Windows side. I wonder if there is anything else I can try short of reformatting the drive. In the meantime, I am using Puppy Linux (frugal install), with no problems.
So, let me get this straight:
 - You earlier ran Gpart, who said you XP partition had filesystem errors and needed you to run chkdsk to correct them.

 - Then you ran chkdsk 4 times, which should have corrected them on the first pass...

 - Are you still trying to resize your (wive's) xp partition?

What is your plan? Meaning resize/shrink your XP partition again to leave how much free? Then deleted the ext4 partition and create a larger one?

-OR-

Are you going to install on the existing ext4 and swap partitions?

---

### Post by rmcellig on 2012-02-16
Right now her entire hard drive is an NTFS partition that has windows xp pro as well as a frugal install of puppy Linux 5.2.8. What I wanted to do is shrink the NTFS partition so that I could crate a new ext4 partition to install ubuntu 10.04 on. I did try wubi a while back but this time I want to have two partitions. The NTFS one for xp and a new ext4 partition for ubuntu.

I would also need to create a swap partition of about 3gb for the ububtu install.

---

### Post by MAFoElffen on 2012-02-17
> **rmcellig said:**
> Right now her entire hard drive is an NTFS partition that has windows xp pro as well as a frugal install of puppy Linux 5.2.8. What I wanted to do is shrink the NTFS partition so that I could crate a new ext4 partition to install ubuntu 10.04 on. I did try wubi a while back but this time I want to have two partitions. The NTFS one for xp and a new ext4 partition for ubuntu.

I would also need to create a swap partition of about 3gb for the ububtu install.
Sorry for delay. Been in hospital since yesterday morning.  

Good. A plan. So you did chkdsk 4 times.  Why "4" times?  Did it not correct it's errors?

If it were me, if in 4 times trying to correct errors, if those errors are still present, I would back off everything on that partition, low level format, partition the the size you want to end up as... format it NTFS. Check the disk for defects and mark bad sectors (chkdsk /f")... Then Restore it back on.

---

### Post by rmcellig on 2012-02-17
I agree. Formatting the drive might be the answer. Hope you are OK!

---

### Post by MAFoElffen on 2012-02-18
> **rmcellig said:**
> I agree. Formatting the drive might be the answer. Hope you are OK!
Was a sleep study... 26 years of only getting 1-2 hours (not continuous) sleep a night.  Hoping they find "something" that will help.  Sleeping pills don't seem to work with me.

---

### Post by rmcellig on 2012-02-18
Best of luck with that. I bet you are looking for an answer that works!

---

