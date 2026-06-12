---
title: "Partitioning conundrum on install"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2010-01-04
I am installing 8.10 from CD onto my laptop which currently has a Windows Vista installation that I want to keep (i.e. dual boot). 

At the 'Prepare disk space' screen there are two options - "Guided - use entire disk" and "Manual". According to the documentation there should be a "Guided - resize" option for dual booting, but I don't have this.

If I select "Manual" it shows four NTFS partitions /dev/sda1,2,3 & 4. But there is no reference to the Windows installation. (I was expecting it to show the Windows partition and ask how big I want it to be).

Not sure how to proceed here, can anyone please advise?

---

### Post by Zimmer on 2010-01-04
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Basic advice: read everything, Install EasyBCD to your Vista OS, use Vista to create space for your Ubuntu install, DO NOT install GRUB to the MBR (install it to the Ubuntu partition) ...
EDIT: as per the instructions on NEOSMART Ubuntu tutorial.

---

### Post by Bartender on 2010-01-04
> **RegUB said:**
> If I select "Manual" it shows four NTFS partitions /dev/sda1,2,3 & 4. 

You've got a problem right there.  4 partitions, and they're all primary.  Primary partitions will be numbered 1 thru 4, logical partitions start with "5".

Have you created your Vista recovery DVD's?

And what make/model of PC we talking about here?

You might want to attach a screenshot to your next post.  Boot off the LiveCD, choose "Use Ubuntu without making changes" get to the desktop, plug in a thumbdrive, go to Applications>Accessories>Take Screenshot and save the screenie to the thumbdrive.  That way you can attach the screenshot to a post regardless of what computer you're using to get to the forum.

---

### Post by RegUB on 2010-01-04
> **Bartender said:**
> 
And what make/model of PC we talking about here?
Thanks for this. It's an Acer Aspire 5920G.

I'm attaching screenshots of (1) the partitions as seen by Vista's Disk Management utility (2) the partitions shown by the Ubuntu installer. These seem to be in agreement. The Vista installation is on the C: drive which I think equates to /dev/sda2. Since my original post I have shrunk this partition by 10GB in order to create space for the Ubuntu installation, as suggested in the 'how_to_dualboot' link in Zimmer's reply. Do you concur with this?

---

### Post by Bartender on 2010-01-04
Awesome.  I have an Acer 5920.  It was built in 2006.  I was gonna say our partitioning schemes will be identical but they're not.

You're gonna have to slow down.  With four primary partitions it doesn't matter if you squish any of them, so you wasted time and risked data loss by creating the 10GB of free space.  Notice that the Ubuntu partitioner labels it "unusable".  I think the manufacturers do this stuff intentionally to discourage people from making any modifications.

Congratulations on taking screenshots, but the screenshot that I described is more helpful.  Still, it doesn't matter at this point.  You have four primaries and that's where we need to start.

Have you made your recovery discs?

I've found the folks at [notebook review forums]("http://forum.notebookreview.com/") to be very helpful.  They have a Linux sub-forum and an Acer sub-forum.  See if you can find some helpful posts regarding your specific laptop.  Last time I hung out, there were some very detailed threads regarding the confusing Acer partitioning scheme in the Acer sub-forum, and the guys in the Linux sub-forum are usually quite happy to help someone install Linux successfully.

I'll tell you what I did with my Acer.  I made the recovery discs. I tried to shove Vista aside with a GParted LiveCD, which was dumb on two levels.  The Vista partitioner is more reliable for this, and I had four primaries so I was headed off in the wrong direction anyway.  Vista wouldn't start.  On the verge of panic, I ran the recovery DVD's.  When finished, Vista restarted and there was only one partition.  All the others were deleted by the recovery discs.

Another guy came up with a better solution.  He wiped his drive with a GParted LiveCD, formatted part of it as a primary NTFS partition, then popped in his Vista recovery discs, which only saw the NTFS partition and installed there, leaving the rest of the drive alone.  I thought that was pretty cool.

This is way too important for me to say the above will absolutely for sure work with your Acer.  Best to visit the forums I mentioned and find out for sure.  Talk with a few guys who can say what they did.  Maybe you can just delete some of those partitions after making your discs.  I don't know.  I can try to help you figure it out.

Found this by googling "acer 5920G linux four partitions" - there are more results but I'm on dial-up so...
[http://ubuntuforums.org/showthread.php?t=698704](http://ubuntuforums.org/showthread.php?t=698704)

---

