---
title: "Reinstalling Windows XP without messing up Linux"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by seraph741 on 2006-09-29
Hi,

I have a problem with my Windows XP that requires me to reinstall it.  I am currently dual booting XP with ubuntu.  I am just looking for some instruction on how to do this exactly.  Is there anything I should watch out for when doing the reinstall?  What about the Master Boot Sector (i'm using GRUB), will Windows XP mess with that and if so, how do i change it back?

Hopefully I gave enough info to get some help.  I would really appreciate some instruction.  Thanks!:)

---

### Post by daller on 2006-09-29
If it's on the same HD, I think you'll run into serious problems!

Windows XP is not actually tuned to enable you to have more than one OS. - For "logical" capitalistic reasons.

I can't help you on this one, I've never had this **"**problem**"**!

While I'm at it! - Why do you want to install XP?

...The reason why I'm interested, is that I'm working on a "SoftwareEquivalents" page (on the wiki)

---

### Post by skymt on 2006-09-29
> **daller said:**
> While I'm at it! - Why do you want to install XP?

He already has XP and wants to re-install it.

seraph741: You should be able to install XP. First, make some free space on your drive using [the GParted live CD](http://gparted.sourceforge.net/livecd.php). Then install XP in the free space, and use [this method](http://www.ubuntuforums.org/showthread.php?t=224351) to restore Grub. Note that this will probably only work with a real XP install disc. OEM "restore discs" will wipe your whole drive.

Obviously, you should back up before trying anything like this.

---

### Post by thephantomlinguist on 2006-09-29
There's a somewhat easier way that I've used multiple times to pull off a winxp reinstall without messing up my ubuntu install.

Before you get ready to do it, open a terminal and type the following:

```
sudo dd if=/dev/sda of=mbr_backup bs=512 count=1
```

Change /dev/sda to the appropriate disk, so that it gets the mbr off the right disk. (It'll generally be either sda or hda)

What that does is make an exact copy of the first sector of your hard drive (also known as the master boot record).

Reinstall windows. When you're done, grab your Ubuntu live-cd and reboot.

Now, here's the slightly tricky part, you've got to mount the drive you saved the mbr_backup to. To do this, open a terminal and type the following:

```
sudo mkdir /mnt/temp
sudo mount /dev/sda2 /mnt/temp
cd /mnt/temp

```

Of course, change sda2 to whatever partition it is you need.

Depending on how you have your system set up, you'll probably have to change to /home/[insert-your-user-name-here]. If you ran the dd command above from somewhere else, just go to wherever mbr_backup is saved.

Now, do this:

```
sudo dd if=mbr_backup of=/dev/sda bs=512 count=1
```

Reboot, and you should be all set.

Not only that, but your old GRUB menu should work just peachy as well.

Hope this helps!

---

