---
title: "ghost and restore / upgrade to SSD"
date: 2023-03-15
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2023-03-15
I bought my Dell desktop PC in 2016, and it's still going strong.  I'm running Kubuntu 22.04 LTS (upgraded from 20.04 LTS).  It's all set up nicely how I like it.  However, I've realized I would like the speed and convenience of a solid state drive.  Back in my Windows days, I would have used Norton Ghost or Acronis True Image to fully backup/clone my hard drive and then restore it all exactly to the new drive, once installed.  

On Linux systems, I have used Clonezilla, but I've lost some faith in it.  Last time I tried to restore an OS with it, I could not get Clonezilla to see the external hard drive that housed the image of my OS.  Plus, its interface is awkward, or at least it was the last time I used it a few years ago.  Is Clonezilla still it for ghosting/cloning a hard drive in Linux?  Or are there other options that have come along since I did this?  If I had to, I could, of course, just install Kubuntu from scratch, but that would add a lot of additional work getting it all set up.  I like my current setup.  You wouldn't believe how much stuff is customized.  It would be wonderful if I could replace my hard drive and have everything back the same on my new SSD.  

Is Clonezilla still it?  Or are there now better Norton-Ghost-style apps for Linux?

---

### Post by TheFu on 2023-03-15
Imaging only works if the native sector sizes of the storage are the same.  If they aren't, you'll end up with allocations that aren't aligned.

The best way I know to migrate from 1 disk to another is to use your normal backup and restore method.  You know, the one that you test every year so you 100% know it works.

My backup/restore process doesn't use images for a number of reasons.  Mainly because the same backups are leveraged for stolen equipment where I can't assume the replacement equipment is identical.  My restore process begins with a minimal install of the Ubuntu flavor on the new hardware. Most of the time it takes about 30-45 minutes to have the new system working with my data, all my programs, with all my settings.  Plus, because my backups are versioned and don't include the OS/programs, I can easily have 90-180 days of daily backups without using more storage than can easily be afforded.

Example backup commands: [https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)
How to Restore backups: [Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927)

For typical desktop users, getting their entire $HOME directory and the list of installed packages (apt-mark) in the backups is sufficient.  I grab /etc/ and /usr/local because those directories could have important settings that need to be referenced.  In general, it is a bad idea to blindly copy the backup version of /etc/ to a newly installed system.

If you have customized themes or fonts outside settings in your HOME, then you'll want to get those areas too.  Only you know what's important.

---

