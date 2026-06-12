---
title: "How do I delete the grub boot loader from the Master boot record?"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by muffinhead on 2006-05-22
I am having a problem, I severly messed up my ext2 partition, by adjusting and making changes to it.

Ubuntu is installed on my second hard drive, my D:\ Drive, and I decided, after intrusive work to try and fix it, that I would Delete all partitions entirely of my D: Drive, and re-create (1) 5 gigabyte ext2 partition,  (1) 2 gigabyte Swap partition for Ubuntu Linux, and the rest assigned NTFS Partition for Windows Programs, and games.

The problem is if I delete Ubuntu, or the Ubuntu partition, without first removing grub from the master boot record, I can botch both windows xp, and Ubuntu, and get an "unable to boot Operating system" error.

So How can I remove grub from the Master boot record, and boot normally into windows, to fix my Partitions, reinstall ubuntu, so I can get everything straightened out?

Thanks If you can help me, Links to similar threads appreciated, Thank You;)

---

### Post by Irony on 2006-05-22
Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc

---

### Post by muffinhead on 2006-05-22
I don't know if this is a Problem,

I have an emachines W2925 Computer, and the only thing I have close to an install CD, Is a Restore DVD, which Restores my entire system, at the cost of all my data.

Is a restore DVD Sufficient to fix the Master boot record, using the method you described? I don't want to lose all my data in windows XP, and don't want to do a full system restore, as I spent a long while, Installing software to windows XP.

I think I may be able to boot to a Prompt with my Restore DVD, if I remember that was one of the options, but am unsure. 

Please Let me know if this is sufficient, Because my computer did not come with an Windows Xp Install disk, It came Preloaded with windows XP, and has a Restore DVD, incase of a system failure, or Problem. Thank you, if you can let me know:)

---

### Post by Herman on 2006-05-23
> So How can I remove grub from the Master boot record, and boot normally into windows, to fix my Partitions, reinstall ubuntu, so I can get everything straightened out?If it was me who wanted to re-install Ubuntu, I would simply boot the Ubuntu install CD and delete all the partitions to be deleted and re-make them with the Ubuntu Install CD's partitioner and then re-install Ubuntu and GRUB. That way would be the fastest and most direct.
By the way, ext3 filesystems are better than ext2, you should use ext3.

You also should have at least your most important files backed up before working with partitioners and installing new operating systems and their bootloaders too, I have to tell you that.
I have Windows XP recovery disks too and I can't do anything with mine except completely format my whole disk and reinstall Windows. They don't seem to have any other functionality beyond that.

If you really want to do things the way you suggest, see below.
> _For Windows 98 or Windows XP without an 'install' CD_
      Your computer may have come with a Windows XP 'Recovery Disk' instead of an 'Install' disk, or maybe you lost your Windows XP CD or have Windows 98 or some other version. 
      A Windows 98 boot floppy will work just as well as an install CD to restore your 'boot sector'.  Just pop the floppy in the drive and boot your computer to the     A:\_   prompt and use the command fdisk /mbr and your 'boot sector' will be back to normal again.
      You can download a self extracting file to make your own Windows 98 boot floppy disk from [Bootdisk.com]("http://www.bootdisk.com/").  The one I use is called 98SE OEM and I have used it to restore the bootsector on both my Windows XP Home Edition computer and also my Windows 98SE computer.  Something else you should know about is that you can also use [GAG Boot Manager]("http://gag.sourceforge.net/"). You could use GAG for an emergency boot disk from a CD or floppy to boot Windows while Ubuntu is deleted and you won''t need to restore the Windows MBR at all. It's always wise to have an emergency boot disk on hand anyway when uninstalling and installing OS's and boot loaders. Here's a  [How-To on GAG Boot Manager. ]("http://users.bigpond.net.au/hermanzone/p12.htm")
I hope you find something here helpful, Regards, Herman

---

### Post by muffinhead on 2006-05-23
Thanks for your reply, but I forgot to post again and mention, that I solved my problem.

All is I did, was put in my restoree DVD, hit #2, boot to command Prompt, and type in "fdisk /mbr" And my Problem was solved. I also deleted all my partitions on my Secondary Hard disk, Make one NTFS Partition for Windows XP, and one EXT3, and one Swap for Ubuntu Linux, using Powerquest Partition Magic, and my Problem was solved.

Thanks for all your help though, I appreciated it:)

---

### Post by digi421 on 2006-06-29
fixmbr didn't work for me. After the Bios POST, the pc just sits there, no error message, no boot, nothing.
My setup is as follows:
4 S-ATA drives, 3 of which are in a fake bios Raid0 pack. 4th s-ata drive has the OS (winXP) and currently 3 partitions:
partition 0 is the xp partition, partition 1 is ext3 set to mount to / and partition 2 is the swap partition. I let the installer install grub to the boot sector and that was wenn things went fubar.
Now I am stuck with no bootable partitions, xp recovery console can't find any bootable drives (actually it can't find any drives at all). Guess I'll have to re-install everything again and I don't even know where to start because the xp installer can't find any drives.
I am not extremely stupid because I managed to install Ubuntu on another machine (though that has no dual-boot - but at least it DOES boot).

---

### Post by Dylnuge on 2006-07-01
I have a similar problem, with one main difference: I am actually having a replacement computer shipped to me. Therefore, all I need to do to entirelly make my computer "un-tampered with," is to totally reinitalize the system. My question is simple: is it nessicary to still run fdisk /mbr or fixmbr, or should reinstalling windows with the Install disk still just replace the mbr (while leaving my Dell Support Partition in place?)?

EDIT: Opps, guess I should look more at the post before I reply. I have Dapper, not Breezy. Still, same issue, same problem. Shouldn't matter much.

---

### Post by Herman on 2006-07-01
digi421
I'm sorry, but I have no experience with fake BIOS raid0 or Logical Volume Managers so I can't help. For standard general purpose garden variety installs, here is my Page on uninstalling Ubuntu in case that's any help. It gives all the options I know for overwriting GRUB off your MBR. It also has some links with more information. [*Click Here.*]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
Dylnuge
> is it nessicary to still run fdisk /mbr or fixmbr, or should reinstalling windows with the Install disk still just replace the mbr (while leaving my Dell Support Partition in place?)?Simply re-installing Windows should automatically restore your MBR back to the way Windows likes it, with Windows IPL in it. It should not be necesary to do anything special at all.> (while leaving my Dell Support Partition in place?)?I'm not sure about that part, that depends on exactly which kind of Windows install disk you have. It might be best to ask Dell tech support about that if you are worried about it. Or  just give the install CD a spin and see what happens, most of them give some kind of warning when you are about to pass a point of no return. If it detects your partitions and offers you a chance to select one you;ll be okay, If not, hopefully there will be some way to abort the installation and reboot. That's really a Windows/Dell issue though, I don't know about that.

Also related to this topic, (in case anyone is interested), here's how to make a backup of your IPL part of the MBR with the new 'Desktop' Live/Install CD, you can save it to any media you like and restore it again anytime. I tested this several times and it works well for me. People can save either their Windows IPL before a Linux install or their GRUB or LILO IPL before a Windows re-install this way. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")
Regards, Herman :D.

---

### Post by dparker on 2006-07-09
Can I avoice grub entirely?  I use Boot-It to manage multiple boots.

---

### Post by dparker on 2006-07-09
:oops: Oops.  That should be "avoid" grub ... using Bootit instead.

---

