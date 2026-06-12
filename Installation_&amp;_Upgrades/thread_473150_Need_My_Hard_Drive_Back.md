---
title: "Need My Hard Drive Back"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by odista on 2007-06-13
I installed Kubuntu recently.  When I booted up to Windows, I discovered to my horror that I only allocated 20 gigs to its partition.  I meant to allocate 20 gigs to Kubuntu and somehow ended up doing that to Windows instead.

I uninstalled Kubuntu by doing the "fixmbr" command in the Windows recovery console.  I then deleted the Kubuntu partitions by using disk management.  I now have have over a 120 gigs of free space that I can't access through my current Windows partition.

How do I get the rest of my hard drive back into a primary partition without reformatting the entire drive?  Thanks for your help.

---

### Post by aaronc222 on 2007-06-13
I'm going to assume this is XP (although it should work in Vista):

Right click 'My Computer' -> Choose Manage -> go to Storage(on the left) and choose Disk Management

You should now be able to figure the rest out on your own. ;)

---

### Post by azndreamer781 on 2007-06-13
go search for gparted live cd and burn it on a cd and boot it on ur comp and it easy to use and self explain. and when it boot or ask u question for how to boot just keep pressin enter.

---

### Post by aaronc222 on 2007-06-13
> **azndreamer781 said:**
> go search for gparted live cd and burn it on a cd and boot it on ur comp and it easy to use and self explain. and when it boot or ask u question for how to boot just keep pressin enter.

Why go through all the trouble, he stated that his windows is working. If it were broken and he couldn't get to the built in partition tool, sure a gparted disc would be great(and he should probably even create one anyways 'just in case'), but if he's already in Windows, he can partition the drive in about 5 clicks.

---

