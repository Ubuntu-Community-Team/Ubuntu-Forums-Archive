---
title: "Dual Boot &amp; Bone Head Move - HELP!"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by Scunizi on 2006-11-11
I just done what I have probably been wanting to do for some time BUT NOT YET!  I inadvertantly repartitioned my sda1 drive containing XP.  Fortunatly on rebooting, Grub still shows the menu choices.  I know I have to reinstall windows and hours of MS Money data and the games I like to play in that environment.  But when I do, what will happen to the Grub menu?

What can I do so I don't totally screw up my Ubuntu install (dapper) and the dual boot option.

Here's some info.. 
sda1 80 gig (was winxp)
sdb1 ntfs data partition
sdb3 ubuntu
sdb5 vFat small data partition

I do have on CD, Ubuntu Desktop cd, Gparted cd

Any help would be appriciated.

note: I posted this earlier then looked for it and couldn't find it in the forums.  I hope I haven't double posted.](*,)

---

### Post by ThrobbingBrain66 on 2006-11-12
installing XP will overwrite gru. all is not lost however!

after you install windows, follow this howto and you'll be sound as a pound

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub-install](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub-install)

---

### Post by Scunizi on 2006-11-13
Thanks for that.  I've been reading over the instructions and a couple of the links in them.  It sounds pretty straight forward.  But I've run into another problem I'd almost forgot about.  My XP install disk is an XP Home "upgrade" disk and is not bootable.  It's designed for someone that has ME or 98 already installed.  I'd hate to install ME only to go through the upgrade process.  My 98 boot floppy with cdrom drivers has disappeared.  

So I was trying to think of an inventive way to create a bootable cd with the XP files on it without having to use freedos or something similar.

If you're familiar with these steps maybe someone could give me a thumbs up on the process.

Create iso's of my bootable ME disk and XP upgrade disk.
mount both ISO's using... sudo mount isofilename.iso (directory-in-home) -o loop

At this point I should be able to view the contents of both iso's through nautilus or the command line.  

What I would do is delete the visable files from the ME iso and replace them with the files from the XP iso, with the exception of any files that are visable that are required for the boot process.  

Once this is done I think I should be able to burn the ME Iso with the XP files and proceed with the install.  

Does this sound plausible?

---

### Post by louieb on 2006-11-13
I have the XP upgrade CD also and it is bootable. At some point in the install it will ask you put you win 98 or me disk in so it can verify that this is an upgrade.

---

### Post by Scunizi on 2006-11-14
Well I gave the xp disk a try (boot wise) and low-and-behold :D  it is bootable!  For some odd reason when I tried this in the past it wouldn't boot to the CD.  Maybe bios settings, I'm not sure.  Thanks for giving me the curosity to give it a try.  It's saved a ton of time.  Although I'd still like to figure out how to create a bootable cd for other purposes.. Most things I read assume you already know how to do certain things and skip over the actual steps.... learning curves are fun.

---

