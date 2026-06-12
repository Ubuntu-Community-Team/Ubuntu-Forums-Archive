---
title: "moving the /etc folder after install?"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by jakerman999 on 2010-03-07
I've been setting up a media server on a an actual server machine  I picked up dirt cheap, and had it running xUbuntu fine.  gave it a 5gig root directory, 5gig swap partiton, and three 34gig storage drives.  Everything was running smoothly.

Just recently I learned that the 5gig's dedicated to running my operating system of choice, aren't enough to install all the software I wanted(I might be just a little greedy).  The first logical step to correcting this problem was to move /etc to one of the storage drives and create a link were it was, but not being entirely sure how xUbuntu would take that, I thought I'd get an expert opinion.

Thoughts or alternative suggestions?

p.s.  The thread prefix is "all variants" because I have installed the desktops for kUbuntu and just plain Ubuntu on this machine(what I meant by being a little greedy).

---

### Post by Barriehie on 2010-03-07
Nm!

---

### Post by diesch on 2010-03-07
/etc is needed during the boot process before any partion other than / gets mounted so it needs to stay on the root partition. As it isn't big it doesn't make much sense to move it anyway.

Better move /usr or /var to a bigger disk.

@Barriehie: /etc/ has to be there for /etc/fstab to be read by the system so it's to late to include it there.

---

### Post by jakerman999 on 2010-03-07
> **diesch said:**
> /etc is needed during the boot process before any partion other than / gets mounted so it needs to stay on the root partition. As it isn't big it doesn't make much sense to move it anyway.

Better move /usr or /var to a bigger disk.


I was under the impression that /etc was where programs and packages were installed to, and that is currently what's taking most of my 5gigs of space(nothing in the home directory).

Edit: checked in the properties, and found that /var is indeed larger than /etc.  Roughly 100x larger actually. So how exactly does one go about moving that?

---

### Post by Barriehie on 2010-03-07
> **diesch said:**
> /etc is needed during the boot process before any partion other than / gets mounted so it needs to stay on the root partition. As it isn't big it doesn't make much sense to move it anyway.

Better move /usr or /var to a bigger disk.

@Barriehie: /etc/ has to be there for /etc/fstab to be read by the system so it's to late to include it there.

Makes sense!  I've edited my post thank you!

OP; I've moved my /var and it's right about 300 megs, /etc is right about 40 megs.

---

### Post by diesch on 2010-03-07
/etc/ is for config files and such. On my system it's 32MByte... Usually most system files are in /usr/. 

You can use e.g. baobab to see how much space each folder takes.

---

### Post by jakerman999 on 2010-03-08
So how would I go about moveing my /var folder without damaging my system?

---

### Post by Barriehie on 2010-03-08
> **jakerman999 said:**
> So how would I go about moveing my /var folder without damaging my system?

Here's the way I did it.  I had booted from the subergrub LiveCD since I was making the swap larger and in that extended partition I created another partition about 4 gigabytes in size.  Gparted assigned it /dev/hda6.  I then did a normal boot and su'ed to root.
Now: (Note that your fs type may/may not be ext3 - depends on how you formatted it)
```

mkdir ./varr
mount -t ext3 /dev/hda6 ./varr
rsync -av /var ./varr
```
Just to be sure next I cd'ed into ./varr and made sure it looked like /var
Then:
```

umount /dev/hda6
rm -rf ./varr
```
Next I used nano, any editor will do, to add this line to my fstab file:
```

/dev/hda6       /var            ext3    rw,auto,user,exec       0       2
```

Now reboot.  Only thing I can recommend doing different from what I did is to check the permissions on the /var folder and files before editing /etc/fstab.  My /var dir is mounted at boot time for read/write, auto-mount, any user can mount, and programs can run from there.  Maybe not necessary to have the **exec** flag but better safe than sorry and it worked!

HTH,
Barrie

---

### Post by jakerman999 on 2010-03-13
Nearly broke my install with that one.  The dummy currently sitting in my seat had copied /var to the /var/var folder of the new drive, but got it figured out in the end.

I'm looking at my hard drive space, and seeing that I haven't gained any space from moving /var. I'm guessing that the folder is still there, just hidden by the mount.  If so, how would I remove it?

---

### Post by efflandt on 2010-03-14
You should have made the changes by booting from some other system or Ubuntu live CD.  Although, you have to be careful then because the **var** you would be working with would not be /var, it would be /media/something/var and destination would have been /media/something-else/var.

After you copied the files to the other location, you should have recursively removed files from the old var.

If you used fstab to /var, you could probably still see the old /var directory by booting Ubuntu live CD (since it would not use that fstab).  Just be aware that it will be /media/something/var from there.  You still need that empty var as a mount point.

[COLOR=Red]Be very careful about using wildcards[/COLOR] for rm, because recursively removing * could also remove everything in ".." (parent directory).  Always test any file definitions that contain * using **ls -al** whatever first.

---

### Post by jakerman999 on 2010-03-15
Booted into a live cd and cleared /var (to avoid the wildcard I launched gksudo nautilus) then initiated a reboot.  Once again I found myself trapped in the recovery console trying to figure out what I did wrong.  Three hours, can't find a thing wrong with my system so I give up and shut it down for the night.  

This morning when I booted it up, everything's fine.  what in the name of hades happened?  I've run a system diagnosis and everything appears fine, so I guess it's running smoothly again.  Thanks for the help, much appreciated.

---

### Post by Barriehie on 2010-03-15
> **jakerman999 said:**
> muted...what in the name of hades happened?...muted

'Bout like my kernel upgrade yesterday.  Shut it down this AM and when I booted after work grub had all the partitions wrong and then I couldn't remember how to 'sudo' via the livdCD.  Got it figured and booting.  I think it's time to quit 'updating' the box that works.

---

