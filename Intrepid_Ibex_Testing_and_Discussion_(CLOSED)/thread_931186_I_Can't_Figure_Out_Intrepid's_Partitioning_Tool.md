---
title: "I Can't Figure Out Intrepid's Partitioning Tool"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Therion on 2008-09-27
Feeling a little sheepish about this, but I can't figure out Intrepid's partitioning tool.  It's not like I've never done this before, and I'm sure it's something stupid I'm just not understanding, but searches have proven fruitless.

The issue is this: I'm currently dual-booting with Hardy and XP (single drive) and I don't want to wipe out the XP partition.  Yes, I know I could reinstall XP, reformatting and repartitioning the drive in the process, and THEN install Intrepid, but that's my absolute last option.  I just want to install Intrepid alongside my XP like I have Hardy now.  

That can't be asking too much can it?  I just can't seem to figure out the partitioning tool during the install.  I'm installing to a 150GB SATA drive.  I can set up my "swap" partition (512MB) but that's as far as I can get.  As soon as I try to set up partitions for "/" and "Home"; it's a no-go.  I'm totally confused on how to set up the partitions.

Could someone walk me through the steps, please, because I'm totally confused...

Thanks in advance.

---

### Post by blakamin on 2008-09-27
How many partitions do you already have on that drive?

---

### Post by Therion on 2008-09-27
> **blakamin said:**
> How many partitions do you already have on that drive?
The drive is "split" equally between Ubuntu and Windows with each having about 72-73 GB.  

The Linux partitions are the standard Swap, / and Home.

---

### Post by Gina on 2008-09-27
Ah.. so you have 4 partitions.  If these are all primary partitions you will not be able to make any more.  Partition numbers are limited to 4 primary or 3 primary and an extended partition that may then by split into any number of logical partitions.  This is a feature of the PC hard drive system - it's origin goes way back!  And it's a right pain and quite ridiculous IMO.  But it seems we're stuck with it.

If your partitions are all primary you will have to delete one, then make a new extended partition in the space freed up.  Then assign logical partitions within that as required.  You will probably want to resize and maybe move partitions to provide the layout you want.  This may be done in GParted without losing any data (though making a backup is strongly advised).

Hope that helps.

---

### Post by Therion on 2008-09-27
> **Gina said:**
> Ah.. so you have 4 partitions.  If these are all primary partitions you will not be able to make any more.
Thank you for your response.

I'm aware of the four-partitions per volume issue and what not, but the thing is, I don't want to ADD an Intrepid install, I want to over-write my existing Hardy install *with* Intrepid and leave my Windows XP install (on it's separate partition) unchanged.

When I get to the partitioning tool in Intrepid, I choose the "Manual" partitioning option but the only choices I have are to "Create New Partition Table" (which would wipe out ALL existing partitions) or "Undo Changes to Partitions".

I don't understand why the Partitioning Tool isn't seeing the NTFS/WinXP partition and letting me leave it alone and install Intrepid on the *other* partition.

---

### Post by Gina on 2008-09-27
Ah, I see.  I though you might already know that but spelt it out just in case you didn't.  

I don't know why you're not getting the usual options in the manual partitioning mode.  I have installed dozens of times doing exactly what you want with various versions of Ubuntu including Intrepid.  Last time was with Alpha 6.  I generally use the Alternate CD but have used the Live CD as well.  

All I can think of is that you have a fault in your partition table.  I suggest running GParted - either from your Hardy system or using the Live CD of Intrepid - and seeing if you get any errors.  You certainly should see your XP partition as well as all the Ubuntu ones.

You probably already know that when installing Ubuntu using the Manual partitioning option, you should get a list of ALL your partitions (inc XP) and then choose to edit the ones to use for the new install ie. / and /home - the SWAP being recognised and marked for formatting.

---

### Post by ThrobbingBrain66 on 2008-09-27
All you should have to do is click the checkbox to reformat Hardy's / partition and Intrepid will install to that partition.  Leaving the other partitions alone is basically telling the installer to ignore them.

---

### Post by Therion on 2008-09-27
> **Gina said:**
> Ah, I see.  I though you might already know that but spelt it out just in case you didn't.
Roger that.  :)  

> **Gina said:**
> I don't know why you're not getting the usual options in the manual partitioning mode.  I have installed dozens of times doing exactly what you want with various versions of Ubuntu including Intrepid.  Last time was with Alpha 6.  I generally use the Alternate CD but have used the Live CD as well.  

All I can think of is that you have a fault in your partition table.  I suggest running GParted - either from your Hardy system or using the Live CD of Intrepid - and seeing if you get any errors.  You certainly should see your XP partition as well as all the Ubuntu ones.

You probably already know that when installing Ubuntu using the Manual partitioning option, you should get a list of ALL your partitions (inc XP) and then choose to edit the ones to use for the new install ie. / and /home - the SWAP being recognised and marked for formatting.
Yeah, it's not at all what I'm used to seeing.  Thought about gPartEd but then decided against it.

> **ThrobbingBrain66 said:**
> All you should have to do is click the checkbox to reformat Hardy's / partition and Intrepid will install to that partition.  Leaving the other partitions alone is basically telling the installer to ignore them.
Hmmmm... Okay, I guess I'm willing to try that.  Dear gawd in heaven though if I lose my Windows partition (even with my SlipStreamed XP Install disc and all my backups) it' going to be hell on earth.  IMO there aren't too many "time sucks" that suck WORSE than doing a fresh install of Windows... Unless it's reinstalling Oblivion.

So all I do then is "tick" the little box to format "/" and Intrepid will do the rest, eh?

Thanks for the input...  I guess I'll give this a go.



**EDIT:**
Well it's a moot point now because the installer won't format the partition... Period.  It just flat out fails saying it can't write the ext3 partition to the drive and kicks me back to picking my time-zone.

I'll just try again when Intrepid goes final.

---

### Post by Gina on 2008-09-27
It sounds even more like a faulty partition table now.  But you can check it with GParted - you don't need to actually tell it to do anything - just run it to view your partitions.  If your partition table is faulty, the [SystemRestoreCD]("http://www.sysresccd.org/Main_Page") may be able to recover it.  I had that trouble once and fixed it that way.  I thought I'd lost everything - XP wouldn't boot.

---

### Post by nanog on 2008-09-27
Bootitng has never failed me when I've had corrupt partition tables. They offer a fully functional trialware version.

---

### Post by caljohnsmith on 2008-09-27
I would recommend running "testdisk" on your HDD at this point to see if you have a corrupt partition table. You can run testdisk either from the SystemRestoreCD that Gina gave a link to, or if you have internet access from your Ubuntu Live CD, you can just install it there with:
```
sudo apt-get testdisk
```
Make sure you have all your repositories enabled. Then to run testdisk:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Also, please post the output of:
```
sudo fdisk -l
sudo fdisk -lu
```
I know they are similar, but it will save me having to do any math to convert between cylinders and sectors when checking your partition table. :)

---

### Post by Therion on 2008-09-27
> **caljohnsmith said:**
> I would recommend running "testdisk" on your HDD at this point to see if you have a corrupt partition table. You can run testdisk either from the SystemRestoreCD that Gina gave a link to, or if you have internet access from your Ubuntu Live CD, you can just install it there with:
```
sudo apt-get testdisk
```
Make sure you have all your repositories enabled. Then to run testdisk:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Also, please post the output of:
```
sudo fdisk -l
sudo fdisk -lu
```
I know they are similar, but it will save me having to do any math to convert between cylinders and sectors when checking your partition table. :)
Hmmmm... Okay.  I'll give this go.  I'm running a LiveCD right now, but I guess I should mention that both Ubuntu and Windows XP are both booting fine.  Still back in a few with the results!  Thanks everyone...

---

### Post by Therion on 2008-09-27
**Before test starts: **```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 150 GB / 139 GiB - CHS 18241 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  9050 254 63  145404252 [Raptor]
 2 P Linux Swap            9051   0  1  9112 254 63     996030
 3 P Linux                 9113   0  1 18240 254 63  146641320

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition
```

**Test Complete:**```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 150 GB / 139 GiB - CHS 18241 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  9050 254 63  145404252 [Raptor]
D HPFS - NTFS              0   1  1 18239 254 63  293025537 [Raptor]
D HPFS - NTFS              0   1 12  9050 254 63  145404241
D Linux Swap            9051   0  1  9112 254 63     996030
D Linux                 9051   1  1 17860 254 63  141532587
D Linux                 9113   0  1 18240 254 63  146641320
D Linux Swap           17861   1  1 17922 254 63     995967

Structure: Ok.  

Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 74 GB / 69 GiB
```

**Output from sudo fdisk -l:**```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12b112b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9051    72702126    7  HPFS/NTFS
/dev/sda2            9052        9113      498015   82  Linux swap / Solaris
/dev/sda3            9114       18241    73320660   83  Linux
ubuntu@ubuntu:~$ 
```

**Output from sudo fdisk -lu:**```
[/ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12b112b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   145404314    72702126    7  HPFS/NTFS
/dev/sda2       145404315   146400344      498015   82  Linux swap / Solaris
/dev/sda3       146400345   293041664    73320660   83  Linux
ubuntu@ubuntu:~$ 
```

Hope I did all that right!

Thanks for all the help, by the way... Mucho appreciate it!

Going to reboot, and check both my Ubuntu and WinXP installs.  Back in a few...

---

### Post by ronacc on 2008-09-27
if you have a working hardy that you want to replace with intrepid you can do this . gksudo gedit    then open /etc/apt/sources.list  and search and replace hardy with intrepid , save it and close gedit then in a terminal sudo apt-get update then when that finishes sudo apt-get dist-upgrade , that will bring you to an uptodate intrepid installation ( assuming nothing screws up):) PS go watch tv , it'll take awhile .

---

### Post by Therion on 2008-09-27
> **ronacc said:**
> if you have a working hardy that you want to replace with intrepid you can do this . gksudo gedit    then open /etc/apt/sources.list  and search and replace hardy with intrepid , save it and close gedit then in a terminal sudo apt-get update then when that finishes sudo apt-get dist-upgrade , that will bring you to an uptodate intrepid installation ( assuming nothing screws up):) PS go watch tv , it'll take awhile .
Thank you... I think I'll try that.  

Both my Hardy install and my XP install are running fine, so yeah, that's a very elegant solution I should have thought of.

---

### Post by Therion on 2008-09-27
Okay well that didn't do much of squat, actually... I'm not sure but I think I'm running some kind of odd mix now of Intrepid AND Hardy...

sudo apt-get dist-upgrade yields the following:```
baphomet@ObeliskII:~$ sudo apt-get dist-upgrade
[sudo] password for baphomet:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-do gtk2-engines-murrine
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
baphomet@ObeliskII:~$
```

Sighhhhh...

---

### Post by caljohnsmith on 2008-09-27
Therion, your testdisk/fdisk results look just fine, so your partition table should be OK. Before you install Intrepid, can you run gparted:
```
gksudo gparted
```
And format your Hardy partition sda3 to ext3 beforehand? Would that be enough to allow the Intrepid installer to continue?

---

### Post by Therion on 2008-09-27
> **caljohnsmith said:**
> Therion, your testdisk/fdisk results look just fine, so your partition table should be OK. Before you install Intrepid, can you run gparted:
```
gksudo gparted
```
And format your Hardy partition sda3 to ext3 beforehand? Would that be enough to allow the Intrepid installer to continue?
I'm must be missing something because I don't think I can format the partition while the volume is mounted, can I?  I mean, it sounds like I would be formatting the partition I'm currently using (I'm running my live-install of Ubuntu now).  

Do you mean use the gParted LiveCD to format the partition?  Boot from a LiveCD and then use gParted from the Terminal?!

What I reeeeally don't understand is what happened to the simple little graphical partition tool that came with Hardy.  WTF?  It was fine. GLORIOUS even...

---

### Post by caljohnsmith on 2008-09-27
> **Therion said:**
> I'm must be missing something because I don't think I can format the partition while the volume is mounted, can I?  I mean, it sounds like I would be formatting the partition I'm currently using (I'm running my live-install of Ubuntu now).  

Do you mean use the gParted LiveCD to format the partition?  Boot from a LiveCD and then use gParted from the Terminal?!

What I reeeeally don't understand is what happened to the simple little graphical partition tool that came with Hardy.  ~What the heck~?  It was fine. GLORIOUS even...
Maybe I'm the one who's missing something here :); how exactly are you trying to install Intrepid? I was under the impression you had an Intrepid Live CD and were doing it from there, but maybe I'm totally wrong about that? Are you trying to do this while in your current HDD's Hardy install?

---

### Post by Therion on 2008-09-27
> **caljohnsmith said:**
> Maybe I'm the one who's missing something here :); how exactly are you trying to install Intrepid? I was under the impression you had an Intrepid Live CD and were doing it from there, but maybe I'm totally wrong about that? Are you trying to do this while in your current HDD's Hardy install?
Sorry, things ARE getting a bit twisted here.

I do have an Intrepid LiveCD.  I have been trying to install from it.  Now I think I'm with you (sorry, my mind is a little torqued at the moment)...

I think what you're saying (quite clearly, actually) is...

Boot from the Intrepid LiveCD
Run gParted and (re)format the "/" partition.
Try to install from the LiveCD.

Yes?

---

### Post by caljohnsmith on 2008-09-27
> **Therion said:**
> Sorry, things ARE getting a bit twisted here.

I do have an Intrepid LiveCD.  I have been trying to install from it.  Now I think I'm with you (sorry, my mind is a little torqued at the moment)...

I think what you're saying (quite clearly, actually) is...

Boot from the Intrepid LiveCD
Run gParted and (re)format the "/" partition.
Try to do the install from the LiveCD.

Yes?
Yes, exactly, and just make sure you don't have any partitions on your sda disk mounted. :)

---

### Post by Therion on 2008-09-27
Tried that.  Saw both partitions... Deleted and reformatted /sda as ext3 in gParted from within the Intrepid LiveCD.

Started install from LiveCD.

**Error: ***"The ext3 partition could not be created."*

Thank you VERY much for your help, but I'm throwing in the towel.  It's just not worth the effort.
Ultimate is running really well and I'm just going to stick with it for now.  

Thank you again.

---

### Post by caljohnsmith on 2008-09-27
> **Therion said:**
> Tried that.  Saw both partitions... Deleted and reformatted /sda as ext3 in gParted from within the Intrepid LiveCD.

Started install from LiveCD.

**Error: ***"The ext3 partition could not be created."*

Thank you VERY much for your help, but I'm throwing in the towel.  It's just not worth the effort.
Ultimate is running really well and I'm just going to stick with it for now.  

Thank you again.
Yes, I can't blame you for giving up on it at this point. That sure sounds like a bug though, so if you might be willing to take the time, it would help everyone if you could report it at bugs.launchpad.net. I know you're understandably frustrated at this point, but it would help everyone if the developers are alerted about this bug so it might be fixed before the release. :)

---

### Post by nanog on 2008-09-27
Gparted/qtparted fail on corrupt partitions that are created during failed attempts to resize with ubiquity. Remaking/resizing partitions with bootitng made them installable. 

[http://www.terabyteunlimited.com/downloads-bootit-next-generation.htm](http://www.terabyteunlimited.com/downloads-bootit-next-generation.htm)
[http://www.terabyteunlimited.com/downloads/bootitng.zip](http://www.terabyteunlimited.com/downloads/bootitng.zip)

---

### Post by bwallum on 2008-09-27
Hi, I've read the thread and you must be tearing your hair out. I moved from Hardy to Intrepid with```
sudo update-manager -d
```. When the update manager comes up you get the option to upgrade. Just press the button and go away for a few hours. Towards the end of downloading the upgrade files you have to interact with some software acceptance conditions. If your Ubuntu is still working give it a try. Use ```
sudo apt-get autoremove
```to tidy up.

---

### Post by Therion on 2008-09-27
> **bwallum said:**
> Hi, I've read the thread and you must be tearing your hair out. I moved from Hardy to Intrepid with```
sudo update-manager -d
```. When the update manager comes up you get the option to upgrade. Just press the button and go away for a few hours. Towards the end of downloading the upgrade files you have to interact with some software acceptance conditions. If your Ubuntu is still working give it a try. Use ```
sudo apt-get autoremove
```to tidy up.
Thank gawd for beer or I'd be bald by now my friend.

Trying your update suggestion.

OMG...  It's working.  

Well it's doing something anyway... Downloading 952 updates/~1,000 packages.  

It's complaining "Can not calculate the upgrade" and that it can only do a "Partial Upgrade".

Of course my sources.lst is screwy as well now, so frankly I have no idea what I'll wind up with when this is all done.  

Some kind of Frankendistro no doubt.


**EDIT: ** Well I'm in up to my armpits now... Removing/Installing Software stage.

---

### Post by ronacc on 2008-09-27
did you change ALL instances of hardy to intrepid in your sources.list ?

---

### Post by Therion on 2008-09-28
Long story short... I'm back now after doing a fresh format and install.

My system got so tooooootally borked I just pulled out the big guns and reinstalled Hardy from scratch.  

No big loss, mind you; I'm good about doing my backups and have an external drive and so forth.  Just some frustration and time lost.  

Lesson learned: Wait for the final release.  

Thanks for all the well considered input and suggestions and so forth.  Just one of things, I think.  I'm just not ready for Intrepid, or it's not ready for me.  Not yet anyway.


Cheers, all!

---

### Post by Gina on 2008-09-28
You gave it a good go :)  Testing development systems is not for the faint-hearted and you do need experience of problem solving.

---

### Post by Ususbuntung on 2008-10-15
Is it possible that this has something to do with the Partition Editor version of Intrepid LiveCD (beta version)?
Using Intrepid LiveCD, I have only one big grey square marked unallocated on my Thinkpad X31, while actually I have XP and a certain Linux distro that I want to replace with Intrepid.
While using Hardy LiveCD, I get everything it should be!
As the thread starter suggested, I will wait for final release!

---

