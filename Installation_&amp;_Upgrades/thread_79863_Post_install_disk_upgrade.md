---
title: "Post install disk upgrade"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by rbrugman on 2005-10-21
Hello fellow Ubuntuers,
I have been running Ubuntu for a few years now, and my upgrades have always went smooth, but now my server is running out of space.  Right now, I have a 120 gig disk with a 20 gig partiton for programs/system stuff, and a 100GB /home partition.  My brothers have recently started doing some heavy downloading and the **** DVD images are sucking up my server space.  I bought myself a new 400GB disk to add to it.

Here's my problem:

I've never installed a hard drive in linux after the system has already been installed, so I'll need help with that.  Secondly, I was wondering which way would be best to set up the second disk.  I don't have the money for a RAID, so that's out of the question. How could I get the best use of my system without abandoning my 100 gig partition.  I just need more space!

Thanks a bunch!

Robert

---

### Post by rbrugman on 2005-10-21
I know someone has to know how to install a hard drive in linux.

---

### Post by supenguin on 2005-10-21
This question has been answered on the forums, here you go: [http://www.ubuntuforums.org/showthread.php?t=49234](http://www.ubuntuforums.org/showthread.php?t=49234)

The only think I don't think they mention is how to format it... If you're dual-booting, you may want to keep it readable by Windows, if not, go ahead and reformat to ext3 or whatever filesystem you're using with something like "mkfs.ext3 /dev/hdb1". That command is assuming your new hard drive is the second IDE hard drive and is hdb and it has one partition.

---

### Post by rbrugman on 2005-10-23
Thanks for the link, although it really only answers one of my questions.  My second one still remains.  What would you recommend for the setup of the new drive.  I'm looking for something that might give me the same bennifits of a raid (being able to have the home folders "spill over" on to the bigger drive when the current one is full).  I don't want to have to create a new home folders for each user.  Any input is appriciated!

---

### Post by supenguin on 2005-10-24
The only way I can think of to make the home folders "spill over" would be to use some kind of software RAID solution. I haven't had a chance to mess with any of them very much. The one that comes with Ubuntu is called LVM (Logical Volume Management). You'll want to check out the docs for LVM and search the forums, but I'm pretty sure switching your system to use LVM would involve reformatted both drives to use LVM. I hope I'm wrong though!

---

### Post by jmcvey on 2005-10-24
Think LVM is probably the way to go. Don't think you'd need to loss your existing data if you did it in a couple of steps. Basically, I'd put the new drive in the system and create the LVM stuff initially on that drive. Then move /home over to the new drive and change the appropriate files (fstab). Once everything is working, you could then delete the partition /home was in (this would be on the old drive which isn't needed since /home is now on the new drive) and use LVM to add the old drive to the volume group and expand the new /home onto it (basically /home becomes the new drive and the space it used to be on the old drive). Doing it in several steps keeps you from lossing the data, plus you can verify if the LVM stuff is setup correctly since you'd have the original /home data still on the old drive if something messed up. The LVM doc's have more on this and searching a bit on the web will turn up more. I've done something similar for my laptop as I'm slowing moving off of Windows (made the NTFS partition smaller and added the freed space to LVM, then used LVM to add that to /home and finally expanded the file system to use the available space; worked fine and now have an additional 15GB available to my /home).

Jer

---

### Post by rbrugman on 2005-10-24
Thanks!  I got the new hard drive installed.  I am a little confused on the LVM stuff though.  Are there any links or instructions you could give me to get me started?

Thanks again!
Robert

---

### Post by jmcvey on 2005-10-30
I'd start with the how-to ([http://tldp.org/HOWTO/LVM-HOWTO/)](http://tldp.org/HOWTO/LVM-HOWTO/)). It's rather lengthy, but if you understand the basic ideas of disks and partitions than the LVM stuff isn't much different, just different names for similar things. I'd look through section 11 to begin with and if anything in there confuses you then refer back to the preceeding sections. Section 11 gives the commands needed to setup a LVM system, expand volumes, move stuff around, etc. When I get a bit more time I can go a bit more into detail if you have specific issues.

Jer

---

### Post by rbrugman on 2005-10-30
I actually decided to just move my /home partition to the bigger drive and use the old one to store additiona files.  So far I have enough space.  Eventually I'll probably upgrade my server again and put a couple of 500GB SATA drives in it.

Thanks though!

Robert

---

