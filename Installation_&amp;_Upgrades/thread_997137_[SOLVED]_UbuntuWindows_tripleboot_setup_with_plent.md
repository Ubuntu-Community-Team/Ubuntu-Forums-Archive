---
title: "[SOLVED] Ubuntu/Windows tripleboot setup with plenty of partitions.."
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Lupusceleri on 2008-11-29
Hey there..

I put an all variants tag in front of this because I guess it applies to all distros. Anyway, here goes. First a short summary of the story, for all of you that think my post is a clear case of TL;DR. ;)

--------------------------------
Dualboot system, Intrepid 64bit/Vista Ultimate 64bit. Two harddrives, one new (SATA, 500 GB, 16 MB cache), one old (IDE, 200 GB, no clue on cache).

Put OS, swap, and documents in separate partitions on the new one, put programs on the old harddrive (ubuntu/windowses programs each their own partition). That way OS/programs don't have to read the same harddrive at the same time, thus giving me an extra fast computer (theoretically). Is that a smart idea?

Some generic noob questions:

1) Swap partition of 4 GB rather than the "recommended" 2 GB, does this slow my system down? Harddrive space itself is not an issue.
2) Can I put /home on a FAT32 partition (rather than ext2 or ext3), so Windows can read/write it without needing extra drivers?
3) What is the Linux equivalent of Windows' "Program Files" called? /usr/var?
4) Will putting my programs on the IDE drive (with OS/documents/swap on the SATA), in fact slow my system down, since SATA speed/cache > IDE speed/cache?
--------------------------------

On to the real post.

I have a disc with Intrepid Ibex, AMD64 Ubuntu, ready to install. For the rest Vista Ultimate (64 bit).

The plan is, to make a dualboot system: Vista, and Ubuntu. I know I know I can just go all out Ubuntu, but I'm a noob at it and I like having at least one OS I know inside out.

I'd also like to use various partitions to keep it all organized.

I have two harddrives as of right now:

1) 500 GB Western Digital SATA harddrive, 16 MB cache. This one is brand new, still in the box and never used at all. I guess this will be /dev/sda.
2) 200 GB Western Digital IDE harddrive, no clue how much cache but obviously less than the new harddrive. This one is about three years old now, and used to be my main harddrive so it's been used alot. This'll probably be /dev/sdb.

My idea was, that it is a good idea to separate your documents from your OS and programs, by putting them on a different partition. I also think, that it is useful to install your programs to a different harddrive (and/or partition) than your OS. Since, I figured, when you have your programs on another physical harddrive, things should run faster since you don't have to thread both the OS and the program on the same harddrive?

Which brings me to the question, what is Ubuntu's equivalent of Program Files? /usr/var/ or something right? Does Ubuntu put files anywhere else, when it installs new programs, too? Or is it, if you installed the right files on a different partition of course, possible to format the main Ubuntu partition and then reinstall Ubuntu (selecting that same partition for your program stuff of course), so that when you start your fresh Ubuntu you have all your programs and settings back right away?

I read in the stickies, that your swap partition should be at least twice your RAM. I have 1 GB RAM, but I might upgrade in the future, so I plan on making a swap partition of 4 GB. Will a swap partition that is "larger than recommended", slow my system down? I've got plenty of room on the harddrive, so that it's taking up 2 GB extra room doesn't bother me at all.

As for the documents partition, I plan on making an NTFS partition on the new harddrive for it (I want it to be usable from Windows, and preferably Linux as well). FAT32 sucks, since you can't put any files over 4 GB on it. ext2/3 can't be read by Windows unless you download special drivers. I'll use the ntfs-config program to read/write the Documents drive from Ubuntu, so almost all my files will be stored there.

I have the idea to then make another, 8 GB sized, FAT32 partition for Ubuntu's /home, so that I can put files on there from Windows in case my Ubuntu goes boom and can't read/write NTFS anymore. Is that a good idea, and/or possible?

All that aside. What use of partitions would you guys advise? My current "should-be-best" plan is this:

[LIST]
[*]/dev/sda - The new SATA drive.
[LIST]
[*]/dev/sda1 - NTFS, 60 GB, Windows Vista 64bit, Primary partition, boot.
[*]/dev/sda2 - Extended partition, total of 70 GB.
[LIST]
[*]/dev/sda5 - Ext3, 60 GB, Ubuntu Intrepid 64bit, Logical partition.
[*]/dev/sda6 - swap, 2 GB, swapfile thingie, Logical partition.
[*]/dev/sda7 - FAT32, 8 GB, /home and temp-documents, Logical partition.
[/LIST]
[*]/dev/sda3 - NTFS, 370 GB, Documents, Primary partition.
[/LIST]
[*]/dev/sdb - The old IDE drive.
[LIST]
[*]/dev/sdb1 - NTFS, 140 GB, Windows Programs, Primary partition.
[*]/dev/sdb2 - Ext3, 60 GB, Linux Programs, Primary partition.
[/LIST]
[/LIST]

What do you guys think, is it a good idea to do it this way, or should I just keep the programs on the new drive but on a different partition than the OS? Should I put my documents on the old harddrive (it seemed smarter to me to put them on the new drive, since that one is less likely to die from old age)?

Thanks for reading this far!

Greetings, Lup.

---

### Post by mikewhatever on 2008-11-29
> **Lupusceleri said:**
> 

Which brings me to the question, what is Ubuntu's equivalent of Program Files? /usr/var/ or something right? Does Ubuntu put files anywhere else, when it installs new programs, too? Or is it, if you installed the right files on a different partition of course, possible to format the main Ubuntu partition and then reinstall Ubuntu (selecting that same partition for your program stuff of course), so that when you start your fresh Ubuntu you have all your programs and settings back right away?

While /usr holds most of the binaries installed from the repositories, many other files are scattered about the system, so I don't think it's possible.

> I read in the stickies, that your swap partition should be at least twice your RAM. I have 1 GB RAM, but I might upgrade in the future, so I plan on making a swap partition of 4 GB. Will a swap partition that is "larger than recommended", slow my system down? I've got plenty of room on the harddrive, so that it's taking up 2 GB extra room doesn't bother me at all.

With 1GB of RAM, or more, you'll most probably never need more then 500 MB of swap. If you plan on suspending to disk, then it should be the size of RAM.

> As for the documents partition, I plan on making an NTFS partition on the new harddrive for it (I want it to be usable from Windows, and preferably Linux as well). FAT32 sucks, since you can't put any files over 4 GB on it. ext2/3 can't be read by Windows unless you download special drivers. I'll use the ntfs-config program to read/write the Documents drive from Ubuntu, so almost all my files will be stored there.
I've never seen a document as large as 4 GB, but that is up to you.
Personally, I'd advise to keep it as simple as possible, especially if it is your first try. Setting up a triple boot system is a complex task, and the more partitions, the greater the complexity.

---

### Post by falcon61102 on 2008-11-29
I agree with mikewhatever, setting up a triple boot system, especially with two MS OS's is tricky business and it's best to keep it simple.  

One way to keep things easier to manage is let each OS store the programs where they normally store them.  I understand what you are trying to do, but it's going to get real complicated real fast as you start loading programs on seperate partitions for each OS.

That leads me to a question, why both Vista and XP?  I notice that one is 64 bit and other 32 bit, but why two MS OS's?

As far as your SWAP goes, like mikewhatever said, you probably won't ever use more than 500 mb of your SWAP but on the safe side I normally use  1 gig.

---

### Post by Lupusceleri on 2008-11-29
First of all.. Thanks a ton for the quick replies!

> **mikewhatever said:**
> While /usr holds most of the binaries installed from the repositories, many other files are scattered about the system, so I don't think it's possible.

Alright, that sounds very similar to Windows where most of the files get stored into Program Files, but where things also go to the ProgramData folder and the registry. I wasn't really looking to be reinstalling my OSes time after time anyway! ;) So, even if just most of the data (which should be the biggest read/write load, AFAIK) goes onto the second harddrive, that's cool.

> **mikewhatever said:**
> With 1GB of RAM, or more, you'll most probably never need more then 500 MB of swap. If you plan on suspending to disk, then it should be the size of RAM.

Ok, thanks for the clarification. I figure I'll stick with 2ish GB just in case I decide to get more RAM later.

> **mikewhatever said:**
> I've never seen a document as large as 4 GB, but that is up to you.

I can think of one: just about any DVD .iso file. As I'll be putting downloads in the Documents partition as well. Basically Documents would be anything I don't want to lose when I have to format my harddrive.

> **mikewhatever said:**
> Personally, I'd advise to keep it as simple as possible, especially if it is your first try. Setting up a triple boot system is a complex task, and the more partitions, the greater the complexity.

Hehe, I see where you're coming from. This isn't my first linux attempt, I have tried redhat/suse years ago (but I failed there, the things didn't support my WLAN card and cabled LAN wasn't an option.. so in the end I just ended up formatting the HD and going back to full Windows).

And one month ago, I decided to give it a go again and installed Xubuntu (including bootloader) to my pendrive. I liked it a lot then, soooo quick startups! I could finally find my way around Linux, and beside that my WLAN even worked. ^^ So I decided to give Ubuntu a go again on my desktop PC now, and here we are hehe.

> **falcon61102 said:**
> I agree with mikewhatever, setting up a triple boot system, especially with two MS OS's is tricky business and it's best to keep it simple.

Yup.. on second thought why exactly would I want to keep winXP? If I want the fast and no load of nonsense OS I've got Ubuntu I guess. The only reason I could possibly think of is to play certain games.

Ok, I'll remove XP from the equation then.

> **falcon61102 said:**
> One way to keep things easier to manage is let each OS store the programs where they normally store them.  I understand what you are trying to do, but it's going to get real complicated real fast as you start loading programs on seperate partitions for each OS.

Right, well, previously the "replace C letter with D in the installation window every time you install a new program" has worked flawlessly for me, in Vista. So.. this added difficulty-grade shouldn't be a problem at all for Vista.

It should be easily doable for Ubuntu too, unless you guys say Ubuntu has issues with a different partition (or mount point or whatever you want to call it) for /usr? I know I can select where to put /usr when I'm installing (X)Ubuntu, so I don't see why it should go wrong if the OS natively supports it without any hacks at all?

---

### Post by falcon61102 on 2008-11-29
> **Lupusceleri said:**
> Yup.. on second thought why exactly would I want to keep winXP? If I want the fast and no load of nonsense OS I've got Ubuntu I guess. The only reason I could possibly think of is to play certain games.

Vista should be able to run the majority of the games out there currently and if some give you any trouble, try running them in they compatibility mode.  If you right click on the .exe for the game, in one of the property tabs you will find the compatibility modes which allow you run programs that were specifically designed for one OS.  But you shouldn't have too much trouble, there are only a few things that I've run into that didn't run in Vista that ran in XP and those programs were really old anyway.

> **Lupusceleri said:**
> Right, well, previously the "replace C letter with D in the installation window every time you install a new program" has worked flawlessly for me, in Vista. So.. this added difficulty-grade shouldn't be a problem at all for Vista.


And yes, you can do this in Ubuntu for many third party installs as well.  Most of your software will be installed through the Add/Remove programs or Synaptic Package Manager and will be installed to default places, but for third party installs such as games, you can choose different paths for them.

---

### Post by Lupusceleri on 2008-11-29
Short update on the plan for the harddrive partition setup then. Working on updating the OP right now. :)

[LIST]
[*]/dev/sda - The new SATA drive.
[LIST]
[*]/dev/sda1 - NTFS, 60 GB, Windows Vista 64bit, Primary partition, boot.
[*]/dev/sda2 - Extended partition, total of 70 GB.
[LIST]
[*]/dev/sda5 - Ext3, 60 GB, Ubuntu Intrepid 64bit, Logical partition.
[*]/dev/sda6 - swap, 2 GB, swapfile thingie, Logical partition.
[*]/dev/sda7 - FAT32, 8 GB, /home and temp-documents, Logical partition.
[/LIST]
[*]/dev/sda3 - NTFS, 370 GB, Documents, Primary partition.
[/LIST]
[*]/dev/sdb - The old IDE drive.
[LIST]
[*]/dev/sdb1 - NTFS, 140 GB, Windows Programs, Primary partition.
[*]/dev/sdb2 - Ext3, 60 GB, Linux Programs, Primary partition.
[/LIST]
[/LIST]

---

### Post by falcon61102 on 2008-11-29
That should work.  Another option for your first drive would be to have:

/dev/sda1 as Primary NTFS Vista...
/dev/sda2 as Primary Ex3 Ubuntu...
/dev/sda3 as Primary NTFS Storage
/dev/sda4 as Extended with logical...

But either way you do it should work out fine.  And I don't know if you are going to be able to setup your /home as a FAT32 within the setup or if you're going to have to manually change that in the fstab after the install.

---

### Post by Lupusceleri on 2008-11-29
> **falcon61102 said:**
> But either way you do it should work out fine.  And I don't know if you are going to be able to setup your /home as a FAT32 within the setup or if you're going to have to manually change that in the fstab after the install.

I don't know whatever an fstab is, but I do know that I could set the /home mount point thingie in the setup too (just like /usr). The real question was if Ubuntu could handle having one of it's vital folders (/home) on a FAT32 type partition, rather than an ext2 or ext3 or whatever. :)

But from what I can read between the lines of your post - this "other than usual FS" for /home should not be a problem?

PS: mikewhatever, nice read in your siggy hehe..

---

### Post by falcon61102 on 2008-11-29
Everything else looked fine.  Setting up the /home as a seperate partition is not a problem, I'm just not sure if you can do it as a FAT32 within the setup.  If you can't do it there then you may be able to use the fstab to change that.  The fstab is a file that lists all of the partitions and mount points that are automatically mounted on boot.  If you were going to change the location of your /home or you wanted an NTFS partition to automatically mount on startup, that's the place to go.

Try the setting it up in the install and if that doesn't work, then go the fstab route.

---

### Post by caljohnsmith on 2008-11-29
> **Lupusceleri said:**
> I don't know whatever an fstab is, but I do know that I could set the /home mount point thingie in the setup too (just like /usr). The real question was if Ubuntu could handle having one of it's vital folders (/home) on a FAT32 type partition, rather than an ext2 or ext3 or whatever. :)

But from what I can read between the lines of your post - this "other than usual FS" for /home should not be a problem?

PS: mikewhatever, nice read in your siggy hehe..
Unfortunately, I don't think you will get very far if you use FAT32 for your /home partition, because linux relies on having the correct permissions/ownership data for each file/directory in order for most things to work. But I've never actually tried to use FAT32 for a /home partition, so maybe there's a small chance it would work. :)

Another alternative is to keep your /home directory in your main Ubuntu partition, and then just move your personal Pictures, Music, Videos, etc. directories to the FAT32 partition; then you can use a "symbolic link" to link them back to your /home directory. I've helped someone else do that before, and it worked perfectly for him so that both Windows and Ubuntu could both share the same Pictures, Music, Videos, etc directories. Let me know if you want help with it.

---

### Post by Lupusceleri on 2008-11-29
> **caljohnsmith said:**
> Unfortunately, I don't think you will get very far if you use FAT32 for your /home partition, because linux relies on having the correct permissions/ownership data for each file/directory in order for most things to work. But I've never actually tried to use FAT32 for a /home partition, so maybe there's a small chance it would work. :)

Aha, thanks for the enlightening. ;) That saves me one reinstall! :D

> **caljohnsmith said:**
> Another alternative is to keep your /home directory in your main Ubuntu partition, and then just move your personal Pictures, Music, Videos, etc. directories to the FAT32 partition; then you can use a "symbolic link" to link them back to your /home directory. I've helped someone else do that before, and it worked perfectly for him so that both Windows and Ubuntu could both share the same Pictures, Music, Videos, etc directories. Let me know if you want help with it.

Wow, that sounds very nice. Would you know if it possible to (if you let the ntfs-config program permamount the NTFS drives on boot) make such a "symbolic link" to my "Documents" NTFS partition as well? Or more specifically, to a certain folder on my "Documents" NTFS partition (that would be, in vista, <driveletter>\Users\Usernamehere\Documents)?

Thanks a load for all the quick support you're giving.. I appreciate it! :)

---

### Post by caljohnsmith on 2008-11-29
> **Lupusceleri said:**
> 
Wow, that sounds very nice. Would you know if it possible to (if you let the ntfs-config program permamount the NTFS drives on boot) make such a "symbolic link" to my "Documents" NTFS partition as well? Or more specifically, to a certain folder on my "Documents" NTFS partition (that would be, in vista, <driveletter>\Users\Usernamehere\Documents)?

Thanks a load for all the quick support you're giving.. I appreciate it! :)
You bet, you can first have your Vista partition mounted on start up by using that ntfs-config program (or just manually add it to /etc/fstab), and then you can create a symbolic link to your "Documents" folder or whichever folder you want in Vista's partition. It is as simple as something like:
```
sudo ln -s /path_to_Vistas_Documents_Folder /home/<username>/.
```
That would create a Documents directory in your home folder that is linked your Vista's Documents folder, so they are the same thing. Let me know how your installation goes or if you have more questions. :)

---

### Post by Lupusceleri on 2008-11-29
Path to vista's documents folder would be like this, if the label of the drive is Documents and I let ntfs-config mount it to the default location /media/Documents?

"/media/Documents/Users/Usernamehere/Documents"

I'll be doing the actual install tomorrow morning (way past bed time now). So I'll post here how it goes.

------------------

The only possible problem I can think of that might happen, is Vista and/or Ubuntu picking the IDE drive as /dev/sda, rather than the SATA drive.

No idea how to make sure the SATA becomes the main harddrive, rather than the IDE one. The settings/jumpers/cables/whatevers for the IDE would still have to be Primary/Master, even if I want my new SATA to be the boss? Do I have to adjust stuff in the BIOS maybe? When I googled this one I couldn't really find a clear answer on it. :)

So much for the good ol' jumpers and KNOWING for sure which drive would be the boss. ;)

---

### Post by caljohnsmith on 2008-11-29
> **Lupusceleri said:**
> 
No idea how to make sure the SATA becomes the main harddrive, rather than the IDE one. The settings/jumpers/cables/whatevers for the IDE would still have to be Primary/Master, even if I want my new SATA to be the boss? Do I have to adjust stuff in the BIOS maybe? When I googled this one I couldn't really find a clear answer on it. :)

So much for the good ol' jumpers and KNOWING for sure which drive would be the boss. ;)
When you go through the Ubuntu installer program, it will show you both of your drives and allow you to choose which to install to. You should be able to easily identify them by their sizes; if you want a better idea of what to expect, I would suggest checking out Herman's tutorials for installing Ubuntu:
[LIST]
[*][Installing Ubuntu using Manual partitioning method]("http://www.herman.linuxmaniac.net/p23.html")
[*][Installing Ubuntu by first Creating your Partitions with the Ubuntu Partition Editor]("http://www.herman.linuxmaniac.net/p22.html")
[/LIST]
One of the keys for making your multiboot setup as ideal as possible is if you can set your BIOS to boot the SATA drive on start up; that way you can keep Grub on one drive, and your drives will be independent of each other so that you are at less risk of problems. Let me know if you can't set your BIOS to boot the SATA drive though, and let me know how the installation goes.

---

### Post by Lupusceleri on 2008-11-30
Ok after messing around for ages trying to let my BIOS see the SATA disk, I found it. Ubuntu liveCD's GParted sees it too.

Now GParted wants me to make a partition table type. I can pick from:

msdos
aix
amiga
bsd
dvh
gpt
mac
pc98
sun
loop

I assume I need to pick msdos because I will be using Vista alongside Ubuntu, knowing that Microsoft OS's don't tend to like other-than-default stuff?

---

### Post by caljohnsmith on 2008-11-30
> **Lupusceleri said:**
> 
I assume I need to pick msdos because I will be using Vista alongside Ubuntu, knowing that Microsoft OS's don't tend to like other-than-default stuff?
Yes, you correctly deduced it; you should use the MS-DOS partition table format. :)

---

### Post by Lupusceleri on 2008-11-30
Ok great stuff! :)

It's done creating the partitions now, I should tell GParted to format them all I figure? And set the boot flag on /dev/sda1 (the Vista system ntfs partition).

EDIT: The UbuntuHome partition is ext2 rather than ext3 by the way, because I know there are stabile drivers for WinVista to read **AND write** to ext2, without problems. I'll do caljohn's virtual link thingie too.

---

### Post by Lupusceleri on 2008-11-30
Sigh.

Installed Vista, installed Ubuntu.

Reboot for the first time.

"BOOTMGR is missing.

Press CTRL ALT DEL to restart."

This is what I did:

1) Unplugged the PATA drive. Got the SATA drive to work for the first time, then booted Ubuntu liveCD to Gparted it. Made partitions, as described in OP, with instead of the FAT32 /home partition an ext2 /home partition, same size though. Drive was called /dev/sda. Set /dev/sda1 (for WinVista) as boot.
2) Plugged the PATA drive back in. Double checked that the SATA drive had booting priority over the PATA one in my BIOS. Booted Ubuntu liveCD, Gparted it again and the SATA drive was still called /dev/sda. PATA drive was called /dev/sdb. Exactly as I wanted it to be. So I created a new partition table (msdos) for the PATA drive, to be sure there remained no trace of previous experimenting. Then split the thing up into 100 GB of NTFS and all the rest (80ish GB) ext3.
3) Rebooted Ubuntu liveCD again, Gparted it again, everything looked perfect. Nothing had changed.

-----------------------

4) Installed Vista to what was /dev/sda1 (by label). I started sensing trouble when Vista's partition tool called the PATA drive "Drive 0" and the SATA drive "Drive 1". Hmm, exactly *who* was the boss drive again? :evil:
5) Fastforward until after Vista was installed. In the disk manager, it had picked the equivalent of /dev/sdb1 as System partition (thus making me unable to change driveletters and the like for it). It still said /dev/sda1 was the boot partition. I didn't like this, probably means that removing the PATA drive will permanently break Vista.
6) Rebooted into Ubuntu liveCD, and guess what when I run Gparted? The blasted thing switched the harddrives around! ](*,) Yep guys, that means the PATA was as of now /dev/sda and the SATA /dev/sdb. SATA still had the boot flag, PATA no boot flag.
7) So I went "whatever, as long as it works" and installed Ubuntu to the ext3 partition on the SATA drive, and used the settings described here.
8) Rebooted for the first time.. and I get my blasted error message!

-------------------

The plan now, is this:

1) Ubuntu liveCD + Gparted. Total wipe of the PATA again, including partition tables. Wipe all partitions on the SATA drive except for Documents (as I don't want to lose the stuff on there). Then shut down.
2) Unplug PATA drive. Boot Ubuntu liveCD, Gparted. Create the partitions again. Shut down.
3) Install Vista on /dev/sda1.
4) Reboot, plug in PATA drive. Boot Ubuntu liveCD, Gparted, create the NTFS and ext3 partitions again. Make sure the PATA is /dev/sdb still. Shut down.
5) Boot up Vista, let it drool all over it's new NTFS partition on the PATA.. reboot Vista, make sure the SATA is System drive.
6) Install Ubuntu like the last time but make sure this time SATA WILL be /dev/sda.
7) IF the thing refuses to boot again, the most likely reaction will be this: 

[img]http://www.kongtechnology.com/images/stupid-computer.jpg[/img]

;)

Does that all sound good? :p

---

### Post by falcon61102 on 2008-11-30
If you installed both system already, the only thing you need to do is reconfigure the MBR.  I suggest you download the Super GRUB Disk at: [www.supergrubdisk.org](www.supergrubdisk.org).  That will reconfigure your MBR and you should be good to go.

---

### Post by Lupusceleri on 2008-11-30
> **Lupusceleri said:**
> The plan now, is this:

1) Ubuntu liveCD + Gparted. Total wipe of the PATA again, including partition tables. Wipe all partitions on the SATA drive except for Documents (as I don't want to lose the stuff on there). Then shut down.
2) Unplug PATA drive. Boot Ubuntu liveCD, Gparted. Create the partitions again. Shut down.
3) Install Vista on /dev/sda1.
4) Reboot, plug in PATA drive. Boot Ubuntu liveCD, Gparted, create the NTFS and ext3 partitions again. Make sure the PATA is /dev/sdb still. Shut down.
5) Boot up Vista, let it drool all over it's new NTFS partition on the PATA.. reboot Vista, make sure the SATA is System drive.
6) Install Ubuntu like the last time but make sure this time SATA WILL be /dev/sda.

Did all this. Ended up with the SATA drive as /dev/sdb anyway, but whatever. Manually selected the bootloader to be installed to /dev/sdb. Bootloader for Ubuntu at least works flawlessly now.

In Vista, the blasted thing finally decided to pick C:\ as the system drive, boot drive, and all that stuffs.

However when trying to boot up Vista, it still says:

"Starting up ...

BOOTMGR is missing
Press Ctrl+Alt+Del to restart"

I think Ubuntu deleted Vista's bootloader. Supergrubdisks can't fix that I think, since it's a problem with Vista, not GRUB (GRUB just tells the system to use Vista's bootloader, so if that thing is missing or corrupt... you get the failures). Is there any way I can fix this without messing up GRUB yet again?

---

### Post by caljohnsmith on 2008-11-30
Are you getting the bootmgr missing error when you boot the Vista drive on start up, or when you boot Vista from Ubuntu's Grub menu? What might have happened is Vista stuck its boot files in one of your other NTFS/FAT partitions. How about posting:
```
sudo fdisk -lu
```
And for whichever is your Vista partition, for instance sda1, please post the output of:
```
sudo mkdir /mnt/Vista
sudo mount /dev/sda1 /mnt/Vista
ls -l /mnt/Vista
```
But replace sda1 above if Vista is on a different partition. Next, for whichever other FAT/NTFS partitions you have, for instance sdXY, post the output of:
```
sudo mkdir /mnt/sdXY
sudo mount /dev/sdXY /mnt/sdXY
ls -l /mnt/sdXY
```
That will hopefully clarify what your setup is like at present.

---

### Post by Lupusceleri on 2008-11-30
```
martijn@MartijnDesktop:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000775cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125837144    62918541    7  HPFS/NTFS
/dev/sda2       125837145   272639114    73400985    5  Extended
/dev/sda3       272639115   976768064   352064475    7  HPFS/NTFS
/dev/sda5       125837208   251674289    62918541   83  Linux
/dev/sda6       251674353   255867254     2096451   82  Linux swap / Solaris
/dev/sda7       255867318   272639114     8385898+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2c8d2c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   209712509   104856223+   7  HPFS/NTFS
/dev/sdb2       209712510   390716864    90502177+  83  Linux

---------------------

martijn@MartijnDesktop:~$ sudo mkdir /mnt/Vista
martijn@MartijnDesktop:~$ sudo mount /dev/sda1 /mnt/Vista
martijn@MartijnDesktop:~$ ls -l /mnt/Vista
total 2403284
drwxrwxrwx 1 root root       4096 2008-12-01 06:58 Boot
-rwxrwxrwx 1 root root     438840 2006-11-02 10:53 bootmgr
-rwxrwxrwx 1 root root       8192 2008-12-01 06:58 BOOTSECT.BAK
drwxrwxrwx 1 root root          0 2006-11-02 16:41 Documents and Settings
-rwxrwxrwx 1 root root 1073274880 2008-11-30 22:40 hiberfil.sys
-rwxrwxrwx 1 root root 1387200512 2008-11-30 22:40 pagefile.sys
drwxrwxrwx 1 root root       4096 2006-11-02 16:41 ProgramData
drwxrwxrwx 1 root root       4096 2006-11-02 16:42 Program Files
drwxrwxrwx 1 root root       4096 2006-11-02 16:33 Program Files (x86)
drwxrwxrwx 1 root root          0 2008-11-30 22:12 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-11-30 22:01 System Volume Information
drwxrwxrwx 1 root root       4096 2008-11-30 22:11 Users
drwxrwxrwx 1 root root      16384 2008-11-30 22:04 Windows

----------------------------

martijn@MartijnDesktop:~$ sudo mkdir /mnt/sda3
martijn@MartijnDesktop:~$ sudo mount /dev/sda3 /mnt/sda3
martijn@MartijnDesktop:~$ ls -l /mnt/sda3
total 4
drwxrwxrwx 1 root root 4096 2008-11-30 22:12 $RECYCLE.BIN
drwxrwxrwx 1 root root    0 2008-11-30 16:45 System Volume Information
drwxrwxrwx 1 root root    0 2008-11-30 16:10 Users

-----------------------------

martijn@MartijnDesktop:~$ sudo mkdir /mnt/sdb1
martijn@MartijnDesktop:~$ sudo mount /dev/sdb1 /mnt/sdb1
martijn@MartijnDesktop:~$ ls -l /mnt/sdb1
total 0
drwxrwxrwx 1 root root 0 2008-11-30 22:38 $RECYCLE.BIN
drwxrwxrwx 1 root root 0 2008-11-30 22:38 System Volume Information
```

Separated different command "groups" with ---------.

/dev/sda1 is Vista System.
/dev/sda3 is Documents.
/dev/sdb1 is Vista Programs.

---

### Post by caljohnsmith on 2008-11-30
OK, I think I understand now; when you get that "bootmgr missing" error, you get that when you boot Vista from the Grub menu? I think if you boot your Vista drive directly on start up, it will boot just fine. In other words, probably all you need to do is correct your Grub's menu.lst, because I think Grub is booting the wrong NTFS partition, resulting in the bootmgr missing error. How about opening your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your Vista entry with:
```
title	   Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Then reboot, and let me know exactly what happens when you boot Vista from the Grub menu. We can work from there. :)

---

### Post by Lupusceleri on 2008-11-30
My Vista entry already looked exactly like that, except that it had the line "savedefault" between the two lines that start with "map". So I removed that line, rebooted, selected Vista, got the EXACT same error message.

And yeah I did save the modified menu.lst.

Just highlighting some stuff again..

I installed Vista to what would be /dev/sda1. Vista, however, sees this as "Drive 1, partition 1" (which can I think be translated to /dev/sdb1), not as "Drive 0, partition 1" (which can be translated to /dev/sda1). Even after I at first had installed Vista to "Drive 0, partition 1" by unplugging the PATA drive. After plugging the PATA drive back in, Vista booted without any problems and it called the PATA drive "Drive 0" and the original "Drive 0" (SATA), "Drive 1". But as I said, this was no problem for Vista.

So I think that the bootloader from Vista is or was on what's now, in Linux, called EITHER /dev/sda1 OR /dev/sda.

I installed GRUB to what is now /dev/sda, but **when I created the installation, the current /dev/sda was called /dev/sdb and I installed the bootloader there.** For some reason the "names" /dev/sda and /dev/sdb were flipped around during the installation?!

Anyway is it possible that the Vista bootloader got overwritten by GRUB, rather than moved?

EDIT: Going to sleep now, and university right after, so I won't be able to give updates for some 18 hours.

---

### Post by caljohnsmith on 2008-11-30
OK, how about posting the output of:
```
sudo xxd  -l  2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
```
Whichever of those drives returns the value "eb48", that means that drive has Grub in the MBR. If the drive instead returns "33c0", that means it has a Windows MBR. I'm guessing that you must have Grub installed to the MBR of your Vista drive and are booting the Vista drive on start up; if that's true, that would explain why your current Vista entry doesn't work. Can you set your BIOS to boot the Ubuntu drive on start up? If so, how about doing the following to ensure Grub is properly installed to the MBR of the Ubuntu drive:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
And please post the output of the above commands. Reboot, set your BIOS to boot the sdb Ubuntu drive, and let me know how it goes.

---

### Post by Lupusceleri on 2008-12-01
Good evening again, guys. :)

On we go with the grand quest of obtaining a working dualboot.

As for the xxd command - you probably made an error there, as I got this output:

```
martijn@MartijnDesktop:~$ sudo xxd -1 2 -p /dev/sda
[sudo] password for martijn: 
Usage:
       xxd [options] [infile [outfile]]
    or
       xxd -r [-s [-]offset] [-c cols] [-ps] [infile [outfile]]
Options:
    -a          toggle autoskip: A single '*' replaces nul-lines. Default off.
    -b          binary digit dump (incompatible with -p,-i,-r). Default hex.
    -c cols     format <cols> octets per line. Default 16 (-i: 12, -ps: 30).
    -E          show characters in EBCDIC. Default ASCII.
    -g          number of octets per group in normal output. Default 2.
    -h          print this summary.
    -i          output in C include file style.
    -l len      stop after <len> octets.
    -ps         output in postscript plain hexdump style.
    -r          reverse operation: convert (or patch) hexdump into binary.
    -r -s off   revert with <off> added to file positions found in hexdump.
    -s [+][-]seek  start at <seek> bytes abs. (or +: rel.) infile offset.
    -u          use upper case hex letters.
    -v          show version: "xxd V1.10 27oct98 by Juergen Weigert".
```

This is the grub stuffs:

```
martijn@MartijnDesktop:~$ sudo grub
[sudo] password for martijn: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd1)       
setup (hd1)

Error 17: Cannot mount selected partition
grub> quit
quit
martijn@MartijnDesktop:~$ 
```

Last but not least it looks like I found a "backup" of my old Vista bootloader: it was on my USB drive, and is from a few days ago (fresh Vista/XP install) when I had not bought the new SATA drive yet. I made the backup using my flashdrive-xubuntu, so it shouldn't have skipped any files that Vista hid from me. Screenie included.

In the boot.BAK file is something remotely readable:

```
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
<insert useless outdated stuff here>
```

Is it possible to run BCDEDIT from Ubuntu maybe to repair the Vista MBR? :)

---

### Post by caljohnsmith on 2008-12-01
Just thought I would first mention that when running those xxd commands, the "-l" is a lowercase L, not a one; I think that's why you got those errors. Also, I was misunderstanding your setup and thought Ubuntu was on sdb, which is obviously wrong. Anyway, that would explain why that previous Vista entry I gave didn't work. How about instead trying:
```

title Windows Vista
root (hd0,0)
chainloader +1
```
Reboot, and let me know exactly what happens when you select it from the Grub menu. If that doesn't work, then please post the output of the xxd commands I gave previously. :)

---

### Post by Lupusceleri on 2008-12-01
IT'S ALIVE! :biggrin:

Thanks a load, Vista finally boots again! ;)

Now the only things left to do, are pulling a registry hack on Vista to move the Users and ProgramData folders to a different drive/partition. And installing some ext2 drivers for Windows so I can access the UbuntuHome partition. :)

[http://fs-driver.org/](http://fs-driver.org/) is the "best" driver, IE it integrates into the windows shell and you don't need to use any special browsers, right?

---

### Post by caljohnsmith on 2008-12-01
Yes, using that Ext2 IFS program (fs-driver.org) should work OK in Windows, but only with your ext2 partition; unfortunately you will run into a problem if you try and mount any Intrepid ext3 partitions with the Ext2 IFS program, because Intrepid now uses a 256 byte inode size for its ext3 file system, whereas in the past it's been 128 bytes. From their project page they say:
> Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.
I think a better alternative might be:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

I use that program, and their project page says:
> flexible-inode-size supported.
So even though I haven't gotten around to testing ext2fsd with my Intrepid partitions, I think it should work OK. Anyway, good luck and let me know how it goes. :)

---

### Post by Lupusceleri on 2008-12-01
Ok, that's great, I will just use the ext2 driver then as I don't want my windows flooded with partitions/harddrives. The only thing I might have to access is /home, not like I have any use at all for opening Linux programs or systemfiles on Vista.

Besides, as far as I could read on the intarwebs Ext3 partitions go nuts if you mount them as ext2 and write to them? IE they're in fact read only?

---

### Post by caljohnsmith on 2008-12-01
> **Lupusceleri said:**
> 
Besides, as far as I could read on the intarwebs Ext3 partitions go nuts if you mount them as ext2 and write to them? IE they're in fact read only?
I don't know off-hand, because I've never tried to mount an ext3 file system as ext2. You're probably right though that you can at least read from them. That's just a guess though, because I don't want to try it out and find out the hard way. :)

---

### Post by Lupusceleri on 2008-12-06
> **caljohnsmith said:**
> then you can create a symbolic link to your "Documents" folder or whichever folder you want in Vista's partition. It is as simple as something like:
```
sudo ln -s /path_to_Vistas_Documents_Folder /home/<username>/.
```
That would create a Documents directory in your home folder that is linked your Vista's Documents folder, so they are the same thing. Let me know how your installation goes or if you have more questions. :)

Help!

It totally deleted the things in my Documents folder.. o.O

I tried making the virtual link thing, but I figured it was created on the wrong spot (it was a shortcut inside /home/martijn/Documents and I thought it looked silly), so I did ctrl-x and tried to ctrl-v it back in /home/martijn. Then it error'd some, and afterwards no contents show up in that folder at all in Vista nor Ubuntu.

Luckily I have a very recent backup of my stuff, but still.. how do you remove such a virtual link without making your documents explode? Or how do you move it elsewhere?

---

### Post by Lupusceleri on 2008-12-06
Alright, now the initial zomg panic reaction is over it works again.

Made some nice load of virtual links, it looks cool. :)

The only issue I have left, is that I can't seem to find where to auto-mount my Documents ntfs-drive on bootup. For now I just click Places-->Documents and then it mounts and everything is fine and dandy. I know it's something with /etc/fstab, but modifying anything in there is.. scary.

Anyhow I'll meddle around some using bodhi.zazens guide.

EDIT: Mission accomplished, that was way too easy for something looking that scary. ;p This guide: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) is win.

---

