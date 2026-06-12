---
title: "Trying To Make This OS Play Well With Others"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-07-17
Switching to Linux over Windows came as a necessity, but at the point of decision, I only saw it as an alternate path.  The decision point occurred several years ago.

I have a Toshiba L355-S7915.  It came reconditioned with Vista on board.  Two weeks later, Vista would not boot at all.  A file defect of some sort,  It would not recover.  I tried installing Windows 2000, then XP, and neither would complete the setup.  No reason given. I could have shipped the notebook back under the warrantee, but I knew it was still working, because a Ubuntu LiveCD assured me so.  So I just installed Ubuntu.

What I am struck by is that some PC design could be so far off from what was expected back years ago, that neither Windows OS would install on it.  But Ubuntu had no problems at all.  That was the real turning point.

That said, problems remain.  Latest releases of Ubuntu and Oracle's VirtualBox seem to run into problems with Windows 2000 as the intended client.  When you don't know where a problem is, isolation might be useful in looking further,  The Windows client is fixed by VDI imaging, so it must be with one of the other two.

To split these up, I needed another OS to use with VirtualBox.  Because it is well known, and compatible with VirtualBox, I elected to try Fedora 13.  This is not a Debian distribution, and I immediately found that some familiar tools and methods were gone as a result.  you cannot even get into the sudo mode on just a user's password.  In fact, if you explore, you find that you have to be added to a new table named /etc/sudoers in order to make changes like that, but you are prohibited from editing this table as well.  They tell you that you can only make changes if you use something called visudoers.  Not to worry.  Just get the Ubuntu LiveCD running again, and your sudo rights there will carry the day, assuming that you know what you are doing.

The real problem with trying to have something like Ubuntu on one partition and add a different OS to another, is the differences in the boot method employed between them.  With the last few releases of Ubuntu, it is classified as Grub2.  Prior to that, it was what they now refer to as Legacy Grub.  They do not match, and they apparently cannot reside together and both be used for booting purposes.  If they can be, it is only with a lot of manual changes involved.

That was known before I reached the point of attempting this, as I had already run into issues between Grub2 and Legacy Grub when I went from 9.04 or earlier to 9.10 or later.  So I could see what I had to try and deal with in that regard.

What I did not expect and had no answer for, is why the modified Legacy Grub was now reporting that it could not find some partition?  What was that all about?

A new unknown was now making and appearance.  If you are familiar with dividing a single drive up into multiple partitions, then you have some inkling of what a partition table is.  It keeps track of all the details involved.  And grub apparently uses these details when dealing with partitions, as well it should.

But partitions are not absolutes.  They can be changed, added, deleted, resized, renamed, and file systems redesignated.  Tools like gparted and partition manager exist for that purpose.  These effect the partitions, but they do nothing where grub is concerned.  So if you got rid of a partition, or made it a different type, grub can be expected to squawk when you next try to boot up.  And if you get such a squawk, say an Error 17 or Error 22, it means the expected, sought for boot partition has magically gone away and grub is helpless to do anything about it.  But you may not be.

When partitioning came along, it was pretty much a DOS and Windows thing,  Not much said about it, it was just there.  Sort of in the same league with adding a mbr, or Master Boot Record, to existing drive structures.  The mbr is like grub, in the sense that it also is subject to partitioning changes.  My guess is that grub even relies on what is in the mbr for knowing some of what it apparently knows.  And it does not forget either, another indication of a direct tie-in between the two.  And to make matters even more complicated, the mbr cannot be touched with most software tools, plus the fact that every file structure related to partitions is designed to do its own thing, and Microsoft chose to only deal with the file structures related to DOS and to Windows.

Sounds messy and it is.  But it can be dealt with.  The easy way is just to use a Microsoft install disk that offers a Console Repair choice, such as from Windows 2000 on up.  But it cannot just be any Windows 2000 install disk, or even any Windows XP install disk,  With Windows, it has to be brought up to at least Service Pack 3, and with XP, it has to be brought up to at least Service Pack 2.  I mean this is true for either if dealing with large hard drives that require LBA for addressing purposes,  These patches provide this to these older versions of Windows.  Newer versions have it already built in.

Using Windows should be rather simple.  Put the CD in the drive and boot from it. After loading a ton of drivers and stuff, you can finally see it shift over into starting Windows, after which it suppose to get some install or recovery options.  Only with my notebook, Windows 2000 just hangs, and XP goes to a BSOD, meaning Blue Screen of Death state.  But more on dealing with that later.

What you pick is Recovery, then by the Console method.  This gives you command line control and access to some of the related commands.

The command you want is FixMBR.  Some describe this as the equivalent of the older FDISK /MBR, and what these do, specifically, is wipe the MBR record clean.  They also stick a fresh copy of the current boot method there, which is fine, but it is getting rid of the old references that is most important.  FixMBR will also complain that it cannot relate to the file structure in the partitions, so this might not be a safe thing to do, but that is because Microsoft only speaks to DOS and Windows file formats.

FixMBR can be used with specific drives or partition designations following, or used by itself, go with the current active drive,  That should take care of matters for you.  Go ahead and quit, and go back to where you were previously.

But, you may not have a boot Windows CD, or it may not work on your PC or notebook as mine did not, so what do you do instead?  Linux also offers a fixmbr   I got it and tried it, but my problems persisted.  I guess it did not do a clean wipe beforehand.  Reformatting your drive, deleting partitions and adding them back, none of these things work.  Fact is, messing with the partitions may just make things worse, or at least different from your perspective.  So what does work?

I haven't tried everything out there, and actually there isn't much out there to start with, but this will do it:

$ sudo -s
# apt-get install mbr
# install-mbr -i n -p D -t 0 /dev/hda

The options shown here are:

-i interrupt n = none (do not display a MBR prompt)
-p partition D = boot the partition with the bootable flag set
-t timeout 0 = do not wait to boot.

I was fortunate to find mention of install-mbr on the Ubuntu forums, but no mention that you have to install mbr to have access to it.  There was
yet another possible approach involving a package called ms-sys, which supposedly brings much of Microsoft functionality to Linux.  Thought passing on a related web page might be of interest:

[http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

---

