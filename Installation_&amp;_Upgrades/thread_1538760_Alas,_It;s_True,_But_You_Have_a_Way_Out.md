---
title: "Alas, It;s True, But You Have a Way Out"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-07-25
I suspicioned somethine months ago, but for the first time set out to prove it yesterday.  My suspicions were dead on, but you can work around it if you care to.

I was setting up multiple partitions and installing different distros of Linux on each, and later just different versions of Ubuntu.  It always started out fine, but each new install ran into strange, then stranger problems, and when I went back to the earlier installs, they were all messed up.  I could not quite understand why, but there had to be some sort of interplay between them.  I just didn't know what it was.  Since there is only one install or OS involved at a time, it had to be something at the stored file level.  But what?  And how?

I got more information over time, like how a screwed up install cannot be fixed by simply reinstalling and leaving the /home folder and contents intact.  That is where the user accounts lie, and also much of the user settings.  Mess those settings up, you pretty much have to start over from scratch.  I read posts from people that were proud to also designated a /home partition, one that could be shared among multiple installs.  Why?  Installs are not all alike you know, and what might work as a setting for one distro or version might not work so well for another.

Tht is when it hit me.  The installer will respect and leave intact /home if you do a manual install but specify a non-reformat.  That could be the hold over that meant you cannot do a reinstall while always avoiding a reformat.  You need some sort of tool to force all config settings back to a neutral or default setting for that to work right.  Then it came to mind:  What if the esistence of even one /home on any partition was by default the /home used with new installs on other partitions?  That would explain a lot.  So I wrote that up in its own thread as something that might be getting in the way of things.

Why not have a /home partition?  Because tings are different with each distro and each version, so the only ones that find this beneficial are those that choose to have only one distro and version on their PC to call on.  They could also have one or more versions of DOS or Windows for that matter, but these are entirely different and give no special meaning to a folder named /home.

But this was just a suspicion, I had not tried to prove it.  My first question was, how can I prevent this from happening if true?  It might ntot be convenient to copy a /home and everything in it to another partition or backup medium, and of course this would have to be applied to all the prior installs to protect them as well.  And if I leave the /home on any partition to be found, it then becomes the /home for this install as well, which is not what we want.  Okay, let me put it this way:  It is not what I want.

I could use the trial mode of a LiveCD, before and after the install step, and see what is really happening.  Good idea, only the trial mode is dummied up with a false / which sits on top of /ubuntu/ which hides and avoids a lot.  But the Terminal mode and sudo -s gets you around that.

I thought about renaming /home to something else on all the paartitions that have it.  There is a rename command. but it goes global rather than to any specific file, so it was out.  I thought about setting up a new subfolder, maybe call it /rhome, and copying the original /home into it.  But that still leaves the original /home to be found, and copying all the user accounts and contents could take a long time and requre a whole bunch more partition space, and then you have to copy it all back the other way.

This works. and it is true that if you have an exiating, recognizable /home on any partition, that becomes the /home of your newest install.  To fight against this, you cannot create a "/home" yourself, because that means the installer won't put the stuff in there that it needs to if there just was no /home to begin with.  You cannot copy over an existing /home and all its contents, because the configuration setting were right for the other install and likely wrong for this one.  You can't delete the initial /home, because that then prevents the other install from being bootable when you try to go back to it.  Yoy can rename it temporarily, but that is not so easy in Linux.  It is just better to create something like /rhome on the same partition and move /home into it for the time geing.

Here are the commands you will likely need, but you will need to be able to use thme with some understanding of what they do because you have to know when to use them.

Terminal # find this usually under Applecations/Applications
$ sudo -s # typed, geives you root powers so that you can do more
# gparted # typed, lets you see your drive structure and make changes
@ apt-get install gparted # typed. sometimes needed if gparted missing
# mkdir /media/a1 # typed.  Becomes temp mount point for /dev/sda1
# mkdir /media/a2 # typed.  Becomes temp mount point for /dev/sda2
@ mkdir /media/b1 # typed.  Becomes temp mount point for /dev/sdb1
# mkdir /media/b1 # typed.  Same story.  gparted showed you what you need
# mount -t ntfs-3g /dev/sda1 /media/a1 # typed.  loads NTFS file system
# mount -t vfat /dev/sda2 /media/a2 # typed. loads any FAT file system
# mount -t ext3 /dev/sdb1 /media/b1 # typed. loads an EXT3 file system
# mount -t ext4 /dev/sdb2 /media/b1 # typed. same for EXT4

Of course you could have just clicked on each drive under Places to get it to come up, then used
# dir /media # typed, to see what temp mount poirt was created for each,
followed by something like 
# dir /media/labelsda1 # typed. to see what shows up under its root.

Now if it is a linux install, it will look much like this:

bin    dev   initrd.img      lost+found  opt   sbin	sys  var
boot   etc   initrd.img.old  media	 proc  selinux	tmp  vmlinuz
cdrom  home  lib	     mnt	 root  srv	usr  vmlinuz.old

It it is a whole lot different, which it would be for DOS or Windows, then not to worry.  It ia only a concern if it is a Linux file system on that partition and has a /home directory, as this one does, bottom of second column.  This then would be a partition of concern if I were planning to install again to another partition.  So how do deal with it?

Easy enough. This will do it:

# mkdir /media/b1/rhome # typed. Assumes on /dev/sdb1 in this case.
# mv /media/b1/home /media/b1/rhome # typed. Now structure appears /rhome/home in place of the previous /home.  Present versons of the Linux installer will miss that.  Even if someone decides to check for a stash of /home somewhere in the entire structure tree, the chances are that you could beat them.  For instance, just move the entire contents of /home out and into something like /misc, in this fashion::

# mkdir /media/b1/misc # typed.name it pretty much what you want
@ mv /media/b1/home/* /media/b1/misc/ # typed. Just moves the contents
# rmdir /media/b1/home # typed.  Make /home just go away for awhile.

Now you can go ahead with your install, with some confidence that when you do a dir or ls of the new partition, you will also see a home among them.  But now what?

Don't bee in too much of a rush to reboot yet.  The LiveCD mode can still be of some service.  If this was your last install, at least for the time being, you have a few things to undo first, lik3 either moving /hom3 out from behind /rhome, or recreating /home amd moving the contents of /misc back into it.  Here are those steps in the process.  Of course you have to go through the whole sudo -s and mount sequence again for each partition. but you might be getting the hang of that now.

Tjos will jist move /rhome/home back to /home on drive /dev/sdb1:

# mount -t ext3 /dev/sdb1 /media/b1 # typed. All mounts undone by install.
# mv /media/b1/rhome/* /media/b1/ # typed.  it's done
# rmdir /mediab1/rhome # typed.  /rhome has served its purpose.

The method with the /misc is slightly different:

# mount -t ext3 /dev/sdb1 /media/b1 # typed. need to work with mounted partition
# mkdir /media/b1/home # typed.  Put a new one in place of the old one
# mv /media/b1/misc/* /media/b1/home/ # typed.  Not hard at all.
# rmdir /media/b1/misc # ryped.  That completes it.  .

Something like this could be scripted easily enough, but then you would have to port the script about and load it each time.  Still, it is your call.

Another good place for cripting might be to modify /etc/fstab to include mount instructions for all the partitons, or exclude certain ones, or whatever.  Speaking of which, why not script exact methods of finalizing entries in the grub process so that it never gets so screwed up that you can't boot into at least one working Linux partition?  I leave Windows out in tis regard, because the only think Windows is going to do to help in this regard is fix the MBR on occasion.  Speaking of which, maybe a Linux method of patching the MBR is due to be scripted as well.

What's scripting?  Ask a DOS programmer or expert uua=ser what batching is.  That might give you some idea

---

