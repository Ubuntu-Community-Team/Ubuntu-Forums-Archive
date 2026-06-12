---
title: "GRUB 2 Boot Sector Update?"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by aajax on 2010-09-17
This is sort of a continuation of the discussion in another post of mine ([http://ubuntuforums.org/showthread.php?t=1574076]("http://ubuntuforums.org/showthread.php?t=1574076")) but I've narrowed the problem a bit so a new post seemed appropriate.

I'm still wrestling with the cloning issue.  Here is the scenario.[LIST=1]
[*]Installed Ubunto Server (10.04) in second partition (/dev/sda2) of the boot drive using installation CD.  MBR was NOT changed.  I have GRUB (legacy) installed on partition 1 which is a tiny FAT partition.  This partition is configured to chain load the other partitions on this as well as other drives.
[*]Performed some amount of customization of the new system.
[*]Created image file using Partimage from System Rescue CD 1.6.0
[*]Changed UUID for /dev/sda2 in anticipation of restoring image to another partition on the same drive.  This included updating /etc/fstab and running update-grub to account for new UUID.
[*]Restored image to /dev/sda4 using Partimage from System Rescue CD.
[*]Booted /dev/sda4 by manualing editing the menu item on the GRUB 2 menu list.
[*]Ran update-grub to regenerate /boot/grub/grub.cfg and inspected the result to verify that it now used correct root drive (HD0,4).
[*]Restarted the system to verify that both partitions booted correctly but they don't.
[/LIST]
What happens after above has the appearance of the boot sector on /dev/sda4 still finds the menu on /dev/sda2.  This suggests to me that update-grub updated the /boot/grub/grub.cfg but did NOT update the boot sector.  In that, the same boot sector still loads the menu from /dev/sda2.

If my assessment is correct the question becomes, "what method is prescribed by GRUB 2 for updating the boot sector?".  If I'm wrong what is the proper assessment?

---

### Post by drs305 on 2010-09-17
'update-grub' generates the grub.cfg file; grub-install also writes to the MBR.

Are you trying to install G2 into the partition using blocklists - so that the boot sector of the partition is written to and not the drive's MBR?

If so, you would use "grub-install" with the "force" option and designate the specific partition instead of the drive. You can try it without the "force" switch and you will get a nice warning message (sudo grub-install /dev/sda4).  

The reason is that with blocklists Grub2 registers the location of core.img as a physical address - if it is moved, G2 fails. Of course, if you understand what you are doing it will allow you to install to a partition with the 'force' switch.

---

### Post by aajax on 2010-09-17
> **drs305 said:**
> 'update-grub' generates the grub.cfg file; grub-install also writes to the MBR.

Are you trying to install G2 into the partition using blocklists - so that the boot sector of the partition is written to and not the drive's MBR?



I don't know what blocklists are but I do NOT want the MBR updated, which has a lot to do with why I am resisting the temptation to hack.  I only want to update the boot sector on the partition that contains this new system I am building and also wanting to have an operational clone of it.  Because I change partitions a lot it is very undesirable to have any partition depend on another for booting.  If I understand it correctly running "grub-install /dev/sda4" will target the specified partition and leave the MBR alone.  Do I understand correctly?

From my own research there are warnings about using grub-install on computers with multiple drives.  Since I have that and often re-configure the CMOS/BIOS to change boot drives I'm inclined to think that I should understand how to be sure it works as desired.  I noticed something called a device.map file described in the documentation but I find no such file on my new (10.04) system.  I sort of got the idea that I should have such a file and most of all have a procedure for verifying that it is correct.  If that is a good idea how do I do it?

---

### Post by drs305 on 2010-09-17
Not having a device.map is normal. You can generate one if you want with the "grub-mkdevicemap" command and it will be created in /boot/grub/

I haven't done a lot of work with installing Grub2 to a partition. My understanding is that it will only write to the partition if you use the "force" option. But to be sure, I think your best course is to go to the IRC channel on Freenode where the grub developers hang out. They are the experts and, if they are willing to respond, can answer your question (caution - read the Channel intro before posing your question). They are located at #grub.

If they don't respond, try another time. Sometimes they are too busy, sometimes they just aren't responsive, but eventually you will get someone who is willing to chat.

If you get a positive response please summarize it here so we can all learn.
:-)

---

### Post by aajax on 2010-09-18
I'll pursue the chat suggestion in order to learn more about the design of GRUB2.  However, that will take longer than I can afford to wait on this work because I'm neither setup to do IRC chatting nor familiar with how it works.

Fortunately, at this moment in time I am able to boot the system with the defective boot sector.  Therefore I've done that found that running -

sudo grub-install /dev/sda4 --force

has the desired affect.  It does warn me against installing the boot loader in a partition rather than the MBR.  It actually says "This is a bad idea.", which is a curious notion since the normal Ubuntu installation process offers this option.  Furthermore I don't recall the Ubuntu installation saying it was a bad idea.  I think it is a bad idea to allow the installation of a new system on a computer with numerous other systems that are working very nicely to mess with the MBR that all of the systems depend on in order to boot.  Messing up the MBR could prevent me from being able to boot all of these systems not just the new one that is being installed.  The idea is even worse when you consider that the new system is using a newly developed boot loader that is still considered to be in beta test mode.  What is the risk that a future update to the GRUB2 package will cause some problems.  It is a good idea to limit such risk to the system that is being updated.

I happen to think that the idea of being able to repair the bootloader without actually having to boot the defective system is a good one.  At a minimum there is a need to be able to update the boot sector of a partition.  This was possible with the setup command in GRUB legacy but for some reason that capability has been removed from GRUB2.  Your document ([https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")) is quite good and I've come to believe that it should be possible to do this by using the LiveCD and following the suggestions therein.  I'm using Ubuntu Server and I suspect that the LiveCD does not have the graphical desktop referred to in your paper.  However, I assume that using the same version of an Ubuntu Desktop LiveCD would be quite suitable for repairing my Ubuntu Server system.  Also I now think that I should be able to use the LiveCD to create a small/tiny boot partition that works very much like my current DOS/FAT partition.  In that, it is separate and distinct (i.e., independent) from any operational system.  In that, this partition does not need to have a complete Linux system but only a small ext2 filesystem that would contain the files used for booting.  Do you know of or possibly only think of any reason this won't work?

---

### Post by drs305 on 2010-09-18
aajax,

I don't know why it wouldn't work, but I've not tried it. 

The reason you didn't get a warning about installing on a partition during your initial setup may have been timing. Initially Grub 2 would not give a warning when attempting to install on a partition. Sometime in the past six months or so (I lose track sometimes) they decided to add the warning when trying to install on a partition via the command line. Whether that was due to feedback, hindsight, or whatever, the warning wasn't always there.

Best of luck with this endeavor.

PS: I did some work on the community doc for setting up IRC. I used xChat, so that's what I worked on. You might want a totally textual chat client, but this will get you started if you are interested.
[https://help.ubuntu.com/community/XChatHowto]("https://help.ubuntu.com/community/XChatHowto")

---

