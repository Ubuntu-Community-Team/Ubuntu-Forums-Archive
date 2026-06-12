---
title: "installation problems"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by SirJYK on 2006-11-04
My system specs are Win XP Pro, A643400, 1 gig of ram, 2 WD Raptors in stripe 0, additional Maxtor 120 gig 7200 hard drive.  Initial goals were to install Ubuntu and play around with it on the 2nd hard drive.  This I did successfully(version 6.1).  Now, Windows will not work properly unless I disconnect the 2nd hard drive(by disconnecting the power cord).  I would like to regain functionality of the 2nd hard drive in Windows.

1)  How do I do this?  Any tips would be appreciated.  Is there any way to restore the hard drive to previous settings before Ubuntu was installed?  My only thoughts at this point are to save all my data off of the drive and reformat it in Windows.  I really do not want to do this.

2)  I think my logic is flawed in running Ubuntu from the 2nd drive.  My thoughts were to change the boot priority in the BIOS when I wanted to run Ubuntu.  Initially, I figured this would the best way because of my raid array.  

Any help would be appreciated!
Thanks.

---

### Post by SirJYK on 2006-11-04
anyone?

---

### Post by SirJYK on 2006-11-04
anyone?

---

### Post by rsambuca on 2006-11-04
Did you leave all of the drives connected when you installed ubuntu?

---

### Post by SirJYK on 2006-11-04
yes.  I am glad you responded.  I was about to send you a message for help!

---

### Post by SirJYK on 2006-11-04
Some more info...  I can boot into Windows safe mode and mostly all will work fine.  It sees the the 2nd drive and I can view everything on it.  Not in safe mode, Windows becomes non-responsive, unless I power down the hard drive.  Then windows works fine but cannot access the 2nd hard drive, obviously.

---

### Post by rsambuca on 2006-11-04
Wow, that is some bizarre behavior.  Sorry, I am of no help on this one.

---

### Post by SirJYK on 2006-11-04
Any help here before I back up everything and start drastic measures?  I am sure there has to be a simple solution.

---

### Post by SirJYK on 2006-11-05
anyone?

---

### Post by SirJYK on 2006-11-05
Is this problem really that specialized or do I have it posted in the wrong place?

---

### Post by rsambuca on 2006-11-05
Sorry, I have looked around quite abit and can't find any info anywhere on this problem.  The strangest thing to me is that your Windoze works in safe mode and will see the drive, and then doesn't work in regular mode.  Does it even boot with the second drive connected?

---

### Post by Freddy on 2006-11-05
Sorry I cant help you much, but you should try to ask your question over at linuxforums.org cause now a days ubuntu forums kind of (sorry to say it) sux. I remeber back in the days when kubuntu and Ubuntu had diffrent sections and the question you asked didn't vanish into page 3 after 15 minutes.

You should and would be able to run you Ubuntu install from your second (third, fourth) drive, but don't wander into bios to choose what OS you should boot. Install Grub (bootloader) when the install ask you to and use that to boot into one of your OS's. Just reinstall Ubuntu and install Grub with it.   /// Freddan

---

### Post by SirJYK on 2006-11-05
Yes, it boots when the drive is connected.  But, it acts confused and asks which drive to boot from.  I have to pick the striped array.  When the additional drive is not connected, I am not prompted to tell it which device to boot from, like there is a problem with the MBR.  Furthermore, what is really confusing, is that Windows allows itself to be confused by a drive that does not have the core OS on it.

---

### Post by SirJYK on 2006-11-05
Freddy,

All is well on the Linux side of things.  Go figure.  I am impressed.  It runs on a small footprint and is fairly easy to work with.  It solved my problem of backing up my additional drive on my network, since I couldn't access it via Windows.  Now, after I back up my data on my main machine's C drive, I will be ready to really tinker with and setup a dual boot with my Raptors.  I am being forced to do this because I cannot find a simple fix for restoring the integrity of the Windows setup.  Now that everything is nearly backed up, I cannot say that I am unhappy about having to explore other options if you will.

---

### Post by mark_g on 2006-11-05
Weird problem indeed. Personally, I'd try to reinstall Grub, maybe even on the other hard drive and boot from that. Just play around a bit.

```
/sbin/grub-install /dev/sda with sda the correct hard drive
```

(more details can be found on [http://forumz.tomshardware.com/software/Reinstalling-GRUB-ftopict231779.html](http://forumz.tomshardware.com/software/Reinstalling-GRUB-ftopict231779.html))

The drive that's causing you trouble, what filesystem is on it: FAT,NTFS,ext3... ?

---

### Post by SirJYK on 2006-11-05
anyone?

---

### Post by creznedmick on 2006-11-05
greetings
Just a thought, in installing ubuntu did you repartition the the second drive; if so what happened to the drive letters
Michael

---

### Post by SirJYK on 2006-11-06
Yes, I did repartition the drive.  I believe you have to because there is not an existing Linux-friendly partition that exists.

---

### Post by SirJYK on 2006-11-06
Just to add some closure to this topic, this is how I fixed my problems.  I manually deleted norton systemworks.  I couldn't uninstall it in safe mode.  Norton must have gotten jumbled when I installed Ubuntu to the 2nd hard drive where it was located.  This allowed me to boot up and have normal Windows operation.  I then uninstalled Norton and haven't had a problem since.

---

### Post by rsambuca on 2006-11-07
Wow, good job.  What made you think it might have been Norton messing things up to try this?

---

### Post by SirJYK on 2006-11-07
> **rsambuca said:**
> Wow, good job.  What made you think it might have been Norton messing things up to try this?

LOL, nothing definitively pointed to this solution.  I was in trial and error mode.  I knew, in safe mode, i could access D drive properly.  So, I started trying to eliminate anything that could have the power to cause problems at a low level.  Norton, in my opinion, stuck out like a sore thumb.  It was the first on my list.  To be honest though, I was fully prepared to delete the entire hard drive if I had to.

---

