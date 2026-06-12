---
title: "Move installation from accross two hardrives to one"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by noteviljoe on 2010-02-17
So, being a dunce, when I first installed Ubuntu (as a dual boot with windows xp) I had by external hard drive switched on and it installed across by internal 250GB hard drive and the external 500GB hard drive.

This has meant that I have had to have the external hard drive switched on all the time and no doubt makes things slower.

I now want to sort this situation out: what should I do? :?

I have attached a screen shot of the disk utility tool

---

### Post by mikewhatever on 2010-02-17
Automatic installation across two hard drivers sounds very unlikely. Can you post the output of the following command:

sudo fdisk -l

According to the screenshot, all Linux partitions are on the same hdd.

---

### Post by noteviljoe on 2010-02-17
> **mikewhatever said:**
> Automatic installation across two hard drivers sounds very unlikely. Can you post the output of the following command:

sudo fdisk -l

According to the screenshot, all Linux partitions are on the same hdd.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9887150a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       24244   182443008    7  HPFS/NTFS
/dev/sda4           24498       30402    47417344    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x548c3cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       27179   218315286    c  W95 FAT32 (LBA)
/dev/sdb2           27180       60801   270068715    5  Extended
/dev/sdb5           27180       60425   267048463+  83  Linux
/dev/sdb6           60426       60801     3020188+  82  Linux swap / Solaris

---

### Post by mikewhatever on 2010-02-17
That confirms the info provided by the screenshot, all Linux partitions are on sdb. What's the problem exactly?

---

### Post by noteviljoe on 2010-02-17
So maybe ubuntu is just installed on the external drive.

If this is the case then I still have a problem, this means I have to have it switched on at all times and its slow because goes through USB.

So how do I get it installed on the internal drive?

All I can think of: I could reinstall on the internal drive (with external switched off), then wipe external drive.

However: I have got quite a lot of data that I don't want to lose (Mostly MP3 albums). Its too much to fit on the internal drive (i.e. more than 250 GB). It would fit on the external - if it wasn't partitioned - but I can't undo this as then the computer won't start up. Currently Most of the data is on the external drive data partition and some on internal.

Does that make sense?

---

### Post by mikewhatever on 2010-02-17
You can use the installation cd to run a live session, then delete the Ubuntu partitions from the external hdd, make whatever partitions you want there, copy the data you want, then disconnect it and reinstall Ubuntu. Alternatively, perhaps getting a large external hdd for backups is something to consider now.

---

### Post by darkod on 2010-02-17
> **mikewhatever said:**
> You can use the installation cd to run a live session, then delete the Ubuntu partitions from the external hdd, make whatever partitions you want there, copy the data you want, then disconnect it and reinstall Ubuntu.

+1

Unless you have loads of data on the external too that you have nowhere to move. In that case calculate the minimum space needed for the data you want to keep from both drives and figure out how and where to keep it until you finish the process.
For example, if you need to keep some data from the ubuntu, but not a lot, copy that data first on the internal, wipe the external making it one or few large partition for data, then move data from the internal creating free space to install ubuntu there.
Or something like that.

---

### Post by noteviljoe on 2010-02-17
Thanks :-)

I'll give it a try (I am a little scared of loosing my patiently built up music collection but fingers crossed!)

---

### Post by noteviljoe on 2010-02-17
> **darkod said:**
> +1

Unless you have loads of data on the external too that you have nowhere to move. In that case calculate the minimum space needed for the data you want to keep from both drives and figure out how and where to keep it until you finish the process.
For example, if you need to keep some data from the ubuntu, but not a lot, copy that data first on the internal, wipe the external making it one or few large partition for data, then move data from the internal creating free space to install ubuntu there.
Or something like that.

So yea, mikes suggestion won't work :-(, as the data is currently on the external drive and won't fit on to the internal drive (that's why its on the external). There is some more data I want to squeeze onto the external drive. But it won't fit while the partition is still there!

---

### Post by darkod on 2010-02-17
Well, you have to figure something out. It's more difficult for us because we can't even see the computer.
How much space did you plan to allocate to ubuntu on the internal? Do you have enough free space to do the install there? (leave the external aside for the moment)

How about getting a 10-pack or 25-pack of DVD-Rs and copying some data there? 10pack will free approx 45GB for you, and 25pack almost 100GB.

---

### Post by mikewhatever on 2010-02-17
> **noteviljoe said:**
> So yea, mikes suggestion won't work :-(, as the data is currently on the external drive and won't fit on to the internal drive (that's why its on the external). There is some more data I want to squeeze onto the external drive. But it won't fit while the partition is still there!

Actually, I've suggested removing the Ubuntu partitions before transferring data. Regardless, I think it best to have a good backup of all files you don't want to loose, be it music, photos or documents, before starting messing with partitions.
Perhaps you should restore your Windows bootloader for now, sort out the backup issue and then try installing Ubuntu again.

---

### Post by noteviljoe on 2010-02-17
I've bought a 1TB drive now so this should solve my problems - but I just have to think carefully about order to do things.

Does the following procedure seem right? (I might get some of the tec terms wrong):

1. Install new 1TB hardrive as 'slave' data drive (making sure it gets file system that can ber read by windows)
2. Copy all data on to it (from internal and external drive)
3. Wipe clean (format?) external hard drive (making sure I do this in a way that makes it readable to Windows as well as Ubuntu - by picking the right files sytem)
3. Disconnect external drive and new 1TB internal drive
4. Fresh install windows onto old 250GB internal drive (wiping out all old stuff in the process)
5. Then install Ubuntu over the top of windows to get duel boot thing (in case I have to use windows for bad things)
6. Spend ages trying to get Ubuntu set up in a way that works for me.

One question, (sorry if this is a dumb one) it doesn't matter if data is stored on different hard drive to one OS is installed on does it?

---

### Post by noteviljoe on 2010-02-17
> **mikewhatever said:**
> Actually, I've suggested removing the Ubuntu partitions before transferring data. Regardless, I think it best to have a good backup of all files you don't want to loose, be it music, photos or documents, before starting messing with partitions.
Perhaps you should restore your Windows bootloader for now, sort out the backup issue and then try installing Ubuntu again.

Sorry, I see what you mean. Given that I don't know what you mean by restore the windows boot loader do you think the idea above will work/be safe for all me 'precious' data?

---

### Post by darkod on 2010-02-17
The filesystem readable in both windows and ubuntu is NTFS. It is up to you whether you will make one single partition on the 1TB or 2-3, depending how you organize the data.

What you laid out as a plan is OK, just make sure when making the clean install of windows don't let it take the whole hdd. Then you would have to shrink it to make space for ubuntu, and double the work. Plus the risk to corrupt the new windows install when shrinking.

---

### Post by mikewhatever on 2010-02-17
> 4. Fresh install windows onto old 250GB internal drive (wiping out all old stuff in the process)
5. Then install Ubuntu over the top of windows to get duel boot thing (in case I have to use windows for bad things)

Just make sure you don't need anything on the 250GB hdd, siince formatting it will erase all data.
Installing Ubuntu over Windows is not the way to set up a dual boot. Please refer to any of the guides on how to dual boot with Windows.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Edit: Video guide [http://static.screencasts.ubuntu.com/videos/20061204_installing_dual_boot.ogg](http://static.screencasts.ubuntu.com/videos/20061204_installing_dual_boot.ogg)

---

### Post by oldfred on 2010-02-17
If you create a new /home on your internal and move the data mostly the hidden files/folders starting with . from the external you will save most of your settings from the existing install. You can separate your music into a data folder to keep /home settings as a smaller partition.

move home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by noteviljoe on 2010-02-18
Why is nothing ever easy? 

I just tried to install the new sata hard drive following instructions here: [www.easeus.com/resource/install-sata-hard-drive]("http://www.easeus.com/resource/install-sata-hard-drive.htm")

It turns out that the motherboard seems to lack a Serial ATA connector on it (the drive I got at the moment is connected by SATA but as stated above I need to keep that drive in).

I think that I do have an available 'PCI slot' which the page tells me I can use with 'a Serial ATA host adapter' but I can't seem to find one of these when searching on the website of my local computer shop ([www.aria.co.uk](www.aria.co.uk)).

Am I out of my depth or should I persevere? Any help is much appreciated.

---

### Post by noteviljoe on 2010-02-19
Yeay, I made this all work.

I now have a windows and Ubuntu installed on the 250GB drive and my music stored on the 1TB drive.

One last question, when I want to play music etc. from the data drive I have to mount it when I log on - not to much hard work but annoying when I just open up music player (songbird) and it tells me music is missing.

Is there anyway to have it auto-mount when I turn the computer on?

---

### Post by noteviljoe on 2010-02-19
Also (though less important) by Wanna the fish no longer works
She sits there fine and dandy but when you click on her insteed of a prediction you get "Unable to locate the command to execute"

---

### Post by oldfred on 2010-02-19
Who's Wanna?

You have two choices. You can mount it permanently like you are each time manually with an entry in fstab or you can mount it hidden and add a link into your home so it looks just like another folder in /home.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

### Post by noteviljoe on 2010-02-20
Thanks oldfred I'll have a look at those threads.

Wanda is a fish that you can add to your panel - its tells fortunes.

---

### Post by noteviljoe on 2010-02-21
> **noteviljoe said:**
> Thanks oldfred I'll have a look at those threads.

Wanda is a fish that you can add to your panel - its tells fortunes.

Solved the wanda problem by following advice on the following thread: [http://ubuntuforums.org/showthread.php?t=1162740&highlight=wanda](http://ubuntuforums.org/showthread.php?t=1162740&highlight=wanda) \\:D/

---

