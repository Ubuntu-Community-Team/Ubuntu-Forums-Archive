---
title: "Dual boot Ubuntu 14.04 and windows 8.1 on toshiba satellite"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by pigmelt on 2014-05-07
its been a long time sence i have used Ubuntu so i feel like a complete beginner. 
 i have a toshiba satellite P875-S7310 laptop it has an i7 processor and 8 gig of ram, i would like to dual boot Ubuntu 14.04 and windows 8.1. i have resized windows with windows tools  and have about 350 gigs unallocated space on hard drive. i have been reading a lot of posts in the forums and am almost in information over load. i am using the live session from dvd to post this so i know that most everything works that way. when i go to install Ubuntu does not see windows at all so i went to "something else" it sees the ntfs partitions and unallocated disk space but i'm not sure how to proceed with the partitioning for Ubuntu. if i go ahead and install to the whole hard drive can i use the restore dvds i burned when i first got the laptop and reload windows? if i can then i may just go that route. i do have some games on steam that i like but they are not on linux so the only reason for windows is gameing.

---

### Post by squakie on 2014-05-07
The unallocated space will be the space you freed for Ubuntu.  When that shows, highlight the unallocated space.  You should see the option there for "new".  Create a swap partition - if you plan to hibernate make the swap space twice the size of your physical memory.  The system will think for a second, show the new partition you want (not yet created), and a reduced unallocated space.  You can then create a separate partition there with a mount point of / and with the size you have free you might us well make it at least 30gb.  Again it will think for a second, show the additional partition (not yet allocated) and again reduced unallocated space.  There are many ways to partition, and I'm sure others would suggest additional, but I would just create another partition in the unallocated space that is left and make it's mount point /home.  Do not touch your Windows partitions (there should be several since it's Windows 8).  But....before you do any of that, check your BIOS settings - you want fast boot turned off and secure boot turned off.  You may want to search and read the other posts on the forum regarding installation for dual booting with Windows 8.  As always, make sure you have:

- created any backups you might need
- have recovery media (on my Toshiba laptop there is an option in the Toshiba tools to create backup media so you can restore to factory defaults).  If you have done that, then indeed you can use your entire disk drive if you want to.  Just be sure you have those backups and backups of any of the Windows programs and data you would need to reinstall.

---

### Post by pigmelt on 2014-05-07
thank you squakie for the reply i do have the three restore dvd from the backup media option. just not sure if that would completely remove the Ubuntu install if i give my son this machine at a later date, as most of the stuff he does requires windows programs, i may still try the dual boot option just unsure about it.

---

### Post by Dreamer Fithp Apprentice on 2014-05-07
> **pigmelt said:**
>  if i go ahead and install to the whole hard  drive can i use the restore dvds i burned when i first got the laptop  and reload windows?That would be a really bad idea. I won't say  you COULDN'T restore the Windows system, depends on the nature of those  backups, but any data on it and any tweaks you've made since would be  history, and anyway, most likely you'd be back to square one, still  wanting to install Ubuntu facing the same question.

> **pigmelt said:**
> i7 processor and 8 gig of ram,and have about 350 gigs unallocated space on hard drive.Way plenty.:)
 > **pigmelt said:**
>  it sees the ntfs partitions and unallocated disk space but i'm not sure how to proceed with the partitioning for Ubuntu.Use the unallocated space. Or better yet, divy it up into more partitions and use one of them. 350 is way more space than you can possibly use for any Ubuntu. I have 5 partitions intended for OSs, with systems on 3 of them at the moment. My largest system, the one I install everything and try everything on, only occupies 5.2 giB of the 12 giB partition. That's lighter that most I imagine, because I use an ultralight DE, and I clean up the useless cruft with scripts and bleachbit, but even with all the bells, whistles, cutesypie animations, and bloat of a full blown pimped out gnome 3 and unity with multiple DEs,  I'd be surprised if anyone who doesn't keep there personal data on their system partition uses 20. Somebody chime in if I'm wrong. With that kind of space to spare, I'd make at least 2 partitions for OSs. You never know what you might want to try in the future and if you start running short of data space you can repurpose one for more data.

With 8 giB of RAM if you don't use "sleep" or "hibernate" you don't need a swap partition. If you do use those features, one of them uses a lot of swap space. Frankly I get which is which confused but 5 minutes with a search engine should answer that. Even if you need the swap space, and here I'm on shakier ground and perfectly happy to be enlightened by someone who knows better, I've never seen a convincing reason to make a swap partition unless you have a seperate DRIVE to put the partition on. If you put it on a seperate DRIVE, not just another partition on the same drive, you may get some speed advantage, depending on details of drives and controllers. But not making a swap partition doesn't mean the system can't swap - it can swap to a directory in the root partition. And doing it that way the allocation of drive space in the future is more flexible. In practice I've never seen my system swap and I only have 4 giB of RAM. The cpu has always been a more likely resource constraint for me. That of course will vary depending on all sorts of details of usage and hardware. I install everything to one partition, keeping it simple. Everything software and system wise I mean. I keep data (meaning stuff you've written, epubs, saved documents, pictures, sound files, movies, your maps to buried treasures, notes you made on how to blackmail your congressperson, stuff like that) on a seperate partition, which I strongly reccomend. Furthermore that's what I suggest you do with the bulk of your available drive space - make into 1 or 2 data partitions. I wouldn't worry about the standard old bugaboo of formatting a data partition so either Windows or Gnu/linux systems can read it. There are reasonably good NTFS drivers for linux and I'm told there are reasonably good ext3 (4 I don't know, you might want to check on that) drivers for Windows.  Each system needs enough space in a file format native to it to run software (that includes executables you've downloaded, like exe or deb, or archives containing them). Sometimes permission issues cause strange problems if, for instance, you unpack an archived bit of linux software on an NTFS partition and install it. [B]But other that that (I have NO idea why my typing just switched to bold) I know from experience 'nixes have no problem reading NTFS or FAT32 and Windows is reputed to have no problem with ext3, after installing the drivers). And keeping all your data in a seperate partition makes everything tons easier to backup since you seperate the tasks of backing up systems from backing up data. And it make installation of new systems at least a little easier. OK, I'm evangelical on the subject of seperate data partitions. Not everyone agrees. Of course, they're wrong and I'm right, always, but they don't know that. What can I say, not everyone is equally enlightened. :) Anyway, if you keep data seperately /home will be pretty small, mostly config files and there really isn't much point in putting it on a seperate partition in that case. If you want to reinstall and preserve those settings, to me it seems easier just to copy them.

So, to summarize, if it were me, I'd:

Divy that space up into a couple of 20 giB partitions (or more if you think you might like to try several OSs) and put the rest in a data partition. Install to one of 20s and leave the other for later.[/B]

---

### Post by squakie on 2014-05-07
THAT sounds like really sound advice!   I also wouldn't wipe out Windows myself.  I still dual-boot and I've been using Linux for years.  BTW - I personally don't use hibernate.  With the speed of today's hardware and OS's at boot, to me hibernate just seems like a waste.  Just do a clean shutdown.  I only posted what I did as I thought for someone who was sort ofback to square one it would be the easiest for you.  Also, I've always shyed away from writing to an NTFS partition from Ubuntu/Linux.  Just personal preference! ;)  As I mentioned, everyone has a different idea on how to partition, and the truth be told one is (edit: forgot the word "no" here) more correct or more wrong than the other - just as                                                                                                   [**[COLOR=#000000]Dreamer Fithp Apprentice[/COLOR]**]("http://ubuntuforums.org/member.php?u=1435975") mentioned.  It all really depends on what you are going to be doing with your system, and how easy it is to update to a new release without losing your data, etc..  Isn't it nice we at least get all of that freedom of choice?  ;)

---

### Post by Dreamer Fithp Apprentice on 2014-05-07
Jeez, I must the slowest typist on the planet, or maybe I just have more interruptions (I've got like 64 cats here). When I started that post the question was unanswered or I wouldn't have ignored the intervening posts. 

Thanks for the kind works, Squakie. I'm glad you posted. Until I saw yours I didn't realize how lacking mine was on practical, nuts-and-bolts, procedural details. On using NTFS, it's worked pretty well for several years now in all respects but permissions. 

One thing I should have mentioned is that as long as you have the drive space, there is simply nothing, absolutely nothing, to be gained by NOT dual booting. Installation won't take any longer and you can set grub to time out and boot Ubuntu after only a second or even not to show a menu at all so boot time isn't an issue either. And one more thing I just thought of - if you'll download and burn to cd Clonezilla before you do anything else you can completely back up the Windows partition AS IT IS, with everything you've installed and all the tweaks you've made since you made those recovery disks, BEFORE you do anything else. That's the uber-safe way. Clonezilla rocks. Once you've installed and have 2 working systems, each can be used to back up the other whenever you make significant changes. 

BTW,
> **squakie said:**
>  As I mentioned, everyone has a different idea on how to partition, and the truth be told one is more correct or more wrong than the other - But which? ;-)

---

### Post by oldfred on 2014-05-07
I always think partitioning is personal, depending on how you will use system. And I find my own optimal partitioning changes over the years, but I get a new hard drive or system by then and can reorganize.

I only had /, swap and a shared FAT32 partition for 3 or 4 years. But then converted to a new hard drive, changed shared to NTFS, added a new Linux formatted data partition for most new data, and many 20GB / (root) partitions which all still are filled with something either old or very new.
But many users may not have much data. Some want to save large amounts of data. Some may keep Windows separate from Linux and not need to share data between systems. And experience helps as when you have Linux data partitions you also have to set ownership & permissions. 

For a new user a NTFS shared data partition would be my first suggestion. Second would be separate /home, but I do not have a separate /home as I use the data partitions.
I do like smaller system partitions for both Windows & Ubuntu, but Windows likes to save and needs more space for everything, so its system partition does need to be larger than Ubuntus.

---

### Post by squakie on 2014-05-07
> **Dreamer Fithp Apprentice said:**
> ....(my comment about partitions here)....But which? ;-)

Thanks for pointing that out - I went back and edited the post so the word "no" is included ;)

---

### Post by pigmelt on 2014-05-08
thank you Dreamer Fithp Apprentice i feel kind of ignorant i don't rember how to reply with quotes. but i don't really have any twikes or data other than pictures on this system. and the restore dvds i was talking about are burned from the toshiba restore recovery media program sience you no longer get the actual windows and drivers disk with a computer any more. so i'm not really worried about losing data i'll burn the pics to a cd before i try this.
thank you oldfred i'm glad to see you looking at this, and i'm not very confident with the partitioning part of this.
thank you too squakie i need all the support you guys can give.

 when it comes to the partitioning for the mount point do i just select the unallocated space and the add button and that is it, or do i need to give it some space like 200 or so mb, and then after that i select the the left over space and create a 25gig root space then again with whats left a say 50 gig home then a 8 gig swap then the rest for data? as i said this is the part i feel i have not much confidence in. i don't think i be able to work on this till Sunday evening so that gives me time to try and get a little more confidence.

---

### Post by squakie on 2014-05-08
You'll have to tell it how much space to use - but it will come up with a box where you specify the size, the type, the mount point - and I can't remember the rest - perhaps format this partition?

I used to have a guide on my ubuntu one account, but I don't know if any of that works any more or not.  If I find it and can get the link I'll post it here.

---

### Post by squakie on 2014-05-08
OK. I found it.  Be forwarned it is *OLD* !!!   So, skip the downloading part, skip the burn to dvd or cd part, follow the part that shows selecting something other than the default for which/how to install to disk.  When you reach the part about about creating the free space - skip it.  First off - you have already created your free space.  Second - the way posted there is no longer the way recommended.  It shows resizing a NTFS partition via the installer, whereas it is now highly recommended to shrink partitions in Windows using the Windows tools.  Then continue on where it shows creating the ubuntu partitions - remember you can adjust to add what ever partitions you may want.  I hope that is of some small help to you.

So, with that said, here's the link:

[http://ubuntuone.com/6snmL8cnGbpYPBegqcHrnr](http://ubuntuone.com/6snmL8cnGbpYPBegqcHrnr)

---

### Post by Dreamer Fithp Apprentice on 2014-05-08
This is about 5 years old but I don't think anything has changed: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) The point of good GUI is that you don't HAVE to know ahead of time exactly how it works, you just start it and it tells you,  like a branching network of roads, but all the roads have really good signs. That's the ideal, not all aps achieve it, but most do reasonably well.  If you'll back up your pics as you say, and back up Windows with Clonezilla, there is nothing to worry about. Given the backups I don't think you CAN do anything that wouldn't be reasonably easy to fix. Well, maybe you COULD. Clonezilla won't repair the hardware if it falls off your surfboard into the ocean for example, but you know what I mean.

---

### Post by pigmelt on 2014-05-09
Thanks i have a lot to look at since i work 2nd shift ill most likely try the install on sunday i have been putting to gether a check list of what i need to do i'll post that saturday night after work again thanks i have a lot to study on this.

---

### Post by squakie on 2014-05-09
In the installer, the screen captures in the document I posted are for creating the partitions.  It is basically similar to gparted, but there's no need to learn gparted or run it separately - it's all in the installer.  And.......if you are going to replace Windows (I wouldn't) all you have to do is select the "replace" option.

---

### Post by ubfan1 on 2014-05-09
You might have some video issues with the NVidia, so you might need nomodeset for the first boot, until you get the nvidia drivers.  Other boot options might also be necessary.  Don't get partitcularly concerned if you just get a black screen first time, there is a solution.

---

### Post by pigmelt on 2014-05-09
thank you ubfan1 i am fully expecting some things to go south at first and will be very happy if they don't.
 i think i have the partitioning figured out here is how i have the lay out for now: root/ (ext 4) 20 gigs, /home (ext 4) 20014 gigs, swap 16 gigs, /media/shared data ntfs 100 gigs. i think i'll have to take some from one of them to make an uefi partition but not sure. would like some input thanks.

---

### Post by squakie on 2014-05-10
> **pigmelt said:**
> ..../home (ext 4) 20014 gigs....

Surely you don't have a 20+TB drive?

---

### Post by squakie on 2014-05-10
And remember - you can define all of that right in the installation process itself by just selecting the manual (other?) option.

---

### Post by oldfred on 2014-05-10
If booting with UEFI or drive may in the future be installed in a new UEFI system, you should have an efi partition near the beginning of the drive. Windows default is 100MB, but 300MB or more if drive is large TB type does not 'waste' much space.  If SSD keep on smaller size. 
Even if BIOS boot, I suggest including the efi partition space, but then you need a tiny bios_grub partition. If UEFI it does have to be gpt partitioned and Windows only boots from gpt with UEFI. If dual booting with Windows in BIOS mode then drive must be MBR(msdos) then you cannot add efi partition, nor bios_grub as those are only for gpt.

I would not make swap 16GB. You will probably never use swap if you have 8 or 16GB of RAM. I like to have just a little like 2GB as someone posted it may boot a bit faster as it does not have to look for swap and not find it.
I do not recommend hibernation so you do not then need the large swap.

---

### Post by pigmelt on 2014-05-10
Sorry about the /home it's not 20014 it's 214gigs was kinda tired last night. Yes old freed it will be Jedi so I should put a 500mb partition in for that should it go before root? I will do away with swap and add it to data, 
Thanks for all recommmendations I am listening and open for the help.

---

### Post by oldfred on 2014-05-10
You can only have one efi partition per hard drive. So if Windows has already created one, you do not create another. All systems installed to the same drive share the one efi partition and have separate folders for their boot code.

---

### Post by pigmelt on 2014-05-10
Ok thanks I wasn't totally sure so I thought I'd ask that's one less thing to mess up I'm good at messing thins up.

---

### Post by pigmelt on 2014-05-10
ok here is what i have done so far:
1 windows restore dvds made from the toshiba media restore program
2 get ubuntu iso  and burn to dvd
3 try a live session to see if every thing plays well
4 disable secure boot
5 disable fast boot both in bios and power management set to normal boot
6 shrink windows with windows tools
 7 get clonezilla and clone disk image
 check and make sure all the above has been done.
next step will be to do the dual boot install after i get some sleep.

---

### Post by squakie on 2014-05-10
Sounds like you "did good".  I can see you're keeping Windows as well, and I think that's a good idea for now.  Since your thread title says "Windows 8.1", I'm assuming that means you have Windows 8.1 already installed.  That being the case, your BIOS will already be set to, and needs to stay at, UEFI/EFI.  It also means you won't need to create the EFI partition as OldFred mentions as it should also be there yet (assuming you didn't delete any partitions, and only shrunk the main Windows partition).

Good luck with your install, and be sure to post back any questions or potential problems you may encounter.  Also - be sure to let us know how it goes for you!

---

### Post by pigmelt on 2014-05-11
the only question left is when i make the root partition is it a primary or can it be logical, same question for the rest of the partitions. thank im on shakey ground here.

---

### Post by squakie on 2014-05-11
I might be completey wrong here, but I thought I remembered something about Windows 8 requiring UEFI/EFI and that the disk type (I think something like GPT) in which there aren't the primary/logical "thing" doesn't apply anymore.  I think Oldfred would be the one to know those answers and therefore the answer to your question.

---

### Post by squakie on 2014-05-11
Okay, according to what I've read on the net, including [this]("http://www.linux.com/learn/tutorials/730440-using-the-new-guid-partition-table-in-linux-good-bye-ancient-mbr-"), UEFI/EFI does require GPT partitioning instead of MBR.  The result is that in GPT there is no such thing as primary and logical partitions.

So, you won't have to worry about that.

---

### Post by oldfred on 2014-05-11
UEFI does require gpt partitioning. 
But you can install Windows 8 in BIOS boot mode but then have to have MBR(msdos) partitioning.

If your system came with Windows 8 pre-installed then it will be UEFI with gpt and your product key is in the UEFI. So you cannot reinstall it in BIOS mode.

Windows also requires an extra partition or two that may not have been backed up. The system reserved is just an empty unformatted partition to stuff serial number, DRM or encryption key type data into. With MBR partitioning that info was in the area between the MBR & first partition and that space does not exist with gpt.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by pigmelt on 2014-05-11
a big thankyou to everyone that helped. i have the dual boot working just fine, although on the screen where you select the operateing system it says Ubuntu then under that it says windows boot manager with a drive designation which will boot windows so every thing work fine so far. i used a 25gig root partition as primary and a 2 gig swap the remander of the free space went to the home partition which i made as logical. i would have made a ntfs shared partition but there was not a choice for that. oh and so far no video problems. so i'll mark this as solved. maybe someone willt be able to use this thread for their installation.

---

### Post by squakie on 2014-05-11
Congrats!  Now that everything is loaded and working (like video, wireless, etc,,) you may want to read up on gparted now.  You should be able to shrink your /home partition and add a NTFS partition as you want.  The main thing was to get everything installed first without throwing extra hickups into the mix!  Great job!  ;)

---

### Post by squakie on 2014-05-12
BTW - I could be very wrong here - but I thought if you scrolled down the file system types in the partitioning part of the install that you could specify NTFS.

---

### Post by LastDino on 2014-05-12
> **squakie said:**
> BTW - I could be very wrong here - but I thought if you scrolled down the file system types in the partitioning part of the install that you could specify NTFS.  You're not wrong. I think OP probably missed it or he was expecting something else. In this sort of situations you can easily resize /home so no real worries, but that is going to take some serious time depending on his /home size and place in partition table.

---

### Post by oldfred on 2014-05-12
If you use gparted in advance then you can choose NTFS.
But I think since Linux cannot use NTFS for system partitions it does not include that option in the install options.

---

