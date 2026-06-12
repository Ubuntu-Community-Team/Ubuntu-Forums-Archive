---
title: "Boot fails after upgrade - watch out!"
date: 2009-06-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-06-06
I just re-booted after accepting 67 updates, including the -30-8-generic kernel, and the boot process hangs after most of the normal progress messages. No log-in window appears, consoles don't appear, keyboard is dead, and only forced power-off works. (There were no errors during the actual updates).

The kernel log has a segfault message from gvfs-gdu-volume; I did notice some gvfs/gdu related updates in the list, so it may be one of those.

Filed bug report #384405 - meanwhile, any ideas about how to recover? Asking to "fix broken packages" at the recovery console leads to the offer to remove console-tools, but also wants to install another 60 packages.

---

### Post by tad1073 on 2009-06-06
no problems here w/kernel 2.6.30-8 and all the latest updates

---

### Post by scradock on 2009-06-06
That's good! 
Can anyone suggest how I can recover? 

I can chroot into the karmic install from Jaunty, and see the corrupted logs. 

The gvfs updates were gvfs_1.3git20090512-0ubuntu2 and its companions; unfortunately my apt archives don't have any earlier versions in them, and I'm not clear how I can find out the correct versions to force install with dpkg since I can't run synaptic in karmic.

---

### Post by scradock on 2009-06-06
OK, the earlier versions were _1.3git20090512-0ubuntu1. But apt-get says this is not available any more from the karmic repositories. Earlier still, karmic used the same version as Jaunty, _1.2.2-0ubuntu2, which is also not available for karmic, but is for jaunty.

Anyone care to helpme out with instructions for forcing removal of the new versions and replacing them with the 1.2.2 versions from jaunty?

---

### Post by ronacc on 2009-06-06
during the dev process I set synaptic to keep everything (keep all downloaded files in the cache )  it can make it much easier to downgrade if that becomes necesssary . You can clean up the clutter when things get stable .

---

### Post by Nullack on 2009-06-06
You shouldnt have let synaptic upgrade the incomplete gnome gvfs configuration items. Its safer to use apt-get upgrade if your not sure. You will need to wait for the other gnome gfvs configuration items to be upgraded or you need to revert the packages youve partially upgraded.

---

### Post by scradock on 2009-06-06
There was no indication that they were incomplete, was there? Usually that results in the offer to do a Partial Upgrade, which I NEVER accept. 

I always do whatever is marked as upgradeable in Update Manager after I Close the Partial Update dialog, then go to Synaptic to check out which of the upgradeable packages need unavailable things, and which would strip out half the system, and which can be carefully upgraded in Syanptic by bringing in something that wasn't installed before.

Anyway, I'm still stuck - Karmic won't boot to a graphical UI, and I need to know how to get that back so I can be ready for any more updates......

---

### Post by inportb on 2009-06-06
You could always use the CLI to fix your packages until you get your GUI back...

---

### Post by scradock on 2009-06-06
That's right - if I knew the correct commands! I am asking for a couple of lines of code to revert the new gvfs packages to the old ones - I could do it if someone would be kind enough to tell me. I have reverted a package once or twice before, but never without a working X....and I really can't remember the exact syntax, because man dpkg tells me very little.........

How about it, friends?

---

### Post by Nullack on 2009-06-06
mate go through your apt log and remove all gvfs related packages that were upgraded, and grab the last revisions before the new problem ones.

---

### Post by scradock on 2009-06-06
Sounds like sage advice - but I wasn't sure I should be removing the whole of the gvfs subsystem without knowing what I was doing.

Also, what about the fact that the older versions don't seem to be available through Synaptic?

Can I do this sort of system-level reconstruction from a chroot while running on the Jaunty kernel, or do I have to be in a root recovery console using the Karmic kernel?

---

### Post by scradock on 2009-06-07
Ah well, panic over. Karmic now boots, with all the updates properly installed.

Removing gvfs-bin, gvfs-backends and gvfs-fuse and re-installing them turned out to be sufficient - there must have been some unannounced error in the initial update. I tried that from a chroot from Jaunty, and from the recovery console.

It didn't look like a good idea to remove gvfs itself (or libgvfscommon0) - they would have taken out 52 or 53 significant programs as well......

I still don't know how I would have reverted to an earlier version if that had been necessary......

ronacc - where do I set synaptic to cache earlier versions?

---

### Post by Kow on 2009-06-07
```
sudo aptitude update && sudo aptitude **safe-upgrade**
```

is your best friend.

---

### Post by ronacc on 2009-06-07
@scradock open synaptic  go to settings>preferences>files , under temporary files select "leave all downloaded packages in the cache "  . the files cache is in /var/cache/apt/archives , you can veiw a history of what was installed when by going to synaptic>file>history .

---

### Post by jerrylamos on 2009-06-07
2.6.30.8 June 6 Daily Build CD ran and installed on Thinkpad R31, Intel i830 video.  Using it hung up once, par for the course on early Alpha.

Boot fails on ThinkCentre A30 with Intel i845 video.
  
1.  Since it's CD live, hard to see what the failure was.  It occurs after GDM and Gnome start.  It hangs up tight and since all the logs are in memory there's nothing left to look for.  Smells like xorg Intel driver.  The i845 has quite different register setup than the i830.

2.  Since it's CD live, my triple boot karmic, jaunty, intrepid installs still run...doing an rsync on today's June 7 build to see if it will hang or boot.

Jerry

---

### Post by jerrylamos on 2009-06-07
Hey!  Today's June 7 build booted O.K. on the ThinkCentre i845!

If you've got a failed boot on an upgrade, give "fix broken packages" a try - might get you going!  There's a fix on today's build for my problem.

Now to install (hopefully) and see what else is broken....

Oops.  Only booted from .iso image on a hard drive partition.  Can't install from that.  Used to be able to, however now install won't format the target partition if any partition is mounted.  Gparted has no such problem.

Karmic CD won't boot, failed on two different PC's, both with different black screen problems.  Let me try again as Alpha 2 approaches.

Cheers!  Jerry

---

### Post by scradock on 2009-06-07
Thanks Ron - I'll check that out.

@kow - I'm not sure using aptitude would have helped in this case, as there were no markers that the updates were incomplete or inconsistent, and the update concluded with no error messages. I hope it was just a random glitch that got fixed by removing and re-installing the non-essential packages. Just glad I didn't have to remove gvfs itself - takes too much with it.

---

### Post by alphacrucis2 on 2009-06-07
My machine booted ok but I notice after logging in to the gnome desktop that something is repeatedly trying to access the floppy disk drive. I shut it up by inserting a floppy but if I eject the floppy it starts happening again. dmesg shows an I/O error on dev fd0, sector 0 happenning every two seconds. The errors stop if I actually insert a floppy. Curious.

---

### Post by jerrylamos on 2009-06-07
> **alphacrucis2 said:**
> My machine booted ok but I notice after logging in to the gnome desktop that something is repeatedly trying to access the floppy disk drive. I shut it up by inserting a floppy but if I eject the floppy it starts happening again. dmesg shows an I/O error on dev fd0, sector 0 happenning every two seconds. The errors stop if I actually insert a floppy. Curious.

Got the same floppy drive access error.   Something's busted.

Jerry

---

### Post by sparker256 on 2009-06-08
> **alphacrucis2 said:**
> My machine booted ok but I notice after logging in to the gnome desktop that something is repeatedly trying to access the floppy disk drive. I shut it up by inserting a floppy but if I eject the floppy it starts happening again. dmesg shows an I/O error on dev fd0, sector 0 happenning every two seconds. The errors stop if I actually insert a floppy. Curious.

I am also getting the floppy error. I also get the following error when clicking on the "Computer" Icon under Places.


Could not display "computer:///".

Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again



Bill

---

