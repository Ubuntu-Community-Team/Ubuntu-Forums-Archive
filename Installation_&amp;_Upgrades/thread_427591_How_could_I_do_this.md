---
title: "How could I do this?"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by etcpool on 2007-04-29
now i have 2 hds one is 20Gbs. with windows xp pro installed (primary master drive) the other one is 40Gbs. with feisty installed (secondary master drive) (which this time really satisfy me with my language (Thai) working (Thanks really to the team!)

what i'd like to know is if one day i happend to want to move my secondary drive (feisty) to be primary drive and make feisty my primaray or only OS booted how could i do this?


i use to do this with edgy, boot into edgy's live cd do something like grub-install /dev/hda but it said something like device is not a block device or something (don't exactly remember) or if i change the BIOS setting to boot the secondary master drive  the boot process hang at Black screen with the ubuntu text and progress bar.


i wanna do this because i just don't want to reinstall ubuntu again since i began to store my personal data on linux side and just don't wanna back it up and restore, back it up and restore everytime, so i guess there should be some esier way about this.


THX in advance :)


etc,

---

### Post by Herman on 2007-04-30
Hello etcpool,
Probably it isn't important whether Fiesty is on the primary master hard disk or not.  I would just leave the 40.0 GB drive with Fiesty on it the way it is. 
If you need more space for data, you could resize Windows on the 20.0 GB drive to a smaller size and make a new ext3 data partition for Fiesty with GParted. Then later if you still need more space for data, then delete Windows altogether and resize the data partition to fill the entire 20.0 GB disk. It doesn't really matter if the data drive is primary master and the Ubuntu drive is secondary master. If you use Grub as your boot loader Ubuntu will boot just as well on either the primary or secondary disk, it makes no difference to Ubuntu at all. Ubuntu is not selfish like Windows, it doesn't care if it isn't in first position. 

If you really want Ubuntu in the first,  (20.0 GB) disk, an easy way to do it would be to install Ubuntu again, (a new copy of Ubuntu) over the top of Windows in the 20.0 GB primary hard disk and then  you would have two Ubuntu's. If you want you could transfer some of data to your new Ubuntu installation and make that your main (home) system. Eventually just use the old Ubuntu in the 40.0 GB disk for data storage. You wouldn't need to delete the older operating system unless you really needed all of the disk space. You could just leave it there as a second operating system in case anything ever happens to your new one.

I hope those ideas will help you,
Regards, Herman :)

---

### Post by timmy007 on 2007-05-01
Hello Team

Don't know if I'm in the right spot to post this Hard disk drive problem ??

I'm only new to the form but I'll give it a go anyway 

Just Installed a new Hard disk Dirve into my ubuntu computer and I'm having problems trying to a user (me) Ownership of the drive.

It Keeps saying I'm not an invalid user  ???

Any ansewers team ???

Its driving me up the wall   

Thanks

---

### Post by Herman on 2007-05-01
Hello timmy007,
You probably just need to chmod or chown the directory in /media the you mounted your new hard disk filesystem in.
To check, do 'ls -a /media'
```
ls -a /media
``` Then apply a command to change the ownership and / or the file permissions for that directory and its contents so you will have the right access. 
What filesystem is in the partition and what was the mount command or etc/fstab line you are using to mount the filesystem?

Here are a couple of really great tutorials on file ownership and permissions, **  tuXfiles** **Home  **-  Linux  help files, tutorials, and tips [http://www.tuxfiles.org/](http://www.tuxfiles.org/)
                   
       Nana Langstead's chmod how to_____________[GO]("http://www.tuxfiles.org/linuxhelp/fileowner.html")
                   
       Nana Langstead's chown and chgrp how to____________[GO]("http://www.tuxfiles.org/linuxhelp/fileowner.html")

Try those and see how you go, if you still have trouble ask and I will try to explain in more detail for you,
Regards, Herman :)

---

### Post by etcpool on 2007-05-09
This may be a bit late

but thanks for all replies :)

finally, i decide to follow the first solution if situation comes one day. hope that would be ok ;) 

still doing dual boot with windows to sync with my graphite and to do some web & graphic designing (photoshop, illustrator, flash ,dreamweaver, indesign). Otherwise i would love to use linux purely.

Thanks again.


sincerely 


etc, :)

---

### Post by timmy007 on 2007-05-12
Hello Herman

Sorry for the late reply 

Thanks for you help 

It works like a treat I can now write to the drive :KS 

thanks again 
timmy007

---

### Post by Herman on 2007-05-12
Okaaaay, great! Thanks for your feedback, all the best timmy007, regards, Herman :)

etcpool, that should be okay, all the best, regards, Herman :)

---

