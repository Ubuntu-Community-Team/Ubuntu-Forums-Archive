---
title: "Ubuntu 14.04 installer doesn't detect my partitions"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by Roland_Batovski on 2014-07-12
I'm running Win7 64-bit and I'm trying to dual-boot Ubuntu 14.04. However, when I go into the Ubuntu installer, it doesn't display any of my partitions. I would like to mention that this is my second installation of Win7 on my laptop. After reading a bunch of forums, it seems like this is a very common problem and it is very likely that it is due to a damaged partition table.
Is there any way to fix my partition table from Windows? I tried booting into Ubuntu Live but for some reason my laptop's keyboard doesn't work at all (so I can't use the terminal) and the mouse & touchpad only work for a short period of time, then stop working. All the solutions I've seen so far involved running Fixparts from Ubuntu Live (which is something I can't do, given the circumstances). I ran Fixparts from Windows on my 0: drive, pressed "p", and got this:
[http://gyazo.com/434a6a26aef9a346aa59d0154a004fc1](http://gyazo.com/434a6a26aef9a346aa59d0154a004fc1)
I then pressed "w", as instructed in the tutorial, and the cmd closed immediately. I am unsure whether it did anything or not, but as it was closing I managed to catch a glimpse of the word "successfully", so I'm hoping something happened. Unfortunately, this didn't solve the problem and the Ubuntu installer still doesn't detect my partitions.

This is the result of running : "diskpart list volume" in Windows:
[http://gyazo.com/0f1cc91cd2c022225767baa640eb1f9b](http://gyazo.com/0f1cc91cd2c022225767baa640eb1f9b)
and this is what my partitions look like:

[http://gyazo.com/11990c01bc2b840641ef1034a8ed06f0](http://gyazo.com/11990c01bc2b840641ef1034a8ed06f0)

This is what the Ubuntu installer shows: 

[http://gyazo.com/6f799721fb18fceddff49e55adf726f8](http://gyazo.com/6f799721fb18fceddff49e55adf726f8)
(This is not my drive, but I get the exact same result)

I am not completely sure that my partition table is damaged, but that seemed to be the most common issue among other people.

I would appreciate any answers or indications as to what I might do to fix this.
Oh, I would like to mention that I had this setup (Win7 dual-boot Ubuntu) before my Win7 re-installation, but GRUB didn't show up when I booted my new Win7 (Windows bootloader must have deleted it) so I assumed my Ubuntu partition was lost.
Cheers!

[SIZE=2]UPDATE:

I just downloaded gdisk and ran it, show up with:

[/SIZE][http://gyazo.com/bbfe70522408a9d5e6530f094115d9ec](http://gyazo.com/bbfe70522408a9d5e6530f094115d9ec)

[SIZE=2][/SIZE]I think this is a pretty clear indicatio that my partition table is damaged. Any ideas on how to fix it from Windows?

---

### Post by yancek on 2014-07-12
Your second image shows Ubuntu on partition 4 but your last image shows only windows partitions including the 100MB boot partition and 3 ntfs.  You can't install Ubuntu on an ntfs, it won't work any better than installing windows on a Linux filesystem.  Might you be trying to use wubi, installing Ubuntu inside windows as a program?  If so, it is not supported and not expected to work on recent releases of Ubuntu.  Could you post a link to whatever tutorial you were using?

---

### Post by Roland_Batovski on 2014-07-12
In the second image I had the Memory Stick (named "Ubuntu 14_0") with Ubuntu on it plugged in. It's marked as a "Removable".
I am trying to install Ubuntu the normal way: created a Live USB with 14.04 on it, using LiLi and then booted from the USB to go into Linux Live USB mode, then tried installing it from there
As you can see, I have 20GB set aside for the installation of Ubuntu.

I realise that can be a bit confusing, I apologize. Here is a new image with the Memory Stick plugged out:

[http://gyazo.com/a7050727d830863d157c056dacd84d53](http://gyazo.com/a7050727d830863d157c056dacd84d53)

---

### Post by yancek on 2014-07-12
You already have four windows partitions.  Even though you have 20GB of unallocated space it will not be possible to install there.  You would first need to shrink the largest windows partition but that won't really help as with mbr, you can only have 4 primary.  You would need to delete one of the partitions and use that to create an extended partitionin which you can then create a logical partition.  This would probably not work too well as you probably need them.  You should be able to use GPT partitioning and create more primary partitions.  I'm not familiar with it so wait for someone else to offer advice or do some online searches on GPT partitioning.

---

### Post by oldfred on 2014-07-12
Was drive gpt?
Your report from gdisk seems to indicate that it was. Was previous Windows install UEFI?

If drive has both gpt and MBR(msdos) signatures, the installer gets confused and does not know if you have MBR or gpt. The Windows installer in BIOS mode does auto convert a gpt drive to MBR as that is the only way it can boot in BIOS boot mode. But it does not convert completely and leaves the backup gpt partition table.

You can remove backup with gdisk but fixparts is easier.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

The other most common issues are that drive already has the 4 primary partitions used or Windows is hibernated (Windows 8 is always hibernated if fast boot is on).

      
 Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Ben_Cunningham on 2014-07-13
Make sure you have the right drivers for your SATA/other ports. Try plugging the HDD's into the Intel chipset as a last resort

---

### Post by Roland_Batovski on 2014-07-13
Thanks for all the help guys. Sadly, after using gdisk inappropriately, I managed to completely destroy my partition table and my Windows wouldn't boot anymore. I had to install a fresh copy of Windows and lost all my data to no avail, as the problem still persists. I even tried installing Ubuntu first and then Windows ( doing it the awkward way around ), but the Ubuntu installer says "input/output error on read from /dev/sda" even on a freshly wiped drive. I even tried different distros (mint, fedora, arch) and I'm getting the same result. I'm guessing my HDD might be damaged. I 've lost all of yesterday  trying to fix this and I'm soon to lose my patience. I might just buy a new HDD for my laptop and end the ordeal.

The funny thing is, the freshly installed copy of Windows works like a charm...
I am really confused and unsure of what to do next.

Again, thanks for the time put into helping me!

---

### Post by Roland_Batovski on 2014-07-13
UPDATE 2:

I wiped my HDD clean and reinstalled a fresh copy of Win7 x64. The problem of installing any sort of Linux distribution still persists. None of the installers see my current partition table. I will post results about my partitioning below:

Result of running "list disk" and "list volume":
[http://gyazo.com/30dbe1195917fbe38d983c9ef0983a43](http://gyazo.com/30dbe1195917fbe38d983c9ef0983a43)

My current partitions as seen in Disk Management:
[http://gyazo.com/32738a8d06f086e7e54470e33879717a](http://gyazo.com/32738a8d06f086e7e54470e33879717a)

Result of running FixParts from Windows cmd on drive "0:":
[http://gyazo.com/e006ea2d1936c0e924ff3f32003a8056](http://gyazo.com/e006ea2d1936c0e924ff3f32003a8056)

FixParts seems to indicate no problems with my partition table, or any sort of GPT vestiges.

I still cannot install Linux because of the same "input/output error on read from /dev/sda" message that pops up as soon as I press "Install now". 
I am now inclined to think that my partition table is fine, so there must be some problem elsewhere. I'm going to run a full scan on my HDD now and post the results when it's done, just to check whether it's corrupted or not.
I would appreciate any sort of help or indication. Thanks a lot!

UPDATE 3:

Ran the scan on my HDD and it appears to be intact, no data corruption according to Windows.
I booted into Live USB Ubuntu and ran "fixparts", "fdisk -l /dev/sda", and "gdisk -l /dev/sda". Got some pretty shocking results:
[http://gyazo.com/c1096dc43983038d31104c992fd304bb](http://gyazo.com/c1096dc43983038d31104c992fd304bb)
It seems like Ubuntu is completely unaware of my MBR for some reason, which would explain why the installer doesn't show the partitions.
When I try to run Gparted I get a similar error:
[http://gyazo.com/8a9f60cb28599a6618c1ee2f9c3361ff](http://gyazo.com/8a9f60cb28599a6618c1ee2f9c3361ff)
Pressing Retry/Ignore/Close just doesn't do anything...

Any ideas?

Sorry to be spamming this forum but I'm getting absolutely desperate.

Cheers!

---

### Post by Josiah_Kane on 2014-07-13
I know this isn't the question you're asking, but it may be worth considering other options. 
If you're still just trying out Ubuntu (which I infer you may be if you want to give it just 20 gigs) you might want to opt for a virtual machine instead of a dual boot. It won't get you the same low level hardware access (or perhaps more it might save you from some of the troubles there associated with) but it's far safer, a good spot more convenient (e.g. for sharing things between operating systems) and will be quite enough to mess around with. The snapshots feature of many VMs is particularly useful for un-breaking things as you poke around the new OS.

Assuming that's not what you're after, my gut says look at your BIOS (or equivalent, depending on how new the machine is) settings at this point. 
The other option, if you happen to have a spare computer lying around (or can lie to a friend about the chance you break theirs if you pinch it for a while) is to swap your hard drive into the other machine. That should fairly categorically rule in/out whether there's actually anything about the hard drive causing trouble.

---

### Post by Roland_Batovski on 2014-07-13
Yeah the only reason I started doing this is because I wanted to get rid of my VM ^_^ It's all nice and dandy but I'm trying to use dual monitors at work and the VM support for that is a bit messy.
My laptop is indeed running BIOS, what kind of options should I look at? Could you please be more specific?
I doubt there is anything wrong with the HDD itself, as I'm currently running Windows on it, and ran tons and tons of tests on it, passing all of them. There must be something else going on, but I can't quite put my finger on it.
Thanks, Josiah!

---

### Post by oldfred on 2014-07-13
The errors from sudo gparted are more from using sudo instead of gksudo. But that is not your main issue.

Not sure why if drive is now fully MBR(msdos) that neither fdisk nor gdisk see it. If MBR I would not use gdisk.

What does this show, anything?
sudo parted -l

And does this output anything into the text file?
       sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by Josiah_Kane on 2014-07-14
Every machine's bios settings are different so it's very hard to say; but most have a few options to detail how the drives are set up, things like RAID and IDE vs AHCI, or even which drives are masters and slaves, and any of those could thoroughly confuse matters. I think it's one of those situation where Linux respects its elders/behaves itself/gets its configuration from the  BIOS while Windows completely ignores settings if it doesn't think they  make sense. 
I can't be much more specific without sitting in front of the machine. Sorry.

---

### Post by Roland_Batovski on 2014-07-14
oldfred,
Ran the commands you told me about. This is the result:

[http://gyazo.com/d3c6ad19591411120cb9c53290a5cf0c](http://gyazo.com/d3c6ad19591411120cb9c53290a5cf0c)

Sounds like either Linux can't read the MBR (which seems weird) or something is wrong with my HDD (which is unlikely, seeing as I'm perfectly running Windows on it and encountered no problems so far).


Josiah, 
I also looked in my BIOS and the only thing I could find related to what you were saying is that my SATA is set up as AHCI, the other option was ATA.

Cheers!

---

### Post by oldfred on 2014-07-14
You can copy & paste terminal output directly in your post. If longer use code tags. Easy to add code tags with advanced editor and # in edit panel.

Almost always AHCI works better, but a few exceptions.

Seems to be a hard drive issue and I have seen it before, but not seen a solution.

What does Disks(14.04) or Disk Utility(12.04) show? Anything?
And what does testdisk show?

You can try this also:
 Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Roland_Batovski on 2014-07-14
The reason I'm posting pictures ( like a caveman :3 ) is because, for some reason, after 1 or 2 minutes in Ubuntu Live, my USB Keyboard, Laptop Keyboard, USB Mouse and Touchpad stop responding and I can't do anything about it. Therefore I'm booting back and forth to take pictures and then post them from Windows.

Here are the results:

[http://gyazo.com/d34f67694b0a5088c3233a323bb843ec](http://gyazo.com/d34f67694b0a5088c3233a323bb843ec)
[http://gyazo.com/d34f67694b0a5088c3233a323bb843ec](http://gyazo.com/d34f67694b0a5088c3233a323bb843ec)
[http://gyazo.com/94032072449c112304ac584762ea2ea6](http://gyazo.com/94032072449c112304ac584762ea2ea6)
[http://gyazo.com/43cc4f635ffb1bd99dc24b64eaae4fef](http://gyazo.com/43cc4f635ffb1bd99dc24b64eaae4fef)

I couldn't find anything called "testdisk". Not sure what you're referring to. "sudo apt-get install testdisk" didn't work either :-/

I ran CHKDSK on my entire hard drive and it was all fine

---

### Post by oldfred on 2014-07-14
Your first two screen shots are of your CD/DVD, you want those of device /dev/sda.

Did you run the remove RAID commands?

Testdisk is in repositories, but you may have to turn on universal?

       [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

---

### Post by Roland_Batovski on 2014-07-14
Sorry about that...

[http://gyazo.com/79ba8415d6131e1168a1893a9305e405](http://gyazo.com/79ba8415d6131e1168a1893a9305e405)

here you are

The dmraid commands just gave Input/output error as seen in the last two links

---

