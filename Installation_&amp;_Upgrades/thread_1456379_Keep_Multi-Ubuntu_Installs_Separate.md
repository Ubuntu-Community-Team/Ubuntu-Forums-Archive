---
title: "Keep Multi-Ubuntu Installs Separate"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-04-17
I mentioned on several occasions that it looked like additions installs of Ubuntu after the first soemhow got some of the subfolders crosses, or something like that.  It was because each install gave me something different to try and straighten out.  I was just trying to figure out a possible cause, and that is what came to mind.

So here is an easy way to make sure that each install of Ubuntu that goes to a different drive or partition does not mess with any previous install.  You have to maask of the previous installs, which are distinguished by the subfolders under root.  And the LiveCD gives us two opportunities to first do this, then to put everything back as it should be.

Okay, you plan to install, but you begin with running the LiveCD first.
You use System/Administrative/Partition Editor to idenfity all the drives and partitons where you have or will have Linux.  Note these down.

Now you want to access each of those.  To do this, use Terminal mode and become super user by sudo -s, and that is it.  On LiveCD, no password is required.

For each of the drives or partitions noted, put a mount point in /media. I did it this way for my in-law's PC:

mkdir /media/a2
mkdir /media/a3
mkdir /media/b3

Then you mount the corresponding drive:

mount -t ext3 /dev/sda2 /media/a2
mount -t ext3 /dev/sda3 /media/a3
mount -t ext3 /dev/sdb3 /media/b3

You can now use the dir command to see which, if any, harbor a prior install:

dir /media/a2
dir /media/a3
dir /media/b3

This would be a typical list of the files and folders displayed:

bin    dev   initrd.img      lost+found  opt   sbin	sys  var
boot   etc   initrd.img.old  media	 proc  selinux	tmp  vmlinuz
cdrom  home  lib	     mnt	 root  srv	usr  vmlinuz.old

Finding these, is is a simple way to mask them off while the new install is taking place on a different drive or partition:

mkdir /media/a2/aa         'aa is the name of a temporary folder
mv /media/a2/* /media/a2/aa 'move everything from / into /aa

You will get an error because /aa cannot be copied into /aa.  But everything else will move just fine

Now we want to put one back where it was, which is /boot.  Grub needs to know where any boot processes are located, and we do that this way:

mv /media/a2/aa/boot /media/a2

Now we continue with the install process.  At the end, we have a choice of continuing to test, or reboot.  We need to pick the option to continue

Now for each drive or partition that we had altered, we do this to put things back.  Enter the Terminal mode again and use sudo -s

now we do this:

dir /media/a2

If we only see aa and boot there, this is one we changed.  So now we do this:  mv /media/a2/aa /media/a2

This moves everything back.  The one thing left is to get rid of aa, which we do like this:

rmdir /media/a2/aa

Of course I used /media/a2 repeatedly here, but you would use whatever mount point you set up for the drives or partitions involved.

That's it.  you can unmount the drives or partitons, or just exit the Terminal mode and do a reboot.  I worked it out, tried it, and it works.  My second install is as good as the first, and the first is uneffected by the second.  Now to go this route, I also use the manual method with partitioning, so I can tell the installer exactly where and what to use for each install.  If you don't include this method in the process< I have no idea what your result are likely to be.  I suspect it will be something less than what you hoped for.

---

