---
title: "Weird Win2000 dual boot situation????"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2007-04-09
I am trying to set up a customer's computer with a dual boot, same drive. Win2000 Pro and Xubuntu Edgy Eft.

Specs:
Older eMachine
Celeron
600mhz
196mb ram
Ide0=Seagate 10.2 gb set as master
Ide1=cd-rom set as master
PCI sata card with VIA6421 chipset=Seagate 120gb FAT32 (formatted thru Edgy)

This is a very long story to explain so PLEASE bear with me. The cdrom wasn't working when I tried installing Edgy Alternate CD so I had to use the method of installing from an iso. (heres the guide: [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)) I used the latest Gparted Live CD to shrink the NTFS parition down to 4.5, then I made a 1gb fat32 partition for the iso and boot files, and formatted the rest to ext3. I know I know, I forgot about swap.

I did the Edgy install. During that install I deleted that ext3 that I created with the gparted livecd and made a swap and a ext3 for edgy. I booted to Edgy and everything was great. I did a bunch of stuff, like setup ssh, ran automatix2 and installed all the goodies. I realized I was getting short on space and knew I no longer needed that 1gb fat32 partition with the iso and boot files on it.

I booted up using gparted livecd again. I first used partimage to backup my edgy and my ntfs partitions. I stored them on a fat32 partition I hooked up to usb (this is not sda, it's sdb1, don't get this usb external drive confussed with fat32 internal sata drive on pci card). I deleted the fat32 and swap partitions. I grew my Edgy install to add 1gb in front of it, created a new swap in front of that. So now partition table of hda and sda is

hda1=NTFS 
hda2=swap 
hda3=Edgy (ext3)

sda1=120gb fat32

Then I mounted Edgy's partition thru gparted livecd to make sure that menu.lst and fstab called out correct partitions. I realized, what the hell????? They are already correct??? How in the world did that happen??? The kernel location was already hda3 and grub's files location was already (hd0,2). Even the fstab was correct, swap on hda2. HOW IN THE WORLD I THOUGHT?????

So I figured I would have a huge mess on my hands so I tried booting edgy normally and sure enough, it came up fine!!!!!!!! AWESOME!!!!! So I figured next test it to make sure Win2000 survived. Before I did that I put some mp3's on the fat32 drive (sda1) while in Edgy to make sure Win2000 could read it. 

Well when I booted back into Win2000 to make sure everything was ok, grub found it but a black screen came up first and said that a FAT32 partition was found and needed to be checked or something like, it said do you want to continue, I assumed it meant continue and check it, I tried hitting y but it didn't take so then by default it did no. Win2000 came up but very very slowly! I clicked on MyComputer and it just sat there with no drives showing. So I went to Admin, Computer Management, Storage and tried to open the hard drive management tool and that just sat there as well. Finally the mycomputer window came up and there was

C=NTFS obviously win2000
D as the cdrom
E don't know if this is that old fat32 partition that was 1gb with iso and boot files on it or what???? OR is it my swap partition or is it Edgy?????
F which is the 120gb sata drive, FAT32

Well I tried to click on the F drive and it showed the music I copied onto it, I was even able to play in Windows Media Player. 

**Questions:**
*The black screen during Win2000 bootup couldn't have been referring to the PCI Card SATA Drive drive could it? (yes I have the drive installed correctly and hardware device manager states this PCI card is working properly)
*Why is windows seeing and giving a drive E?? 
I think that's why mycomputer is taking forever to load, it's trying to read a non existant fat32 partition or a linux partition formatted as ext3 or a swap partition.
*Does anyone else have a problem with Edgy choking while try to read ext3 or swap partitions on same drive as Win2000?

I poped in the LiveCD of gparted again because it's got Testdisk on it. I didn't want to run testdisk from within Edgy because of hda2 and hda3 being used. Testdisk told me that there were 16 heads per cylinder but it probably should be 255. Despite using test disk and it telling me that my currect partition table was ok but it also told me about the heads per cylinder, I used the gemotry tool to change it to 255. Another weird thing testdisk also was saying that my swap partition id was something really werid and my Linux partition id was Ambius???? So I used geometry tool and identified them as 83 for ext3 and swap id as 82. 

Questions:
Why did my id's get all messed up??? Because I changed the number of heads?
Is it possible that the alt install cd for Edgy isn't iding the partitions correctly? 
Wow do I chkdisk within win2000, I can't find it anywhere? 

Well changing the heads per cylinder really f'd something up, why didn't I just leave it alone!!!! You can only learn when you try I suppose. Now windows couldn't even boot, it said unable to boot partition. So I went back into testdisk within gparted live cd and sure enough, there was only 1 partition now, that was labeled Linux. WOW!!!! Oh my gosh I thought, I just lost all of Win2000 (didn't really matter since it's a new install) So i used testdisk to find lost partitions and it was taking way to long so I had to go to work. So I am not sure of the outcome yet but I am sure it's fine because I didn't write anything to the disk after I changed the 16 to 255. So it should just recreate the partition table. 

**Questions:**
Why does testdisk tell me that the heads per cylinder is 16 but it should be 255?? Can anyone explain this?
I will probably have to recreate the Boot Sector for Win2000, should I use Super Grub Disk or just use Win2000 and boot it and use FIXBOOT command? 

Any opinions or suggestions would be greatful!!

---

### Post by jobox on 2007-04-09
Ok 255 heads? That really freaked me out. I checked all the old drives in my drawer and they all have 16. Unless you have some freaky hardware i'd say 16 was correct.
To be sure you should consider reading the labels on the disk itself. Most will say C/H/S: and then the numbers. for Cylinders/Heads/Sectors. For comparison purposes here are the numbers of my 61.5GB IBM Deskstar. C/H/S: 16383/16/63.

Other than that I've never had my windows trying to read anything but FAT or NTFS. Not ext2/3, Reiser or swap. or even extended. 
Win2k has fdisk in command line and disk-management from gui. Afaik both report windows as uknown partition or unformatted. Also keep in mind that an extended drive is also a drive. that might account for any 1 additional drive yousee in widows that you didn't expect.

That said i can't wrap my head around your case. If you're still in need try to explain your current state and your current major problem. As a general advice; you'll learn less but work more if you just reinstall both os'es and make real sure your correct before tweaking geometry ;)

---

### Post by dannyboy79 on 2007-04-09
ok, i got it on the 255 and 16. maybe testdisk was written for servers or humongous hard drives??? whats a head anyway, it that the platter or is the platter tha cylinder? why would the developer of testdisk put a message int here telling people that the heads are at 16 and it should probably be 255? anyway, i didn't create any extended partition so that can't be what E was? so you're saying that windows doesn't even see the swap or ext3 partitions? unless of course I install fs driver and mount the ext3 correct? well what I did was do a full search using testdisk and it only found my last ext3 partition so I figured somehow win2000 and the swap partition got screwed up and hopefully that's why win2000 was choking when I tried to bring up disk management and also mycomputer. it's ok since I used partimage to back up my ntfs partition onto a fat32 usb external drive. I want to test and see if partimage works for backing up ntfs and then restoring it anyway. then I don't have to use ghost anymore!!! i will say this, if it works it's most likely because there's no fragmentation since this was a brand new install and all I did was go thru the updates and that was it. so I'll post back with my failure or success.

---

### Post by dannyboy79 on 2007-04-10
UPDATE:
What I did was use partimage to backup each of the os installations as well as used tar from puppy to backup all the content of the partitions. but no matter what I did with test disk or whatever the partition table would just not recover no matter what. testdisk kept wanting to only write 1 linux partition to the partition table so I am not sure whats that's all about. I kept getting partitions not ending on a cylinder or somerthing like that when I would do fdisk -l within puppy.

This may all had something to do with installing from the alt install cd iso and boot files located on the second partition and after the install, I checked both win2000 and edgy and they were fine and then since I didn't beed that partition I removed it, then  also removed the swap I made for edgy, then I made a new swap, and the space that was left over, about 1gb, I grew my ext3 edgy install partition forward to meet where the new swap ended. i am guessing that was too much for the disk? I don't know. it's a seagate 10.2gb from an eMachine.

So to start again I used the gparted live cd and completely removed all exiting partitions and wanted to start fresh. I probably should have used some program to write zero's to the disk to wipe everything but I am hoping a format is good enough. so I create my hda1 as NTFS, my hda2 as ext3 and my hda3 as linux swap. i did each of these as seperate tasks instead of doing it all at once thinking this may be better, is it? after that was all done, I did a restart of the computer to make sure those changes took. when I booted into gparted live cd, oddly enough when I mounted hda2, it actually had a folder within it called lost+found. I thought, MAN, how in the world did that survive deleting the partitions and reformatting and changing the partition table (hda3 used to have linux on it and now I made hda2 have it on it) but apparently it did. that kind of scares me and I hope I am not going to regret wiping the drive with some tool. i wouldn't even know what to use as there is nothing to write zeros to the drive within the gparted live cd despite it having almost everything a person would need. it has fsck, it has gparted, it has a terminal,  it has partimage, it has midnight commander and it uses fluxbox as it's WM. sorry for getting off topic.

Anyway, I wanted to find out if partimage can backup and restore ntfs since many ask about it so I restored my ntfs partition (i did the backup without compression and the drive was not fragmented since it was a new win2000 install. i backed it up to an external fat32 usb disk which has just 1 partition on it) and the restore went fine.

I then tried to boot that using super grub disk and I got disk read failure. huh? so I figured since it was restored from partimage that maybe an automatic full repair using the win2000 install cd would fix things up. when the win2000 cd searched for win2000 installs it did find it. GREAT! (i had restored it to hda1) so I ran the automatic full system repair, and after about 5 mins, it said it was done and that the machine was going to reboot. what's odd is that the portion of the mbr where ntldr or grub reside did NOT get overwritten when I did the full system repair becuase when I rebooted the machine there was grub giving me an error 17 and I know why.

I got grub error 17 because currently the grub installed in the mbr points to (hd0,2) and now that partition is the swap partition. my next step is to reinstall grub to the mbr of the disk and point it to the new location of edgy which will be (hd0,1). the way that I am going to do that is by booting to puppy and mounting the hda2 partition and using the tar command to extract my tar file of the system. I know then I'll need to recreate /proc and /since those aren't really folders. come to think of it I never excluded those, I hope this doesn't hurt my chances of restoring edgy. it shouldn't? even if it does this will all be a great lesson for a real system. See this is merely customer's computer and I can do whatever I want with it because before I started this whole mess, I backup all his important files onto a seperate disk way away from all this mess!!! SO I can always just reinstall edgy, it's just that I did about 4 hours of setup on it. 

I'll post back with any success or failure.

---

### Post by dannyboy79 on 2007-04-12
UPDATE: using partimage to backup an NTFS partition to an external disk formatted as fat32 did NOT work. I used gparted live cd to create the new partition and ntfs fs. when I used partimage to restore the image partimage didn't give me any errors so I was hopefuly that it worked. However upon booting up, grub gives me a disk read error. so I figured all I have to do is run check disk within the win2000 cd recovery console. well I ended up doing a full auto system repair and still got the same thing. I even tried fixing the mbr so that it would just boot up using ntldr but still get the disk read error. Apparently partimage just might not be there yet as far as backing up and restoring NTFS partitions. My partition was not fragmented at all either. the only thing I can think of was that maybe there was so much garbage left over from the previous install or whatever (I didn't write zeros to the drive, I only deleted partitions, recreated them, then formatted) so maybe that's why it didn't work but I am going to try again. I have a little 3.2gb hard drive that i will write zeros' to first, then go thru the whole process that I have done here so that I can finally answer the question, 

CAN PARTIMAGE BACKUP AND RESTORE MY WINDOWS INSTALL?? (meaning NTFS fs)

---

