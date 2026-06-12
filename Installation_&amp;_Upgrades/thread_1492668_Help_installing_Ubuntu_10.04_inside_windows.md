---
title: "Help installing Ubuntu 10.04 inside windows"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by vickystylton on 2010-05-25
I downloaded the ubuntu 10.04 i386 iso and burned it to a cd (I know there's no need for that, but I just did it.). Then i launched wubi.exe from the cd. I went through the common procedures and rebooted the machine. After rebooting, I selected the ubuntu from the boot menu. What I expected was for the ubuntu desktop to load. Instead, the 7-step Install ubuntu window's popping up. It asks for the partition too, which was not expected with wubi [install inside windows]. I read on the net that it'll just do some installations on its own and that we needn't configure anything.

There are two options provided: to erase the whole hard disk or select the partition manually. When I quit the installation process, I end up with the live environment.

Then I rebooted into windows and found that 12 gb of hdd space was provided for ubuntu. What might be the problem?

---

### Post by bcbc on 2010-05-25
I think you must have booted from the ubuntu CD - you probably have your computer set in the bios to boot from cd/dvd before the harddrive. 

What you wanted was to boot from the hard drive and then select ubuntu (while having the cd available in the drive).

I'm not sure what happened with the 12GB reserved for ubuntu unless you only stopped the install after partitioning the drive. So I guess your options are to reinstall wubi (have to uninstall first Control Panel -> Add/Remove programs), or to just use the 12GB and install ubuntu to that as a regular dual boot.

If you want to stick with wubi, then you can reclaim the 12GB - either format as ntfs and use as a D: drive, or merge them (easier with vista/win7 than XP).

And read the following sticky beforehand for known lucid issues and workarounds: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by vickystylton on 2010-05-25
> **bcbc said:**
> I think you must have booted from the ubuntu CD

Well, when I tried it for the first time, that was the case. But then, I uninstalled wubi [and I got back the 12 gb. thats not a problem.] and then installed again. This time, I was careful not to insert any cd in the drive. So it went straight to the choose OS menu.

> **bcbc said:**
> What you wanted was to boot from the hard drive and then select ubuntu  (while having the cd available in the drive).

Yes, thats what I did the second time. But I guess the cd is not really required, as wubi copies the iso to the hard disk.

Then, I selected ubuntu from choose OS menu. Now a 'verifying installation' window appears, followed by the ubuntu installation procedures [starting from checking the time zone to partitioning my drive]. For installing inside windows, partitioning of the drive's not required, right?

---

### Post by bcbc on 2010-05-25
No, no partitioning required. Wubi installs to virtual disks that are stored under the windows file system in c:\ubuntu\disks\ 
You should see a root.disk and a swap.disk, and sometimes a usr.disk.

I am surprised that the wubi install copies the iso to the hard drive - I know it does that if you run wubi.exe standalone, but thought that if you ran it off the cd it used the cd for the install. This may have changed with 10.04 I guess - I've only ever installed 9.10 wubi.

---

### Post by vickystylton on 2010-05-25
Yup, there's a root.disk (11.4 gb) and a swap.disk (250 mb) at D:\ubuntu\disks. Also a boot\grub folder which's empty. :D

I guess the iso might be new in ubuntu 10.04. Its located at D:\ubuntu\install. Also, there's a grub.cfg inside D:\ubuntu\install\boot.

Any specific file I must look for in this directory?


Also, the drive in which I've installed ubuntu ( D: ) does not appear in the live environment. Why's that?

---

### Post by bcbc on 2010-05-25
> **vickystylton said:**
> Also, there's a grub.cfg inside D:\ubuntu\install\boot.

Any specific file I must look for in this directory?

Also, the drive in which I've installed ubuntu ( D: ) does not appear in the live environment. Why's that?

You shouldn't have to do anything manually to get ubuntu to boot after the installation is complete - it should be simply a matter of selecting it from the windows menu. Can you describe in more detail what problems you are having?

As far as seeing drive D: under the live environment, it should be there. Look under places, and click on it to mount.

If you're booting the actual wubi ubuntu it will be mounted under /host and the other drive can be mounted from Places

---

### Post by vickystylton on 2010-05-25
The main problem I have is that ubuntu asks for partitioning my drive when I select ubuntu from the boot menu, instead of going straight to the login screen. I've attached the screenshots.

So is this what really should appear for 'install inside windows' option?


Also, I guess sda5 is my D: drive. It says unknown in the screenshot.

---

### Post by bcbc on 2010-05-25
> **vickystylton said:**
> The main problem I have is that ubuntu asks for partitioning my drive when I select ubuntu from the boot menu, instead of going straight to the login screen. I've attached the screenshots.

So is this what really should appear for 'install inside windows' option?


No. That isn't right. It seems to be booting from the CD. Did you see a screen offering "Try it" (without changes, and "Install". This shouldn't appear with the wubi, it should start immediately installing into the virtual disks created.

---

### Post by Mark Phelps on 2010-05-25
The Wubi Guide linked below is dated, but it does show the kinds of screens you should be getting:

[https://wiki.ubuntu.com/WubiGuide#Installation]("https://wiki.ubuntu.com/WubiGuide#Installation")

---

### Post by vickystylton on 2010-05-25
> **bcbc said:**
> No. That isn't right. It seems to be booting from the CD.

But I haven't inserted any cd, and I selected ubuntu from the boot menu.

 > **bcbc said:**
> Did you see a screen offering "Try it" (without changes, and "Install".  This shouldn't appear with the wubi, it should start immediately  installing into the virtual disks created.

The first screen that appears when I select ubuntu is 'verifying the installation configuration'. Then appears 'setting the clock'. I've attached the screens after that.

> **Mark Phelps said:**
> The Wubi Guide linked below is dated, but it does show the kinds of  screens you should be getting:

[https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation)

Yes, I get those screens in windows. The problem for me is after selecting ubuntu from the boot screen.

---

### Post by bcbc on 2010-05-25
Hmm, well maybe it does have something to with the fact that your second partition is unknown. Have you tried installing on your c: drive? Or another partition?

By the way, did you select YES to unmount or NO on that second screenshot?

---

### Post by bcbc on 2010-05-26
OK I ran a wubi install (wubi.exe and the 10.04 for 386) and there was absolutely no prompting after rebooting and selecting ubuntu (except an option to press ESC for custom settings which I ignored). It continued right until the end, and then rebooted without prompting from me.

Anyway, after all that, I ended up at a grub rescue prompt when I selected Ubuntu from the windows menu. It has messed up something on my external drive as grub can't see any partitions. I haven't had a chance to load up the external under ubuntu so I can figure out exactly how it's messed up.

So - I guess this thing is a little flaky :)

---

### Post by bcbc on 2010-05-26
EDIT: I tried again this morning after booting from a live cd and running analysis (but no updates/fixes) - and now it's working!? Maybe it's my external that's flaky.

Last night wubi wouldn't boot and in addition, the external wouldn't boot (it has grub2 in the MBR and a couple of ubuntu versions installed).

Here the analysis part...

Bootinfoscript - > sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb8 starts at sector 82895463.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.diskfdisk - > /dev/sdb8        82895463   103378274    10241406    b  W95 FAT32
> TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 100 GB / 93 GiB - CHS 12188 255 63
     Partition                  Start        End    Size in sectors
 8 L FAT32                 5160   1  1  6434 254 63   20482812 [Wubi]

Boot sector
OK

Backup boot sector
OK

Second sectors (cluster information) are not identical.

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.


---

### Post by vickystylton on 2010-05-26
> **bcbc said:**
> Hmm, well maybe it does have something to with the fact that your second partition is unknown. Have you tried installing on your c: drive? Or another partition?

Yep, I tried installing on my E: drive. Same result. E: is the unknown one now. I've attached the screenshot.


> **bcbc said:**
> By the way, did you select YES to unmount or NO on that second screenshot?

I selected YES to unmount in that screenshot. Anyways, I've tried both, doesn't make much difference. I've attached the screen right after selecting NO with this post (screenshot 5).

Might there be some problem with the iso I downloaded? 

By the way, I tried installing via cd, manually with iso and wubi in the same folder, and by mounting the image. Didn't expect to make much of a difference though.

I'll post the results of bootinfoscript here soon.

---

### Post by bcbc on 2010-05-26
Did you try running wubi.exe standalone and letting it download the iso itself? It takes a long time (of course) but at least it will get the correct one for your architecture.

Just to reiterate I didn't get any of the screens you are getting after rebooting. It goes straight into the installation. So something weird is happening.

There is a wubi.log on your windows drive under your user data directory. Maybe that can shed some light as well.

EDIT: I see you already mentioned you downloaded the i386 version. You can boot the CD and let it check for errors, or you can run an md5sum on the .iso and ensure it is valid.

---

### Post by vickystylton on 2010-05-26
I checked the md5sums. They match.

Now, another problem seems to have arisen. At the time of install, I'd connected my external hdd as well. I did not install ubuntu, but the hdd showed up on the 'prepare disk space' and 'prepare disk partitions'. I also remember that it'd allocated around 350 gb for ubuntu (I did not select it. It was just shown as an option for me in the 'prepare disk space' menu under 'manually select partition' radio button.)

Now, 346 gb of my external hd is missing. The total capacity is being shown as 585 gb instead of 931 gb. Any possibilities that it might be because of ubuntu?

Should I post this as a separate thread?

---

### Post by bcbc on 2010-05-26
Post the results of the [bootinfoscript]("bootinfoscript.sourceforge.net") with the external plugged in.

I don't know whether you should create a separate thread.

Did you proceed after it told you it would use 350GB for ubuntu? You probably should have exited straight away. If not it might have created a new partition of type ext4 that shows up in windows as an unknown partition. 
So that might explain why you only have 585GB showing (that's the partition that windows can see).

But post that script and we can see what's going on.

---

### Post by vickystylton on 2010-05-27
> **bcbc said:**
> Did you proceed after it told you it would use 350GB for ubuntu? You probably should have exited straight away.

Yes, you're right. I did not proceed after that.

Here's the results of bootinfoscript:

> sdb1: _________________________________________________________________________

============================= Boot Info Summary: ==========================

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,228,367,675 1,228,365,628   7 HPFS/NTFS


blkid -c /dev/null:It says 1000.2 GB as the disk size, and the file system as ntfs. So ubuntu hasn't formatted it to ext4, but I still suspect ubuntu. Might be a bug? 

I can try formatting the external, if there's no other choice. But, even in the format window in xp, it says the size is 585 gb. So is there much chance that I'll gain the remaining space too, if I format?

---

### Post by bcbc on 2010-05-27
It looks like it resized the ntfs partition but didn't create a new partition. If you open it up in windows, control panel, adminstrative tools, my computer,  then under the tree Storage, Disk Management, it should show the unused space.

---

### Post by vickystylton on 2010-05-28
> **bcbc said:**
> It looks like it resized the ntfs partition but didn't create a new partition. If you open it up in windows, control panel, adminstrative tools, my computer,  then under the tree Storage, Disk Management, it should show the unused space.

Wow. It never occured to me to look there. Yeah, you're right. 345.78 GB of unallocated space. So how do I get it back?

Edit: Ok, I googled it and found that many partition managers and UBCD might be able to do it. Now my doubt's this: If I do as instructed, I'll be losing all the data right? I'd prefer if there were any methods which doesn't involve losing my data. :) Also, I don't want it as a separate partition.

---

### Post by bcbc on 2010-05-28
> **vickystylton said:**
> Wow. It never occured to me to look there. Yeah, you're right. 345.78 GB of unallocated space. So how do I get it back?

Edit: Ok, I googled it and found that many partition managers and UBCD might be able to do it. Now my doubt's this: If I do as instructed, I'll be losing all the data right? I'd prefer if there were any methods which doesn't involve losing my data. :) Also, I don't want it as a separate partition.

Boot ubuntu and open GParted (I think it's on the live cd or you can install it through synaptic). Then you should be able to resize the partition without losing any data.

Caveat - any resizing partition has risks. So I advise backing up your data.

---

### Post by vickystylton on 2010-05-29
I'll be a bit busy for atleast a couple of days. So I'll experiment with the hd after that.

Still, the problem with wubi hassn't been solved. Will I have to wait for the next release, then? [I don't want to install it by creating a new partition.]

Needless to say, I've already tried installing inside windows via vubi atleast 10 times or more. I tried ubuntu 10.04, kubuntu and ubuntu 9.04. The latter two gave me the error:

> Error 1: Filename must be either an absolute pathname or blocklist.Lucid's atleast starting up when selected from the boot menu.

Will sort out the HD problem and post the updates here soon. :)

---

### Post by bcbc on 2010-05-29
> **vickystylton said:**
> I'll be a bit busy for atleast a couple of days. So I'll experiment with the hd after that.

Still, the problem with wubi hassn't been solved. Will I have to wait for the next release, then? [I don't want to install it by creating a new partition.]

Needless to say, I've already tried installing inside windows via vubi atleast 10 times or more. I tried ubuntu 10.04, kubuntu and ubuntu 9.04. The latter two gave me the error:

Lucid's atleast starting up when selected from the boot menu.

Will sort out the HD problem and post the updates here soon. :)

I have no idea why wubi won't install for you. If lucid runs (booted from a cd) there's really no reason why wubi shouldn't work. If you post the entire results of the bootinfoscript, I can see if there's something strange.

Try looking for the wubi.log (in your user data folders under windows) and post that as well. 

Finally you could try posting under this thread: [http://ubuntuforums.org/showthread.php?t=1439526](http://ubuntuforums.org/showthread.php?t=1439526) - I believe that the Original Poster is the writer of wubi (not that he responds all that often).

But the problem at the moment is that for most people wubi seems to work, and there's not enough info yet to determine why you are not having any luck.

---

### Post by vickystylton on 2010-06-17
Finally, I get time to reply to this post. :)

The external hard disk problem's solved. I created a new partition for the unallocated space with the disk management utility bundled with xp. Then, I merged the two partitions using paragon partition manager. And, the data was far from being lost. All the data in the external was preserved by the partition manager. :)

I did not try out wubi after that. But I guess the result's going to be the same. I'll post it here if I encounter anything different from what I've been experiencing so far with wubi.

Thanks for your valuable time, bcbc! :)

---

