---
title: "losing documents during install?"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by simongraves on 2010-07-02
Hello benevolent community,

I've been trying to upgrade my girlfriend's old thinkpad from 9.x to 10.4, from the update manager.  Something hung up during the install, or maybe it was aborted prematurely, and when I saw the screen next, it was frozen on a screen of text, the last of which was "checking battery state".

When I restart the computer it runs through its processes and always hangs up at that "checking battery state" screen.

So I figured, OK, I need to reinstall.  I used a different computer to download and burn an installation disk.  I can boot from that disk without hindrance.  I started the process of installing the operating system and the installer eventually told me that I currently have 10.04 installed on the hard disk.  It asked me if I would like the new install to share the disk with the old (and presumably damaged) install, or would I like to erase the disc and start afresh with only the new install?

This raised a red flag for me -- "What about all the documents already on the disk?  Will they be erased during install?  How do I get to those so I can back them up before proceeding?"

So I aborted the install and rebooted from the CD to be able to navigate through the system and find all the documents I want to save.  But when booting from the CD, I couldn't find the documents anywhere!  It looks like a clean, new environment.

I'm afraid to continue with the upgrade, for fear of losing her documents forever, but I can't run the computer on its own.  I tried booting through the CMOS and using the various boot options in there with no luck.

So I'd appreciate some advice on:

1) Where are my girlfriend's documents and how can I get to them? (Most important)

2) If I do a full 10.04 install will it really erase the disk or is it just talking about the portion of the disk that houses the OS?

3) Any sort of guiding inspiration to give me a better idea of how to proceed.  All I care about is recovering a few Open Office documents.  Once those are out I don't mind wiping everything and starting from scratch.

Thanks!

Simon

---

### Post by oldfred on 2010-07-02
Use full disk will erase everything and install a nice new clean install, but save nothing from an old install. This is why many suggest a separate /home or at least of full backup of the home folder before any system changes.

To see if any partitions are still on your system:
```

sudo fdisk -l
```

If it is gone testdisk may get some or most of it back. But lets see if your old install is still there.

---

### Post by simongraves on 2010-07-02
Thanks, Oldfred.

You mentioned the HOME folder and I went looking for it.  I found a disk in the Places column called "29 GB Filesystem".  This must be the old files!  In there is a home directory with everything in it.

I'll proceed after backing up and start a new thread if I have more trouble.  Thanks again!

Simon

---

### Post by oldfred on 2010-07-02
I like to label partitions & then they get mounted with the label as a default, if I am not mounted to another name in fstab. The one thing I have noticed is if I label it Data then it mounts again as DATA. You can label in gparted or disk utility (or command line with several different commands)

---

