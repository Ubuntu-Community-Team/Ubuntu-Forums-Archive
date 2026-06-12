---
title: "Upgrading HDD - options for closing existing install"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by justaguy93 on 2008-04-28
I am going to be upgrading the hard disk in my laptop shortly and I know Mac systems have a utility that you can use to clone your existing install on to a new drive so that you do not need to reinstall the OS.  I've done some searches and there seem to be a few options in Linux for this type of thing.  Could anyone share their opinion on what commands or tools are the easiest to use for this situation?  

Thanks!

-justaguy93

---

### Post by kidders on 2008-04-29
Hi there,

There's no reason why you can't simply copy everything from one filesystem to another. In most cases, trying to do anything more elaborate just complicates things unnecessarily.

Since you have a laptop, you may not have the hardware necessary to plug both your new and old hard disks in at the same time, so rather than a straight copy...```
cp -dpR /old /new
```...you might need to do something more like...```
tar cf old.tar /old
mkisofs old.iso old.tar && cdrecord old.iso
...
...
```I'm not sure how much you know about how Linux works, so it's hard to guess how much detail to post.

In general terms though...[LIST]
[*]There's absolutely no reason to have to re-install your OS. It takes long enough to get a Linux distro working the way you like it once ... having to do it a second time would be awful!
[*]In principle, all you need to do is copy all the files in your system from one disk to the other, and you're more or less done. You need to be _very_ careful to preserve all permissions, symlinks, etc. though. If you can't copy directly from disk to disk, you might need to use your network, a DVD recorder, a USB hard disk, or something like that.
[*]You'll need to install a bootloader onto the new disk once you're done, so be sure you know how to do that before you start.
[*]Needless to say, none of this should be done while your Linux install is actually running. A LiveCD or a second Linux installation are essential.
[/LIST]

If you like, I could give you more precise suggestions (ie post something that might actually be *useful* to you!). Post the output of **df -h**, and maybe a little about how you'd like to move your stuff from one disk to the other.

(Incidentally, I take it the old and new hard disks won't be the same size.)

---

