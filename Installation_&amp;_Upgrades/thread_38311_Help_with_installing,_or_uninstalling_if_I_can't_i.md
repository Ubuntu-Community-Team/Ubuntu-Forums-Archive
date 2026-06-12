---
title: "Help with installing, or uninstalling if I can't install on a second HDD."
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by DAXP on 2005-05-30
I've been trying to install Ubuntu on a second HDD in my PC. Whenever I get to the partition part, it gave me some errors, such as some input/outport error. Because of this I cannot partition the HDD. So I tried to install Ubuntu onto a Pocketec Datastor, a little external HDD with 80GB. Installation worked, but upon reinstalling I get Grub Error 21. Because of this I can't get into Windows or Ubuntu. Right now I'm using SLAX, since I had some CDs of it lying around. Because of this I cannot acess my HDDs, nor can I download anything or burn any CDs. I think. It hasn't worked when I tried to download stuff... So if I can at least get Windows back, I'll be fine, but I really want to have Windows and Ubuntu, if someone can help me.

---

### Post by codejunkie on 2005-05-30
if you have a windows cd laying around you could throw it in and choose the recovery console option and type fixmbr that should get windows up and running. i have no idea how to fix the grub error but this should help you at least get windows up till you can fix the grub error hope this helps.

---

### Post by DAXP on 2005-05-31
Unfortunately I've lost my Windows CD. I've looked through my room countless times, but to no avail. If it comes down to it I'll order another copy from Newegg, though I'd perfer not to do that...

I think I know what the Grub error is though. I googled it, and it means that Grub can't find one of the OS's disks. So, apparently, my BIOS doesn't support booting from USB HDDs, or it does but it's turned off. Hopefully it's the latter, but I have no idea how to check...

EDIT: For some reason I can now access the Datastor HDD. So if I need to edit any files gained from installing Ubuntu, I can. However, it's still acting as if my internal HDDs aren't there...

---

### Post by mingus on 2005-05-31
You don't indicate which version of Windows you have.  If it is XP, look at:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;305595](http://support.microsoft.com/default.aspx?scid=kb;en-us;305595)

If another version, search on MS support site similar topic name.  Basically you are just creating a DOS floppy with the limited command set which allows you to execute the fixmbr command.  That will restore the MBR and you will then boot into Windows.

What to do next gets a bit complex.  As I understand your post, you attempted to install on a second internal HDD but that failed.  So you installed on a different external USB HDD.  When you booted, you got the grub error.

This suggests that you (1) installed grub on the mbr and (2) your BIOS cannot/is not set up to boot from the USB drive.  You can check (2) by going into the BIOS setup - when the computer is first starting look for a short line that says something like "press del" (or F1 or F2, etc.) to enter setup.  Find the boot menu and the boot sequence options available.   My guess is that USB is not an option.  If it is, select that, save/exit.

Whatever, the question is how do you want Ubuntu finally installed, on the second HDD or on an external drive?

If the USB external drive, that can be done but frankly it isn't newb stuff.  There are tools and techniques described at:
[http://www.8ung.at/spblinux/concept.htm](http://www.8ung.at/spblinux/concept.htm)            and
[http://syslinux.zytor.com/index.php](http://syslinux.zytor.com/index.php)
Alternatively, you can create a partition on the first HDD, install the /boot and the boot loader there, and put the rest of Ubuntu on the other drive.  However, there can be gotchas in this approach depending on what is already on that drive, where it is located, etc.

So I would be inclined to focus on getting the second internal HDD installation to work.  Can you provide additional data about that drive?  What has it been used for?  Is there a file system on it?  Did you tell the Ubuntu install to take the entire drive, or to install alongside something else?  Is the drive partitioned already?  And how old is this system's BIOS?  With a bit more info, we may be able to get Ubuntu installed on it.

Hope this helps.

--mingus

---

### Post by DAXP on 2005-05-31
That's correct. And USB is not an option. =(

And as for how I want it installed, the easiest way. From how you talk, that would be to put it on the second HDD. I don't want to put it on my Windows HDD, because I'm scared I'll screw something up and it'll delete something I don't want it too. So I would like to get the second HDD working as well. I'll answe those questions to the best of my ability.

Originally it was used as the only HDD in a HP PC. Now it just has a few misc programs, which may have been deleted while I was trying to partition the drive. Not sure what you mean by this. The only thing on it before trying to install Ubuntu was Adobe Reader, Photoshop, and RCT3. I told Ubuntu to take the entire drive, so there would be one for each OS. It was, yes. HP had it partitioned so that the System Restore data was on a partition of the HDD instead of sending CDs. However, I deleted the partitions and told Ubuntu to partition it automaticly. All that did was make the second partion 1 or 2 gigs smaller and the first 1 or 2 gigs bigger. The systems BIOS..I'm not sure. I don't know too much about the BIOS, but if it helps I have not updated it and the motherboard is an ASUS A8N-SLI Deluxe.

EDIT: Didn't know using quick reply cause you to quote someone. >_>

And I don't think the floppy thing will work. The PC doesn't have an internal floppy drive, so I'd have to use a USB one. Tried it anyway, and it did not work. =/

---

### Post by DAXP on 2005-05-31
I don't know if we're allowed to 'bump' topics, if we aren't, I'm sorry. I'd just really like this fixed.

Anyway, I went into my PC to double check that my HDDs were connected right. They were, but I changed the jumpers from Cable select to Master with Slave Present and what I hope is Slave with Master present, or the equivelant. There was no slave setting depicted on the slave HDD, so I chose the only setting that it didn't show a meaning for.

I then tried to install. The installer is now teasing me. I told it to partition the slave drive, and it didn't get any errors at first. Got to 100%, so I thought "Hey, all I had to do was change the jumper settings!" That's when it gave me the same error I had before, that it was unable to partition the HDD. >_<

---

### Post by mingus on 2005-05-31
First re the boot floppy:  You must check in your BIOS to determine if it can boot from USB.  There will be a boot options menu, and possibly a sub-menu for external devices.  USB will be shown as an option if it is supported.  If so, pls note that this will refer to USB ports attached to your motherboard, not any via PCI or attached to a hub.  If the BIOS option does not exist, then other than getting very esoteric, your best bet is to borrow a W2K or XP install CD and use Recovery Mode off of it.

Re your HDD setup on the controller:  Regardless of the other problem we are dealing with here, you must be absolutely sure you have this setup correctly or there will be issues.  Cable Select is Western Digital specific; not sure if other manufacturers support it, and it requires a specific cable.  If you do not have WD drives, or one is not WD, it is better to use the vanilla cable and jumper the drivers as Master & Slave.  Do not guess on the jumpering.  Of course, the Master is connected is on the end of the cable and the Slave is the middle connector.

Re the second HDD:  My questions were to get a sense of what might be on that drive which might cause the partitioner to choke.  While the Ubuntu partitioner is supposedly robust, you have the disadvantage during install of not seeing what is happening, other than a failure error.  The problem may be with the partition table, bad blocks, etc. - or an issue with the swap partition - that this partitioner cannot handle.

So consider preparing the drive with a different tool prior to install.   There are quite a few choices here, I'll give you what I would consider:
1.  Boot Windows, go to My Computer/Manage/Disk Manager, delete any partitions shown, create one new partition for the whole drive, and format it with FAT32.  Then make sure you can open it in Explorer and write a file to it.
2.  Install PartitionMagic on Windows and have it check the drive and then do the same test as #1.  
3.  Or, burn a Knoppix live-CD, boot from it.  Make sure the drive is mounted.  Open a terminal and use cfdisk to look at the partition table, delete any partitions, create a new one and format it as ext2.  (Do "man cfdisk" to understand how to use cfdisk first!)  Knoppix also comes with QTParted, a graphical partitioner which will also check the drive's state and perform the same tasks.

Alts #2 and #3 are definitely preferred over #1.

After you've successfully reformatted the drive and tested that the partition table is clean, you should be able to do your Ubuntu install.  Delete whatever partitions you created in your test, and then do your Ubuntu install.

If the install fails again, and you used either PM or Knoppix, go back to that tool and manually set up the partitions.
hdb1 => /            (for root, make it ext3)
hdb2 => swap     (2x RAM)
hdb3 => /home   (ext3)

If this is an older machine, add a 4th partition /boot (100mb) as hdb1 followed by the others.  Then install using expert and when you get to partitioning, tell Ubuntu what you've already partitioned.  Ubuntu will then reformat the partitions and install according to the mount points you gave it.

Good luck.

---

### Post by DAXP on 2005-05-31
Already checked, it doesn't support it. And update might let it, but it'd be useless since there are no USB ports on the motherboard.

I originally had them set as cable select, the Seagate had the option depicted on the HDD as well as the WD HDD. I set them as Master and Slave with the right cables, and that's when it started teasing me. >_>

And all of these options I can not do. As stated, I cannot find my Windows CD. I tore my room apart, even moved my desks and bed, but never found it. I just called one of my friends, the one that knows the most about PCs, and he said he usually gets rid of his Windows CDs. >_< So, I guess my best bet is to wiat until Monday (going to the beach Thursday), order a new XP CD, and then use it once it arrives?

Also, I tried taking my brothers old HDD (it's a Samsung, though it was taken from the same model HP as the one the Seagate came from) and using that. It worked, until it got past installing the base Ubuntu packages (or whatever the step is called). Then it said it had a problem writing to the drive, and that it may be full, which is strange since it was a 160GB drive that had been recently formatted. Then the installer went insane, and it got an error on all the steps. If I tried to re partition, it got an error starting the partition. Tried to create a user and pass, error. And now it gives the same error as the Seagate did. I have really bad luck, don't I?

And someone on another forum told me to type rescue in before starting the installer, because then it usually repairs the booter for Windows so that I could boot into that. I tried this, and it eventually told me to pick a HDD to mount. Unfortunately it had an error mounting any HDD, even external ones.

---

### Post by mingus on 2005-05-31
DAXP -

I take it you can't borrow an install CD???  Rather than buy one, you can create one of your own from another CD or possibly from a recovery partition such as was originally on that HP driver.  All you need is to install the XP boot sector (hint:  google xpboot.bin), a burner, the i386 folder, and possibly the setup.exe program.  This is how slipstreaming is done.  And there is another alternative which surely you know but I dare not mention.  

Going to a 160GB drive which is over the 137GB barrier will have its own issues.  This is shooting in the dark.  Don't go there.

Stick with your original second HDD, download and burn the Knoppix CD, and use the procedure above.  You should also consult the Debian installation manual regarding pre-partitioning the disk prior to install.

Get the 2nd HDD properly configured in the box, wipe it, test it, and you'll be ready to go.

---

### Post by DAXP on 2005-05-31
Actually one friend has a 'Windows XP Reinstallation CD for Dells' he's bringing tommorow, before we go to the beach. And if you list the file names for the others I can try that. I have a Windows XP Tablet PC, but I'll have to try and get my brother to let me use his laptop if I need to get online. And I'd rather not do what I think you mean.

The other HDD is 160GB as well. HP, for some reason, decided to use two different HDDs in the same model PC, as we both got those PCs at the same time.

And I can't download anything big. At least not if I need to burn it. SLAX isn't letting me take out it's CD, and it won't use my other CD Drive. My brother won't let me download something big on his PC, and I'm afraid that's the only PC (besides this one) that has internet access.

But this second HDD has gotten close. This HDD is having problems installing Ubuntu, the other was having problems being partitioned.

---

### Post by mingus on 2005-05-31
Ouch.  You didn't mention you have a tablet.  Isn't that a diff vsn of XP?  Can't help you much there.

Right now all I can suggest - assuming you have a burner - is to consult the Microsoft support site where I first directed you.  Check whether the procedure to create a recovery diskette is the same for a tablet.  If the files are the same, then it is a matter of grabbing those files which hopefully are the same on your brother's laptop.  You can then download xpboot.bin (it also exists under other names) and follow the burn procedure, which is very specific.  What you will have done is create a replica of the diskette MS describes, except on a CD.  Should work exactly the same.

Once you've made it thru this step, concentrate on just getting the 2nd HDD to work under Windows.  That it is configured correctly, can be read/written to, shows the correct size, etc.  See my post above for doing this with Windows Disk Manager.

Once you're *sure* it is OK, I would - again - go the Knoppix route and pre-partition the drive.

Finally, where you will need to be careful is the boot loader setup.  With this large a drive, go with lilo and make sure LBA is enabled in the BIOS and in the boot loader as well.  Also consider putting the boot loader on a floppy rather than the MBR, or you may be back to square one.

Good luck and signing off.

--mingus

---

### Post by DAXP on 2005-05-31
Tablet is just a second PC I have, for when I leave the house and need a PC, or if something like this happens. It's....not that great, but it works for what I need it. This is a desktop. And as for getting Windows working, a friend's coming over tommorow and he says he has a Dell Windows XP Reinstallation CD. I think that might work.

And the HDD was working with Windows fine - except when I tried to install UT2004. I installed Adobe Reader, Photoshop, and Rollercoaster Tycoon 3 on it. Haven't tried the other HDD.

And I don't think putting the boot loader on a floppy would let e use Linux. I don't have a built in floppy drive, only a USB one. Didn't think I'd need a floppy when I built the PC.

---

### Post by mingus on 2005-05-31
Forgot that you couldn't boot from floppy.

Regarding, the HDD, this is not a matter of it having "worked" under Windows before - there could still be bad blocks or partition table irregularities that would cause a partitioner to choke.  The user typically does not see these problems.  The drive just needs to get it wiped and then partitioned with a tool that is native to the OS you're going to install, as Debian recommends.

If the second HDD is 160GB, without getting into the technical details, this adds weight to considering doing the partitioning ahead of installation, or at least installing in expert mode and doing the partitioning manually during install.  In particular it is a consideration for the boot loader, which in this case LILO would be safer.  A safe partitioning scheme would be /boot on hdb1, swap on hdb2, and / on hdb3.

Good luck with the Dell Recovery CD.

---

### Post by DAXP on 2005-06-01
Ok, I'll try doing what you've said to get the HDD working.

Which is best, using Partition Magic in Windows or the Knoppix one? And about how much space should I give each partition?

And thanks. Hopefully it'll work.

And hopefully I can get this working by tommorow night. I'm leaving for the beach Thursday, and won't be back till Monday. During the time I won't have acess to this PC.

---

### Post by mingus on 2005-06-01
The rules of thumb are (1) use a partitioning tool that is native to the OS you are installing, and (2) don't mix partitioning tools.  

I would use a Linux partitioner.  The Ubuntu/Debian default is PartMan, probably because it can resize Windows partitions.  However, there is an issue with it and certain IDE interfaces.  And I would be concerned that it choked the first time.  In the installation manual at:

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs05.html#id2539368](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs05.html#id2539368)

I found that you have the option of using either fdisk or cfdisk instead of PartMan.  
I would therefore be inclined to use cfdisk.  Just read the man page first and be very careful.

If cfdisk can't handle the partitioning, you have an unidentified problem that will need to be researched.  If that happens, the cfdisk errors returned may give you the needed information.

Since cfdisk is included with the Ubuntu installer, you don't need to get a live CD to pre-partition.

With this drive, you may need a separate /boot partition.  Make it hdb1 primary and 100MB.  Make hdb2 primary for swap, 2x your RAM.  For the rest of the drive, it's a matter of how you intend to use the system.  Certainly the easiest is just to make hdb3 the root (that is, the "/" mount point).  Some users separate /home from the root because /home is where user data and user defined apps are kept (like My Documents in Windows); good for backups.  But if you want to read/write to this data from your Windows installation, then you would want a vfat (FAT32) partition of some size with a user-defined mount point like "/data".  (Note:  The root can be broken down across separate partitions, and there are arguments in favor of this, but given how new you are to this, I would not go there.)  Finally, if you don't need all that capacity now, you can leave some of the space reserved for later.

So it's entirely up to you.  All things considered, one scheme that might be good for you could be:
hdb1     /boot           100MB   primary   ext2
hdb2    swap            2x RAM   primary   swap
hdb3    /                   20GB      primary   ext3
hdb4    extended     to end of drive
hdb5    /home          20GB      logical    ext3
hdb6   /data              ??          logical    vfat
remainder of drive not partitioned, reserved for future use.

If you have a huge amount of data planned, like a music or video library, you can expand hdb5 to accomodate that, or it is just as easy to create an additional partition just for that with a user-defined mount point like /music, etc.

btw, if your system has an overlay installed to handle the oversize drive, it probably won't work and isn't needed with Linux.  Unless the manufacturer says that it can/is, then be sure to remove it before installation.

good luck.

---

