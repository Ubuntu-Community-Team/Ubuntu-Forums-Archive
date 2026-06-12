---
title: "Vista/NTFS partition borked after Ubuntu install.. help!"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by JoshPowell on 2007-03-03
So, I've spent a good part of this afternoon trying to get this fixed but I haven't had any luck. 

I downloaded the Fiesty Fawn Herd 5 to try out native Compiz and booted up, headed over to the install icon made it past the few screens to the drive options, chose to resize the main partition (from 230GB to 215) and have it used guided mode to setup the Linux partitions. Hit next and I got some error, can't remember what. So I canceled the install, and eventually rebooted. Vista wouldn't load -- it didn't do anything actually. Just sit there (post POST). 

Sooo... I booted up the live CD again, and looked in Gparted and sure enough there was a nice little exclamation mark next to my NTFS partition. Pulling up the information page showed the following:

**Warning:**
Failed to load $MFT : Input/output error
Failed to startup volume : Input/output error
Couldn't mount device '/dev/sda2' : Input/output error

I've tried a few things but haven't had any luck at all. Booting my Vista DVD and going into the repair options doesn't help, and running chkdsk doesn't work as it sees the type as RAW and won't check RAW. 

I tried the gparted live CD.. no luck with it. (I read somewhere that issues simaler to mine were caused by an older version of ntfsresize being used and that resizing it again with the newest version of ntfsresize would fix it... but the latest version of ntfsresize (with the livecd..) wouldn't touch it.)

I eventually installed Ubuntu to the free space, which might have been a mistake, and I didn't have any luck there either. I'm back on the livecd as the vista repair function removed grub for me and I didn't bother to put it back on.

I'm sure I could format and reinstall Vista but I'd really really prefer not to lose all the data in my NTFS partition and as this was a fairly recent install I don't have a backup of any of it. Is my NTFS partition hosed beyond repair? 

Any help? Please? :)

edit: If it helps, it's a Dell E520 with all the hardware stock. SATA drives.

Here's fdisk -l
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6       27999   224861805    7  HPFS/NTFS
/dev/sda3   *       28000       30288    18386392+  83  Linux
/dev/sda4           30289       30394      851445    5  Extended
/dev/sda5           30289       30394      851413+  82  Linux swap / Solaris

---

### Post by konungursvia on 2007-03-03
You should be able to reinstall Windows while selecting an option to Keep Existing Directory Structure or some such slovo. I've done it a few times, and you end up with (nearly) all your old data there. Some programs' executables won't be in the registry, but they'll still run if you create icons to call them up. Can you try this option with Vista re-install?

---

### Post by JoshPowell on 2007-03-03
I thought I'd try that, but Vista doesn't even see the partition as a NTFS partition and won't give me an option to "upgrade" it. Thanks for the suggestion though.

---

### Post by peedeeramone on 2007-03-11
wow, you're in almost the same boat as I'm in...

welcome aboard

I actually have had my xp install for about a year now and i decided to finally commit ubuntu because I had been wanting to for a while.

I resized my original ntfs partition and set up my swap and ext3 partitions for linux respectively and went through the install fine.  I decided to resize my swap partition because it was originally a little small.  my problem may have been that i had the ntfs partition mounted when i attempted this or something, but either way things got screwed up from there...

Now my ntfs partition is screwed up and couldnt even be recognized as a ntfs partition. On top of that, the swap size didnt grow like i wanted it, and my gnome desktop wont load so i have to use kde.

My ntfs partition has alot of stuff that may not be super important, but there is a whole lot of stuff that i reaaally dont want to get rid of

I tried to run chkdsk using the xp install cd, but it gave me some error like the drive doesnt exist or something...

I used a RIP cd and forced the partition to be called an ntfs partition which it did, but it still didnt help...

so yeah, if anyone can help with this it would be most appreciated

also if the guy who originall posted this gets his problem solved without formatting please let me know

---

### Post by nick122147 on 2007-05-13
I had similar problem and fixed it with ntfsfix (package in ubuntu). then vista fixed the rest itself.

---

### Post by DoctorOwl on 2007-05-13
I didn't resize my NTFS partitions and after booting from the Live CD 7.04 my NTFS partitions were corrupted after I'd mounted them from the desktop.

I thought maybe I'd made some other mistake but the comments here make me think differently.

---

