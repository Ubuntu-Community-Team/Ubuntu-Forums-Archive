---
title: "Windows 7 doesn't hibernate (Ubuntu does)"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by Toci on 2012-07-15
Hello, I upgraded to Ubuntu 12.04 and initially I was going to keep the /home partition from my previous version but it seemed to become encrypted and didn't recognise it, so I made a clean install and seemed to be able to give all partitions (Windows included) read-write permission from Ubuntu.

 But when I try to hibernate from Windows the screen goes black, hibernates, but not the OS.
 From Ubuntu Gnome, if I type ```
sudo pm-hibernate
``` it hibernates perfectly.

 I have to say that I had to edit the partitions several times through gparted-live, because I couldn't boot and also because some partitions didn't work properly.
 Here's what they look like now:

[[img]http://www.freeimagehosting.net/t/fh2rs.jpg[/img]](http://www.freeimagehosting.net/fh2rs)

 Windows' help page says that I should make Win 7 the "boot" option, but it already is.

 I would very much appreciate your help.

---

### Post by darkod on 2012-07-15
Have you tried without mounting the win7 system partition? Why do you have a permanent mount, do you access it from ubuntu that often?

I would remove the permanent mounts of the win7 partition and the recovery partition. You can always access them temporarily if you need to copy something. Windows doesn't like other OSs to touch its partition too much.

Not sure if that can affect hibernation or not.

Also, you need to make sure you never hibernate windows, then try to boot ubuntu. You should restart or shutdown, and then boot ubuntu. Not with windows hibernated.

---

### Post by Toci on 2012-07-15
Darkod, thanks for the reply.

 Okay, so I went to gparted, unmounted, and then using Storage Device Manager unchecked the "mounted at boot time", but it still doesn't hibernate.
 Also the "mount as read-only" for Windows doesn't want to uncheck, even now that it isn't mounted.

 And, I do access Windows from Ubuntu, I even back up windows files from here, because after I lost a windows system I managed to recover everything using Ubuntu.

---

### Post by darkod on 2012-07-15
I am not sure about the hibernate option. Are all the hibernate settings in windows OK?

You can enable or disable hibernate by opening command prompt as administrator and running one or the other command, depending what you want to do:
powercfg -h on
powercfg -h off

I can understand making backups from ubuntu, but my point was that the win7 partition doesn't need to be mounted all the time for that. You don't make backup every second. Just mounted when ever you need.
In fact, for some programs like fsarchiver, the source partition is not even mounted when doing the backup, only the destination partition.

I would never keep the windows system partition mounted all the time. It can create conflicts especially knowing how untolerant is windows to other OSs.

Double check /etc/fstab if there are any entries for the windows partition there. If there are, you can consider removing it or temporarily commenting it out and see if that helps. It all depends how you configured the mounting of the partition, it will depend how to undo it now.

---

### Post by Toci on 2012-07-15
I checked again that nothing was interfering with hibernate, but everything seems fine.

 I went to the command promt, typed the "powercfg -h on", tried to get it to hibernate again, and it's still not working.

 The windows partition is not mounted now, I didn't know that it could cause so many problems, so I'll follow your advice and leave it as it is at the moment.

 Here's what fstab says:

#Entry for /dev/sda3 :
UUID=9ED06370D0634D99                      /media/sda3      ntfs     nls=iso8859-1,ro,noauto,umask=000                                             0  0

---

### Post by darkod on 2012-07-15
If you put the # symbol at the front of that entry, it will consider it as comment and ignore it.

If later you want to start mounting it again automatically, just remove the #.

As far as hibernate is concerned, I have no more ideas. Maybe on a windows forum they can help you better since this is windows hibernation we are talking about.

---

### Post by Toci on 2012-07-15
All right, I'll do that.
 And I'll try to find more options for the hibernate issue on a different forum.
 Thank you very much for all your help.

---

### Post by efflandt on 2012-07-15
Did you change anything with the Win7 boot?  The Dell computers I have experience with typically boot sda2 (RECOVERY which you should have no reason to mount in Linux) which boots Win7 on sda3.

I did not realize that when I was setting a Dell laptop up for someone and temporarily installed Ubuntu with grub on sda4 (without touching mbr) to make it easy to remove.  After I removed Ubuntu and set sda3 as boot partition I had to go through gyrations booting a Win7 system disc several times to get it to boot due to missing files (that were actually on sda2).

Once I got my Dell desktop and looked at that before doing anything, I realized that it normally booted Win7 on sda3 from RECOVERY partition sda2.  I guess that is so you can restore the drive to factory original if Windows messes itself up.

But it could just be that Win7 does not like to hibernate if it does not control the mbr.  I know that a Win7 service pack update would not work until I restored a normal DOS/Win mbr.  I actually have grub2 on sda4 (a primary partition), because originally Dell Datasafe stored data in the mbr which broke an earlier grub2.  Although, currently I boot Win7 or 12.04 on sda or 11.10 on sdb from 11.10's grub in mbr of sdb.

---

### Post by darkod on 2012-07-15
> **efflandt said:**
> Did you change anything with the Win7 boot?  The Dell computers I have experience with typically boot sda2 (RECOVERY which you should have no reason to mount in Linux) which boots Win7 on sda3.

I did not realize that when I was setting a Dell laptop up for someone and temporarily installed Ubuntu with grub on sda4 (without touching mbr) to make it easy to remove.  After I removed Ubuntu and set sda3 as boot partition I had to go through gyrations booting a Win7 system disc several times to get it to boot due to missing files (that were actually on sda2).

Once I got my Dell desktop and looked at that before doing anything, I realized that it normally booted Win7 on sda3 from RECOVERY partition sda2.  I guess that is so you can restore the drive to factory original if Windows messes itself up.

But it could just be that Win7 does not like to hibernate if it does not control the mbr.  I know that a Win7 service pack update would not work until I restored a normal DOS/Win mbr.  I actually have grub2 on sda4 (a primary partition), because originally Dell Datasafe stored data in the mbr which broke an earlier grub2.  Although, currently I boot Win7 or 12.04 on sda or 11.10 on sdb from 11.10's grub in mbr of sdb.

Are you sure it was the recovery partition? It would usually be the small 100MB partition win7 creates which is called System Reserved. Booting the recovery would usually start the factory restore process which you usually don't want.
That small partition can be sda2 if a utility partition is sda1, but  there is big difference between System Reserved and Recovery. Unless Dell has created some weird loop to boot windows through the factory restore.

To the OP: Another idea is to run something like:
chkdsk c: /r

in windows. It might not have liked ubuntu touching it some time, and maybe it considers it "dirty". Run the disk check. It might not help, but it couldn't hurt.

---

### Post by Toci on 2012-07-15
efflandt, no I don't think I changed anything, except for what I mentioned, that all partitions seemed to have gotten encrypted.

 darkod, I disabled "hybrid sleep" and it sleeps and hibernates, but I'll run the code you mentioned to see if there's a problem.

 Thank you both for the help.

---

