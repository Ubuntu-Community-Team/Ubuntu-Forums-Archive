---
title: "Unable to boot (fsck test fails, cannot login after that) =("
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by Jango on 2006-02-28
Hi!

I cannot boot my kubuntu, here what happens after system starts up:
[http://img398.imageshack.us/my.php?image=img02972gc.jpg](http://img398.imageshack.us/my.php?image=img02972gc.jpg)

The last line says:
"Give root password for maintenance (or type Control-D to continue):"

The problem is that my password does not work and i cannot login to run fsck manually. What should I do?

Thanks! :)

---

### Post by joshuapurcell on 2006-03-01
Have you been able to boot into this installation before? If this is a fairly new install then I would reinstall and see if the hard drive continues to have problems. You could also try to select the recovery mode kernel in the grub menu before the OS loads (get there by hitting escape during the beginning of boot process after POST). You could also use a liveCD or installCD and then run fsck while in that environment.

---

### Post by Jango on 2006-03-01
No, that's not a new installation, I've being using it for several weeks. Is there any other way to get root privileges and run fsck? I have only installation CD, and I have dial-up so it's pretty difficult to download a LiveCD. 

Thanks for advice, though!

---

### Post by joshuapurcell on 2006-03-01
The only thing I can think of right now is to boot up using the 'recovery mode' kernel (mentioned above). Press escape during the GRUB menu and choose the appropriate kernel. It should automatically log in as root (single-user mode), but I'm not sure if that is before or after the system will need you to run fsck... hopefully before.

---

### Post by Jango on 2006-03-03
It doesn't work =\ But still, thanks for advising :D

---

### Post by cadumg on 2006-03-13
Did you solve it ?

I've had the same problem, after restoring the linux partition with Norton Ghost.

---

### Post by simbart on 2006-03-14
did you ever solve this i have exactly the same problem..unable to login presumably because the boot process has not gone far enougth to enable the whole sudo thing so there is no root password, or something!!

would it be possible to use a live cd to repair this..
something along the lines of booting with a livecd
mount file system
and then run fsck..

if any of you clever fellows would be able to give more specific instuctions on doing somthing like this, i would be most gratefull, i'm a bit out of my zone..

thanks
simbart

---

### Post by simbart on 2006-03-17
well i'll post a response just incase someone else has the problem, its pretty straight foward really..

boot up with a ubuntu live cd
open a terminal
sudo -i
fsck /dev/hdc*

replace * with the appropiate number for partition /dev/hdc2 for my system..

job done, reboot, hoorah!!

simbart

---

### Post by Scunizi on 2006-03-23
simbart.....I'm having the same problem. I've booted from Live CE and followed your instructions.  It looks like it's doing something but there is no evidant HD activity.  I had to replace hdc with what I knew was the root partition that seemed to have a problem.  The replacement was sdb3.  After initiating fsck /dev/sdb3 the screen returned with "/ has been mounted 26 times without being checked, forced check" then "Pass 1: checking inodes blocks and sizes."  Then the cursur drops to the next line without any prefix and nothing else appears on the screen and no HD light to indicate activity. ](*,)   So what's up?  I'll attempt to reboot and see what happens.  If the same thing again I'll go through your inst. again and let it run.  Any further input would be greatly appriciated.

Edited Note:  Tried rebooting and fsck ran again.  Same problems on sdb3, SCSI pairity error in block xxxxxxxxxxx, and other things.  The same basic message over and over with only a change in the block and sector numbers.  I'm running a P4 2.4 dual boot w/XP.  XP is on the primary (but smaller) drive and is set up in the bios as the 1st drive to check after the CDRom.

As a last resort I can always reinstall by deleting the partitions for ubuntu and having it automatically repartition... again.  This is the second time this has happened... eeerrgg

---

### Post by cyphereza on 2006-09-24
I managed to repair my /dev/hda1 using FSCK (on Gentoo LiveCD).
I feel like my pc has a lot of 'wasted' data after running FSCK. Correct me if I'm wrong. Thank you.

---

