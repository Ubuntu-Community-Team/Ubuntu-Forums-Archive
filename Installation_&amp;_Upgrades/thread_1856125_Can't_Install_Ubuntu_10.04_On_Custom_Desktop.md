---
title: "Can't Install Ubuntu 10.04 On Custom Desktop"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by bctis on 2011-10-07
Hi, I am currently trying to install Ubuntu 10.04 LTS after deleting 11.04 which I installed using Wubi. The CD starts up ok and I get to the part where I select language and keyboard layout etc. But when I come to the part where I have to select partition where I want to install the Ubuntu it says that I have no operating system on my machine even know I currently have Windows 7 installed. Also when I try manually choosing partition all buttons and everything on Installation screen are blank and Ubuntu doesn't see that I have a HardDrive at all. I specifically created a partition in windows 7 for Ubuntu and still nothings shows up in installation screen. Forum your help would be greatly appreciated.

Thanks in Advance.

---

### Post by MG&amp;TL on 2011-10-07
What sort of hard disk have you got? It's possible that the kernel/gparted can't see the HDD.

---

### Post by bctis on 2011-10-07
I have WD Caviar Black 1TB harddisk but I dont think it is because of harddisk I had similar issue on my Acer laptop, I ended up overwriting ubuntu over windows but I didnt realize what I did until the installation was over :(

---

### Post by MG&amp;TL on 2011-10-07
I meant what sort of connector/storage medium it used.

You could always try cloning your current HDD, ([http://clonezilla.org/]("http://clonezilla.org/")) then doing what you can with the Ubuntu installer, and if it all goes horribly wrong, reinstall and do it again.

---

### Post by Hakunka-Matata on 2011-10-07
Hi, and Welcome.

Please boot into the Ubuntu liveCD/USB, don't install, just select "Try without installing".  
Run these commands in a Terminal window and post the results.  
```
sudo fdisk -l && sudo sfdisk -luS
```You may have forced windows to convert your hard disk partitions to Dynamic by creating that partition for ubuntu.

---

### Post by bctis on 2011-10-08
Thank You For your reply, I ran the commands you told me in the exact same fashion and nothing happened. I entered the commands in terminal and pressed enter and nothing happened.

---

### Post by MG&amp;TL on 2011-10-08
That's not good. Returned to a prompt like this?

```
username@username-desktop~/$:_
```That's not good. Ubuntu cannot read your disks.

---

### Post by MG&amp;TL on 2011-10-08
All due respect, are you sure that your drives are plugged in? I haven't heard of linux not liing a hard disk yet...file a bug.

---

### Post by bctis on 2011-10-08
What do you mean by plugged in mate? I have one harddrive and since I am typing this message and can Actually access my windows7 operating system then I am sure it is plugged in. So what I am supposed to do now if it cant read my disk?

---

### Post by MG&amp;TL on 2011-10-08
Yep. cool. I was just checking! :)

I will google your hard drive, but if it cannot recognize it, I am not sure that there is much you can do.

---

### Post by westie457 on 2011-10-08
While you are in Windows could you open Windows MMC and go to storage. Take a screen shot of your current partitions and post it back here please so we can see what the problem is.

Thank you.

---

### Post by MG&amp;TL on 2011-10-08
I have googled your disk, but it would seem that the WD disks seem to be flaky when installing an OS. IDK why.

If you still want to run Ubuntu reliably, and none of these other suggestions work, I would suggest that you:

a) run Wubi
b) run Virtualbox.

I can't really give anymore suggestions- I learned the little I do know from recovering a broken HDD.

---

### Post by bctis on 2011-10-08
Thx mate :) I googled it as well and nothing special popped up, I checked for its drivers as well just in case, but this problem is really strange because I had exact same problem on my Acer Aspire laptop, and ended up just deleting windows. I guess if nothing works I will use Wubi again. BTW here is the screenshot u asked for [http://postimage.org/image/3dd2s8x0/](http://postimage.org/image/3dd2s8x0/)

Thx in Advance []("http://postimage.org/image/3dd2s8x0/")

---

### Post by westie457 on 2011-10-08
The hard drive partitioning is okay. The disk and partitions are all Basic. One suggestion is while in Windows MMC delete the Ubuntu/E: partition leaving it as a blank space then try restarting the installer to find out if it sees the unformatted partition. If it does carry on with the install, if not you have not lost anything and we will have to look for another solution.

Hope this helps.

---

### Post by bctis on 2011-10-08
Does it make any difference if I install Ubuntu using Wubi? Or is there any way to install ubuntu 10.04 LTS using WUBI?

---

### Post by westie457 on 2011-10-08
Just personal preference really. A WUBI install is really for testing as in using a LiveCD and is limited to a maximum size of 30GB. 10.04 should install via WUBI with no problems, also it should install to its own partitions with no problems.

A quick question do you have any SATA3 ports on your motherboard and if so is the hard drive connected to one of them?

The reason I suggested to leave the partition unformatted is to help the installer to try to find the hard drive or at least part of it.

---

### Post by westie457 on 2011-10-08
When you removed Natty did you just delete it or did you uninstall using Windows Control Panel just like any other program?

---

### Post by Hakunka-Matata on 2011-10-08
You've created a ntfs partition for ubuntu with windows Disk Management evidently.  Delete that partition and try installing.  Just leave the empty space, ubuntu install procedure should find it.

---

### Post by bctis on 2011-10-08
Ok, When I uninstalled Natty I used Control Panel to do so and then I formated my Ubuntu drive, and here is the screenshot of what I did right now, I left 100GB unallocated.  [[img=http://s4.postimage.org/4xgdyzvo/Screenshot_21h_20m_31s.jpg]]("http://postimage.org/image/4xgdyzvo/")

So I did what you suggested leaving 100GB space unallocated and ubuntu install procedure did not find it, please Help and keep in mind that the exact same thing happened on my Acer Aspire laptop, so the issue may not lay in harddisk itself.

My motherboard is AsusRampage Formula 3 and yes it does have Sata3 ports but I am not sure if the Harddisk is connected to them or not. 

How Can I install Ubuntu 10.04 Using Wubi? Because when I use wubi it automatically installs Nattys Ubuntu 64amd?

---

### Post by MG&amp;TL on 2011-10-08
Wubi is not a true OS; it's an ubuntu install 'tacked on to windows install; think of it as a several-GB program.

To get wubi, get an iso, extract it, and double-click on wubi.exe

---

### Post by Shazaam on 2011-10-08
Unplug your pendrive and try the Ubuntu livecd installer again. Just a shot in the dark...

---

### Post by MAFoElffen on 2011-10-08
> **MG&TL said:**
> Wubi is not a true OS; it's an ubuntu install 'tacked on to windows install; think of it as a several-GB program.

To get wubi, get an iso, extract it, and double-click on wubi.exe
Sidenote:

Ouch!!!  My personal preference is usually always a traditional Ubuntu (it's own partition) install.  But the Wubi explaination here is a little out-there....

Clarification:
"Wubi" is a Windows Installer that installs the "real" Ubuntu OS within a disk image file that resides within the Windows host partition.  Having been installed from a Windows installer, it can be unistalled from the program manager of Windows.

Wubi can be installed directly booting from the LiveCD... That wubi install can later be xported to an external partition or disk... Which will then be like a traditional install.

On this OP... I would pursue finding his "disk not shown problem."  That's going to affect him whatever Ubuntu Installation he ends with.

To the OP- 
 - Does the disk show up if you start from a LiveCD > use Try > System > Administration > Disk Utility ?
 - Does the disk show up from the partitioner on an Ubuntu Alternate Install disk?
 - Since you clearly did not finish an Install, did you execute the previous linux command mentioned (below) [FONT=monospace]
[/FONT]```
sudo fdisk -l && sudo sfdisk -luS

```from a terminal session running from the Ubuntu LiveCD? If not please do and post.

---

### Post by MG&amp;TL on 2011-10-08
> **MAFoElffen said:**
> Sidenote:

Ouch!!!  My personal preference is usually always a traditional Ubuntu (it's own partition) install.  But the Wubi explaination here is a little out-there....

Clarification:
"Wubi" is a Windows Installer that installs the "real" Ubuntu OS within a disk image file that resides within the Windows host partition.  Having been installed from a Windows installer, it can be unistalled from the program manager of Windows.



Thank you. What I said was how I had it explained to me. :)

So would I (disk install), but his HDD is giving problems, so I suggested an alternative.

---

### Post by MAFoElffen on 2011-10-08
> **MG&TL said:**
> So would I (disk install), but his HDD is giving problems, so I suggested an alternative.
The suggestions were there...

Boot from a LiveCD and use it as a Linux diagnostics tool.  If it can't be seen by a Linux session, there's problems somewhere.  

2 people gave the suggestion of removing the present NTFS Ubuntu partition and leaving the then unused space.  I'm +1 on that.  While he's in the Windows Disk Manager, it he could move the Primary Windows back one sector, it will deter some problems later with some multi-boot systems...

I gave some suggestions on my last post and requested some info that the OP should be able to get.  I see he is using a IveCD on USB... If he can boot to try a session he can confirm that it runs on his PC.  From that session he can go to places and try to mount his hard disk...

I have about 150 drives here on 12 systems (sytem, eSATA, NAT and RAID).  I also work in a Computer Recylers, were we have to test drives, for sale and for the resurrection of systems (mostly as Linux.) I don't usually have dirve problems with Western Digital's not booting Linux or Unix.  Now, some models of Seagates are another story.

What I'm saying is, by his screen shot's, the OP is running Win7 --> I assume that his hardware is not that old.

One thing none asked was it this PC has a functioning CD/DVD drive...   Another thing would be to chack the BIOS and see if the HDD shows up  correctly in the CMOS.  If the drive itype is SATA, in the BIOS check if  the SATA compatibility type is set to "2.0" and not to "3.0". Linux  kernel doesn't support native SATA 3.0 yet.

That BIOS tidbit is a sort of a Ubuntu LivrCD / Installer / Disk Partitioner kind of thing.  (Affects hardware RAID also.) If the BIOS settings are not what is "there", then the disk partitioner wigs out.  I assume it's like if BIOS doesn't see it, Linux follows suit.  Same will happen if you try to find a drive (clean/blank)  with Linux when the drive does not have any kind of a partition table...

One thing he might do is to download the "Ultimate Boot Disk" and the "GParted LiveCD" ISO's.  GParted is also on the UBCD, but is easier for a new user to use the standalone...  Anyways- from the UBCD, go to the WD utitly pragram and test the disk to ensure it is functioninfg without errors.  

From the GPrarted Livecd, see if you can see the partitions.  That disk runs Debian... That would confirm that the disk can be seen or not from Linux (and from Debian Linux!) from the full version of GParted.

I have some that I have to just go into the BIOS, Look at the drive settings, then save/exit Bios settings > boot LivecD > Install > and everything is then fine with it. Not the norm, but does happen.

Right now, we need some info and we need to guide him to get it.  Its probably something simple.  We just don't see it yet until we can get that "right" piece of info to narrow it down.

---

### Post by bctis on 2011-10-09
MAFoElffen thank you for your detailed reply, it will take me some time to do everything you said but I will be done today and post the results on forum, Somebody told to remove Pendrive before installing the funny thing is Linux Installation actually recognizes my pendrive as a partition and I can Install Ubuntu on it but when I remove my pendrive it doesnt see any other disk. Another question is, wont I lose data transfer speed if I switch in BIOS from SATA3 to SATA2?

---

### Post by bctis on 2011-10-09
MAFoElffen thank you for your detailed reply, it will take me some time to do everything you said but I will be done today and post the results on forum, Somebody told to remove Pendrive before installing the funny thing is Linux Installation actually recognizes my pendrive as a partition and I can Install Ubuntu on it but when I remove my pendrive it doesnt see any other disk. Another question is, wont I lose data transfer speed if I switch in BIOS from SATA3 to SATA2?

I also executed these 
sudo fdisk -l && sudo sfdisk -luS commands when I selected Try Ubuntu from Ubuntu CD and nothing happened, nothing at all.

---

### Post by westie457 on 2011-10-09
ATM as things stand Ubuntu cannot read drives on a SATA 3 port, it is not supported. This might change with the release of 11.10. So it is a trade off lose some transfer speed when moving files or have a working system.

IMHO it would be better to have a working system so connect to a SATA 2 port. The drop in transfer speed will probably not be that noticeable.

---

