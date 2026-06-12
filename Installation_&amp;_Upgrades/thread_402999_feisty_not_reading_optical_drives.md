---
title: "feisty not reading optical drives"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by donkyhotay on 2007-04-06
I just upgraded 2 different systems to feisty. One works just fine the other however appears to hang up during the boot process but if I wait long enough (about a minute or so) it will start booting normally. By switching TTY I found that at the part it slows up at it gives 1 of the 2 following error messages:
ata2.00:failed to set xfermode (err_mask=0x4)
or
ata2.01:failed to set xfermode (err_mask=0x4)
and does this about 4 times before going back to 'normal' booting. Once booted the system still doesn't recognize either of my two optical drives. Booting with kernel 2.17.* works just fine without any issues (not slow, optical drives work fine). I would think it was just a flawed kernel issue except this only happens to one of my computers and the other runs feisty with no problems whatsoever. Anyone have any ideas?

---

### Post by wpshooter on 2007-04-06
Is the firmware up-to-date on both of your CD-drives ?

How do you have the drives controlled and jumpered ?

---

### Post by donkyhotay on 2007-04-06
Yes everything is jumpered correctly. Everything works flawlessly with kernel 2.6.17 but has issues with 2.6.20 which is why I would think it's just flawed kernel except my other computer runs kernel 2.6.20 and has no issues.

---

### Post by donkyhotay on 2007-04-07
bumpety-bump...

---

### Post by keko_metal on 2007-04-22
Same problem here. Some setup details

Both Using Kubuntu 7.04

PC Nr One (Updated worked flawlessly, no error)
- 80GB SATA hard drive.
- ATA CDROM jumpered as master

Pc Nr Two (xfermode error on boot)
- 160GB ATA Hard Drive, Primary ATA Controller, Jumpered as master
- ATA DVD+RW, Secondary ATA Controller, Jumpered as master
- ATA CD+RW, Secondary ATA Controller, Jumpered as slave

Seems more like a kernel problem, more than a Ubuntu one.

---

### Post by kotter71 on 2007-04-22
Same problem here.  Installed the most up-to-date kernel available.  Same freeze during boot.  Same error messages.  And I have a very similar setup.  What type of DVD-RW do you have?  I read somewhere that there was a possible issue with Lite-On DVD writers.  Maybe this will shed some more info:

[https://bugs.launchpad.net/ubuntu/+bug/75135](https://bugs.launchpad.net/ubuntu/+bug/75135)

Maybe not?

I simply reverted back to Edgy and I'll wait to see how this evolves.

---

### Post by keko_metal on 2007-04-22
I have a Sony OEM DVD-RW. I found that opening both disc trays while waiting to boot, the kernel stops trying constantly to set up xfermode and continues with the normal process.

---

### Post by chernobyl on 2007-04-22
Very similar issue here.  Hopefully some missing information will come up that will lead to this one being fixed :) 
Upgraded from Edgy, which ran like a champion.  This is a Compaq PIII 900Mhz with 384MB RAM.
After upgrade, I would get a root CLI.  I had to adjust fstab to fix that, but hard drives are OK now.
I still suffer the CD issue!
On boot I get a 3 second hang.  The culprits show up on the message term ( ctrl-alt-f8 ):
```
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x51 data 32 in
```
When I click either optical drive in the Computer dialog, I immediately get the error dialog "Unable to mount/no media in drive" as mentioned above.  No attempt to read the drive occurs at this time whether a disc is inserted or not.
When I insert a CD/DVD, the drive keys up but there is no software reaction.  The drive just does not mount.
Dropping to terminal reveals that the drive just isn't auto-mounting.  The command "mount /media/cdrom" works and allows access to the disc, but Nautilus still doesn't see it.  There's no desktop icon, and the Computer dialog still doesn't read the drives at all.  (I can "umount /media/cdrom" just fine as well.)
Relevant lines from fstab (after my fixing):
```
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/cdrw /media/cdrom1 udf,iso9660 user,noauto 0 0
```
I hope someone finds a fix soon!

---

### Post by eltaito on 2007-04-23
yeah I am having the same problem with my LITE-ON LTR-32123S CR-RW drive...it worked perfectly before upgrading to the 2.6.20-15 kernel...there seem to be plenty of related bugs on launchpad...hopefully there will be a fix soon, this is the first hardware detection problem I've ever had with Ubuntu on this particular computer (have had Ubuntu on this computer since Hoary)

---

### Post by eltaito on 2007-04-24
for my specific problem there is now a workaround  that can be found here:

[http://ubuntuforums.org/showthread.php?t=414002&page=2]("http://ubuntuforums.org/showthread.php?t=414002&page=2")


> There is now a work-round that cures this fault.

Add the word 'irqpoll' (without quotes) to the kernel line in /boot/grub/menu.lst thus:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll

Then Feisty will boot faster, and the Liteon CD burner will be recognised.


that makes my LITE-ON CD-RW drive work perfectly and more importantly removes the hang time while booting.

---

### Post by chernobyl on 2007-04-28
Looks like my problem is a bit different.  My bootup errors have vanished recently (?) but Nautilus still doesn't see media that I insert.  I tried adding irqpoll to the GRUB boot line but it didn't do anything for me.  This might be a problem with Nautilus?  I can still mount/umount from CLI just fine, so I know the drives are OK.

---

