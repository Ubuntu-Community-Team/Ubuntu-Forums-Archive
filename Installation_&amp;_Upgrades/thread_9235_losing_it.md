---
title: "losing it"
date: 2004-12-26
forum: Installation &amp; Upgrades
---

### Post by Staph on 2004-12-26
1.   Downloaded demo - great - played music from XP folders - uploaded pics etc to desktop - everything I want.

2.   Downloaded fullversion - installed ok - but there are little red arrows on hd1 and hd2 and can't get into my old windows stuff at all.

Can I mount my windows partitions using mouse clicks and dragging etc?

Obviously I am setting out to learn how to use shell commands but these first few hours are disappointing - and don't tally with the expectations raised by the demo.

I have had ubuntu test the installation cd as part of the installation routine and it came up clear - but is it likely there is a fault in it anyway?

Happy Xmas and New Year to the Linux community!

---

### Post by raditzman on 2004-12-26
Hello, there's a guide which can help you with that:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by Staph on 2004-12-26
Hi Radzman - thanks for that - I have already spent an hour or two on the guide - and I have a Linux pocket guide as well - so no doubt I will eventually find the solution - but it is heavy going for a  newbie.

What puzzles me is this - just to be sure I have started the live CD again - and there, before my very eyes, are icons for all the partitions on two drives - if I want music I got music - if I want to look in the files I can.

The installed version gives me no access to windows partitions at all - so what's the difference?  There are icons for the drives and partitons tucked away in the system files but they all carry a little red "X" and  can't be activated.

I have a copy of SUSE and I can get to everything in that - but I don't like the style and feel of SUSE nearly as much as Ubuntu.

It would save me some sweat to know that my experience with the installed version is like its supposed to be - otherwise my download might be buggy - but I have no way of telling.

---

### Post by swerner on 2004-12-26
Ok, this is going to get kinda ugly. Ok, first you need to find out if you have NTFS for your windows partition or FAT32. If you're running WindowsXP it's likely thats it's NTFS, otherwise it could be FAT32 (especially in the case of Win98). The downside with NTFS is that Linux can't write to it at the moment, it has read only access.

So you run the following commands (sorry about the ugliness)
```

sudo su 
mkdir /windows
chmod a+rx /windows
gedit /etc/fstab

```
The first line logs you in as root, then you make a mount point directory, then you change the ownership properties such that all user can read the mount point directory. Then you open /etc/fstab for editing. Add the following line to the end of the file
```

/dev/hda1        /windows   ntfs       defaults            0       0

```

Where /dev/hda1 is your windows partition (change for your system), /windows will be the new windows directory (change the name if you wish), ntfs is your partition (change to fat32 if needed). Leave the rest as it is. You also have to make sure there is a blank line at the end of the /etc/fstab file, other wise there may be some error messages. 

Next run the command (while still root)
```

mount /windows

```

An icon should appear on your desktop (it won't appear the next time you boot) and a window appear. If it does not, you can use the gnome file manager to browse to the /windows directory. 

In either case you will have to create a shortcut from the desktop to the /windows mount point (or any sub-directory in /windows).

And I hope this gets you on track to play your music. Enjoy :)

---

### Post by Staph on 2004-12-26
:grin: Hi Swerner - well now I Know! - off to give it a go - many, many thanks!

---

### Post by jobezone on 2004-12-27
Hi, glad you found the solution.
About the diference in the live CD and the Install CD:
Your Install CD is not buggy, our at fault, they actually don't automatically create the necessary entries in /etc/fstab for other partitions as the Live CD does. As an afterthough, it is a functionality bug, as by not doing this, it creates unecessary work for the new user.

About the guide mentioned at the begining, it is a bit terse on explanations, so you can check out the wiki at [www.ubuntulinux.org/wiki](www.ubuntulinux.org/wiki) where these and other matters are better explained.

---

