---
title: "Dell PBR bad sig problem with workaround"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by PRMan on 2007-05-30
Since my Vista Beta expires in a couple days (and I hate it), I decided to install Ubuntu instead. After installing Ubuntu successfully on 2 laptops, I decided to install it on the second hard disk in my Dell 400SC Server (which I use mostly as a goofing around and gaming system), replacing the Vista installation that was there.  (The first disk has XP Pro.)

The first problem I had is that when the installer was asking me which disk to install on, it wasn't immediately obvious which disk was which.  I opened up the File Manager (or whatever it's called) and looked at the two disks.  From there, they were just called "disk" and "disk_1".  Again, it wasn't obvious which was sda and sdb.  

It seems to me that when I right-click in the File Manager, there should be a Properties option which would give you detailed information like that.  (I finally ran the mount command in the Terminal to bridge the gap.)  Users shouldn't have to work that hard to ensure they don't overwrite their other OS.  

Also, it would have been nice if it could have told me sda1 - Windows XP, sdb1 - Windows Vista.  I'm sure there is some way to identify OSes if you can mount the partitions.  This would have greatly reduced my confusion.

------------------------

Anyway, I finally told it to go ahead and use all the drive that was formerly Windows Vista.  It installed and I rebooted and I was greeted with:

"Loading PBR for descriptor 1...
Bad PBR signature"

or something like that.

Anyway, the computer was completely unbootable, so I put the Live CD back in and looked at the drives.  The XP partition seemed fine from the Live CD and the Ubuntu partition looked good too.

I did some reading and it appears that the PBR error refers to the hidden Dell Utility Partition, which apparently the Ubuntu install clobbered.  There is absolutely no way Ubuntu should be made available while having this problem with a very popular line of computers such as Dell.  Indiscriminate clobbering is such a Windows thing to do (although Vista handled the same install just fine).

Everybody's response (if there even was one) was, "Your Windows is toast.  Reinstall from scratch."  But I knew that wasn't the case because I could see it from the Live CD.

------------------------

Finally, I tried some different booting options by hitting F12 at the BIOS screen.

3. Primary Master

will give me GRUB and if I leave it for 3-5 seconds will boot Ubuntu correctly.  

Also, from that GRUB menu, I can select 

Other Operating System: 
Windows Vista

Doing that gives me my former Vista boot menu, from which I can select

Previous Version of Windows

and lo and behold, my XP partition loads just fine and works perfectly.

I just thought I would post this so that other people won't reformat their perfectly good partitions if they have a Dell and the F12 Boot Selector option, and Ubuntu clobbers their Utility partition.

------------------------

My question is, since I have friends who also have Dell 400SC systems, could I boot up the Live CD and use the dd command to grab a certain number of sectors from their disk (the Utility partition) and then use dd on my system to put it back?

Also, if I switch the order of the disks so the Ubuntu drive is first, the Dell may not care about the Utility partition anymore.  If I do that, will I have to make changes to the GRUB setup, since hd0 and hd1 would be reversed? (or would they?)

Thanks for any insight that anyone can shed.  Also, if there is somewhere to report massive system-wrecking bugs, that might be good too.

Thanks.

---

### Post by PRMan on 2007-06-05
Since nobody has responded, I'll update Dell users with what I did.

The Dell 400SC has internal USB ports that are inaccessible from the front.  Previously, I had an old USB key mounted inside the case for testing ReadyBoost.

I reformatted that in Windows (still FAT32) and then booted into Linux and did a grub-install on that drive (plug it in and then use type "mount" to find it).  I copied my menu.lst file from my working GRUB and set my BIOS to boot off USB devices before Disk devices.  In looking at the menu.lst file, I also uncommented the cyan on blue color scheme so I would know which GRUB I had booted into.

I rebooted and sure enough I got a blue GRUB menu.  I booted Ubuntu and it worked (was still listed as (hd1,0)).  I rebooted and tried Windows XP, but it didn't work.

It turns out that Windows XP used to be (hd0,0), but when booting from the USB key, it changes to (hd2,0).  I got back into GRUB and used the "e" command to edit the line to say (hd2,0) instead and then hit "b" to boot.

Windows worked as well.

I edited menu.lst (from Ubuntu because of text file line endings) and made the change.  They both work now.

Yes, I have to boot from a USB key inside the case, but everything works from a simple menu (well, as soon as I figure out how to remove that Vista menu).

---

### Post by PRMan on 2007-06-05
Oh, yeah, in researching this with Dan Goodell, who was pretty helpful in discussing the problem (search for DSRFix)&#807;, I also got an opportunity to use the PTEDIT program on his DSRFIX boot CD.

There was nothing wrong with my partitions at all.  Dell just gripes because it wants to see a FAT16 or FAT32 or NTFS partition somewhere.  If it doesn't see one of these on the "boot" disk, the BIOS simply crashes out.  

Again, there was nothing wrong with Windows or Ubuntu at all, just Dell's BIOS refusing to cooperate.

"Loading PBR for descriptor 1...
Bad PBR signature"

on a Dell after a Ubuntu install should be translated

"Dell doesn't support non-Windows operating systems...
and we enforce that in our BIOS"

---

### Post by esr on 2008-04-06
I ran into this "Bad PBR" problem while trying to migrate my sister's Dell Dimension 3000 to Ubuntu 7.10.  The fleas of a thousand camels should infest whatever idiot PHB thought it was a good idea for the BIOS to crap out with a cryptixc error message if it doesn't see something that it thinks in a Windows recovery partition on the boot drive.

After several hours of web research and experimentation I did manage to work around the problem.  Here are the key things to know:

* This trap is especially nasty because  it will not manifest on the warm boot after installation. You have to power down the machine and power it back up again to notice that your new Linux machine is in fact unbootable :(

* The workaround for the problem is to have a FAT32 partition somewhere on the boot drive. The contents of the partition doesn't matter, and it doesn't need to have a mount point.  What matters is having a FAT32 entry in the Master Boot Record. This will be enough to make the BIOS think it sees the recovery partition it is looking for. 

* A FAT16 partition **won't** work, at least not for a D3000; there are hints elsewhere on the net that it might be sufficient with other DELL BIOSes.

Now here are some implementation hints that might save you time:

* You are likely to have already installed Ubuntu when you run into the bad-PBR problem.  If so, you *can* in fact shrink one of the existing partitions and create a FAT32 partition in the gap that opens up.  However, be aware that FAT32 partitions have a larger minimum size than you might expect.  According to the [FAT32 Resource Page]("http://www.project9.com/fat32/") it is "about 260K"; I got away with 254.

* GNU parted, at least at the 1.7.1 version now current, cannot resize an Ubuntu boot partition; it complains of an "incompatible feature" (probably resize_inode, though I'm not sure of that).  The partitioner in the Ubuntu-7.10 installer can do it, though; start the installer edit partitions as needed, then cancel the install.

A friend suggests that with a bit of trickery it might be possible to let the wasted FAT32 soace be your swap partition.  I have not tried this.  Anyone who finds a recipe for that should add it to this thread.

---

### Post by bpinkston on 2008-04-09
Thank You, this is good information to have.  I installed only Ubuntu, you would think the BIOS wouldn't care how the paritition is formatted.   Will fix this tonight, and update.

Thanks,

---

### Post by linuxafficionade on 2008-06-18
Here are the steps I took (copied from Dell's forum):



I recently ran into a similar problem on a friend's PC - if the image restore won't do it for you probably your drive partitioning has gone south. I had the windows stop c0000221 Unknown Hard Error.

 

If still in warranty my first suggestion would be to call Dell and ask for real restore solution, a CD would be nice, after all you paid for an XP license and you might as well have the disks.

 

My friend was out of warranty so at this point paid support was out of the question and Dell won't ship CDs (they do for the corp but not for the home - go figure) so in that case I dug around the forums and found a reference for these notes:

[http://www.goodells.net/dellrestore/index.htm#fixes](http://www.goodells.net/dellrestore/index.htm#fixes)

which shows the problem as much more serious as it looked at first, a broken master boot record and possibly some hard drive damage. I got the Ultimate Boot CD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) which has some diagnostic tools for the brand of hard drive (Samsung), loaded it and ran - hard drive is okay so then to the next possibility which was damaged MBR (master boot record) or damaged partition table.

 

So in my case I needed to backup the hard disc first to save data, as luck would have it I had an external enclosure for a 2.5 hard drive, so I took out the drive and attached on my other machine (in this case Mac). It shouldn't really matter as all I am doing here is copying data from one hard drive to another, so I just got in there and backed up the users' folders.

 

I then downloaded this software:

[http://www.goodells.net/dellrestore/files/dsrfix.zip](http://www.goodells.net/dellrestore/files/dsrfix.zip)

which contains an .iso file for creating a bootable image.

If you follow the instructions there is a software that could usually repair these prb failures.

In my case it couldn't so I had to dig deeper. Thanks to Dan Goodell's explanation I found out the Dell image was a Ghost 2003 image, a program that I had. If you don't have it there is also a proprietary version installed in your Dell recovery partition. So my next step was to save the ghost image to an external drive and then transfer to DVD to recover as the machine would not recover from the Ctrl+F11 command (failed several times after seemingly running it fine). So I went through Dan's steps on using Powerquest (off his CD) [http://www.goodells.net/dellrestore/fixdesc.htm](http://www.goodells.net/dellrestore/fixdesc.htm) and figured out that if I change the Boot Code on Partition 1 to 80 it will become the active partition where the ghost image resides. So I did that and shut down, then transferred the hard drive back out of the PC, into the external enclosure and popped it in the Mac. Voila! I could see the ghost image file in the /img folder and the recover software (proprietary ghost version) in the /bin folder. I copied the folder /bin fully and the file FI.GHO from folder /img to a DVD (close to 4 gigs) and moved to next step. Since I had a full version of Ghost 2003  that runs off of CD I didn't need to make the DVD bootable, but if you don't have Ghost 2003 you'd have to make sure the DVD will boot by getting a Win 98 SE iso from here:

[http://www.allbootdisks.com/download/iso.html](http://www.allbootdisks.com/download/iso.html)

unpacking it and adding its files to the root folder of the DVD that you created.

Next I decided to reformat the hard disc to make sure I have a clean install, so in my case I got the GNOME partition manager

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) , d/loaded the .iso and made a bootable CD by burning the image to a CD.  

, and booted with it, set one big NTFS partition and formatted it. Shut down again. 

In my case I booted from CD with the Ghost 2003 CD and chose to "Restore Partition" to the letter drive of the CD Rom, put in the DVD with my backup image and chose to restore image file to disk, pointed to the only disc in the PC. It ran to 100%. Got ecstatic - done???? No, the pbr error message is back with a vengeance. ](*,) so I decided to get rid of the MBR (master boot record) as it seemed damaged and use boot loader to point to the partition instead. I decided on GAG [http://sourceforge.net/projects/gag/](http://sourceforge.net/projects/gag/) 
although there are also plenty other free and commercial boot loader options: 

[http://www.goodells.net/multiboot/tools.htm](http://www.goodells.net/multiboot/tools.htm) 

went through the motions, pointed to the only Windows partition and I was good to go, Windows finally booted!!!!

Now if a real system restore disc was available (like my extra Windows XP Home Copy) - you could essentially boot from the Windows CD and do a fresh installation with a single NTFS partition, overriding the two junk Dell partitions that are there to just take space, load Windows, then pop in your drivers disc and be good to go! Unfortunately in our case - my friend didn't have any money to spare on an extra Windows license as my Home XP copy didn't take his license # so we had to tinker until we got it working. If only Dell would've provided recovery discs!  Where are the class action lawyers when you need them! [-o<

---

