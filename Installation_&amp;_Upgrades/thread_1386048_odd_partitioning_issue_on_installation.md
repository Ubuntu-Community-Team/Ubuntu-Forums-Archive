---
title: "odd partitioning issue on installation"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by flash722 on 2010-01-20
Hello,

I'm attempting to install Ubuntu 9.10 on a Dell c640 laptop, dual booted with an existing Windows XP system.  I have backed up the XP system and booted the ubuntu CD.

I go through the steps and when the partitioning section comes up I choose to have Ubuntu install itself "side by side" with XP.  I have roughly 12 GB free on the drive but the installer only sees around 9 GB.

The installer starts to "re-partition" and cranks around for about 2 minutes and then pops up with an error (something about not being able to perform the requested task).  When I backtrack OR move forward from this point the installer now only gives me the option to overwrite the existing partition and does not indicate that there is free space on the partition.  

This continues until I reboot into Windows (for some reason the boot-loader installed successfully) and then reboot the CD.  At this point the installer again gives me the option to install "side by side with XP" and the whole cycle starts over.

Suggestions?  I really want to get Ubuntu installed but I must run a dual boot due to a couple business apps that will not not under an emulator properly.

Thanks!


Adam

---

### Post by darkod on 2010-01-20
You have to be careful with the selection in step 4. I don't have too much experience with it, but from what I've noticed:

1. You only use "side-by-side" option if you want ubuntu installed ON the windows partition. In that case it will shrink the windows partition to create free unallocated space and install ubuntu there. This option involved resizing the windows partition and on the bottom bar showing how the setup will look like, you can see the gray slider to select how much to resize.

2. If you have unallocated unpartitioned space (not belonging to any partition), usually the option you want is "Use Largest Available Free Space". As the name says, it will install itself in this unallocated space you have.

If I understood you correctly, you already have 12GB unallocated space that you want to install into, so just ignore side-by-side and try Largest Space...

However, the failed install might have already resized your XP partition so I would suggest to boot into the live desktop first and use Gparted to take a look how is your drive looking right now. Or use XP disk management tool to look at it.

---

### Post by oldfred on 2010-01-20
When you say you have 12GB free, is that in windows. Windows needs about 10-20% free space to work. If you make it too small it may run real slow or stop working. Definitely houseclean old applications and defrag twice before you do the install.

---

### Post by flash722 on 2010-01-20
Hmmm....   well. . a little more info then.  I now understand why Ubuntu only found the 9GB (because of XP's reserve space).  

Currently the disk is partitioned as a single for running XP.  Hence maybe, why I only saw the two options (side by side or wipe it clean).

Will the partition software in the 9.10's installer shrink the XP partition and create another one (say, using the 9GB) for installing Ubuntu?

Or...   should I wipe the drive, re-partition it to say 25GB and 15GB (40 GB total) and then restore my XP system back to the 25GB and then install Ubuntu on the new 15gb?  

Would like to leave my XP system intact if at all possible (except maybe for reducing its size since I have a network HD for storage and really don't need to keep much data locally.

Incidentally, do any of you happen to know how much space I really need to run XP-SP3?   Ubuntu for that matter?

Adam

---

### Post by darkod on 2010-01-20
> **flash722 said:**
> Hmmm....   well. . a little more info then.  I now understand why Ubuntu only found the 9GB (because of XP's reserve space).  

Currently the disk is partitioned as a single for running XP.  Hence maybe, why I only saw the two options (side by side or wipe it clean).

Will the partition software in the 9.10's installer shrink the XP partition and create another one (say, using the 9GB) for installing Ubuntu?

Or...   should I wipe the drive, re-partition it to say 25GB and 15GB (40 GB total) and then restore my XP system back to the 25GB and then install Ubuntu on the new 15gb?  

Would like to leave my XP system intact if at all possible (except maybe for reducing its size since I have a network HD for storage and really don't need to keep much data locally.

Incidentally, do any of you happen to know how much space I really need to run XP-SP3?   Ubuntu for that matter?

Adam

If 15GB is all you can spare (and on 40GB hdd it sounds right), ubuntu will work on that. Of course, more is better, but ubuntu and software you will be adding later are not as much space consuming as windows, so you are OK with the 25/15 idea.

And if you only have 9GB spare at the moment, you wouldn't be able to shrink 15GB from the partition of course. You might wanna take a look and clean up your XP a bit, because you'll need it to fit on approx 20GB, so it has something spare on the 25GB partition planned.
Backing up and clean install is always better than shrinking, because you risk corruption of data and you will need to have a backup before shrinking anyway. Clean install would also involve reinstalling XP software, if you don't mind.
In any case, don't create any partition for ubuntu from windows or in advance, no need really.
For example (if this is the option you select):
You back up your XP data.
Boot with XP install cd, delete the current single partition, create a 24GB ntfs partition and install XP there. Boot XP and make sure it's working fine few times.
Then boot with ubuntu cd, Install Ubuntu option, because the installer will see the approx 14GB unallocated space on the hdd it will offer Use Largest Space... this time, use that and that's it.

I suggested 24GB for XP because the hdd is not 40GB actual size. It's little less measured in real GB, or GiB as some label them (including Gparted).

If you decide to only shrink the XP partition, the above still applies. Leave the newly created space as unallocated, and you can use the Largest Free Space option again. If you decide to do it this way, clear the XP of unneeded items (it must not be more than 20GB in size), defrag XP few times, DO NOT use the side-by-side option to install ubuntu. Boot into live desktop and use Gparted to shrink XP partition to 24GB. Then boot XP few times so it can figure out the shrink and do its disk checks. Only after it's working fine, proceed with ubuntu cd and Largest Free Space option.

---

### Post by flash722 on 2010-01-20
Had to shut off the paging file and defrag the heck out of the drive but it finally shrank the partition.  Installed Ubuntu 9.10.  Appeared to go fine but the system locks up when I try to load various programs.  Argh...   Should I try a different version?  Do I have to "uninstall" or just install over 9.10?

Adam

---

### Post by flash722 on 2010-01-22
Thanks for the suggestions everyone.  Got 9.04 installed nicely.  Now to get the wifi going...   :)

Adam

---

