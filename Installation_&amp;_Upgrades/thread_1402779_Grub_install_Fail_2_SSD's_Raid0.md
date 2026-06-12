---
title: "Grub install Fail: 2 SSD's Raid0"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by allg33k on 2010-02-09
I've got a new Dell M6500 with 2 ssd drives in it.  I've set it up Raid0 and start my install of 9.10.  I then manually set up the partitions as follows.  8 gigs swap (I was told to make swap as big as the ram I have), root is 20 gigs, and home is 140 gigs.  The partitions are created and the install goes fine until it gets to 94% then it says that grub failed to load into target.  The only option is ok, which then starts the live CD.  I can then see my /root and /home partitions in the gui under computer.  I can click/mount the 20 gig root and see that the /boot is there and the grub folder is under it.  So I started searching how to manually install grub and I found this site: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://mail.westyost.com/exchweb/bin/redir.asp?URL=https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

The first step I get this:

ubuntu@ubuntu:~$ mount | tail -1
/dev/mapper/isw_dcfibdbgfg_Volume02 on /media/fe2edc8f-2ff1-493d-9444-c123e3ded8b0 type ext4 (rw,nosuid,nodev,uhelper=devkit)

Second step goes as the page says:

ubuntu@ubuntu:~$ ls /media/fe2edc8f-2ff1-493d-9444-c123e3ded8b0/bootabi-2.6.31-14-generic         memtest86+.bin
config-2.6.31-14-generic      System.map-2.6.31-14-generic
grub                          vmcoreinfo-2.6.31-14-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic

Then the problem:
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/fe2edc8f-2ff1-493d-9444-c123e3ded8b0/ /dev/mapper/isw_dcfibdbgfg_Volume2
grub-probe: error: no mapping exists for `isw_dcfibdbgfg_Volume02'
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

I'm not sure what to do from here. Any help would be appreciated.  I'm assuming I'm not telling it to install in the correct location.  I saw a bunch of simular bug reports from back in December but not sure if that issue has been overcome yet.  From what I saw it sounds like it's an issue with grub2.  I figured well screw 9.10 and tried 9.04 but it doesn't seem to have the right raid drivers because it doesn't see the partitions in the raid array.

---

### Post by darkod on 2010-02-09
If you are using fakeraid (motherboard bios raid) usually you need to install with the alternate install cd, not the standard desktop livecd.
Also, usually grub installation is done manually. Haven't tried it, but there seems to be step by step here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Since you already have ubuntu installed, just focus on the part about installing grub. Not sure if you will need the alternate cd or you can use the desktop cd since you came so far.

---

### Post by allg33k on 2010-02-09
I'm using the RAID option in the bios.  I just read something on another site about the alternative CD on another site.  I also read something about if the nic is plugged into the internet it will get the correct drivers/etc on it's own.  I'm trying that now.  From what I read about the fakeraid thing it would be fine if I wasn't dual booting.  I left that part out initially because I didn't think it really mattered.  None-the-less I do have another partition with Win7 on it.  So from my understanding the fakeraid isn't an option.  There seems to be a lot of Grub2 issues.  
 
So as of now, I'm trying to reinstall.  With the nic plugged in.  I also changed the bootloader install area on the advanced button at the end of the install to point to the volume I have set aside for "/"  We'll see where that gets me.

---

### Post by darkod on 2010-02-09
> **allg33k said:**
> I'm using the RAID option in the bios.  I just read something on another site about the alternative CD on another site.  I also read something about if the nic is plugged into the internet it will get the correct drivers/etc on it's own.  I'm trying that now.  From what I read about the fakeraid thing it would be fine if I wasn't dual booting.  I left that part out initially because I didn't think it really mattered.  None-the-less I do have another partition with Win7 on it.  So from my understanding the fakeraid isn't an option.  There seems to be a lot of Grub2 issues.  
 
So as of now, I'm trying to reinstall.  With the nic plugged in.  I also changed the bootloader install area on the advanced button at the end of the install to point to the volume I have set aside for "/"  We'll see where that gets me.

Sorry, I didn't quite understand the part about dual booting. Actually fakeraid is necessary when dual booting because it's the only way (as far as I know) of having both windows and ubuntu on a raid.
In case you want only ubuntu, a software raid solution is much better. In short, raid settings in BIOS are disabled, equal partitions are created on the hdd and actually ubuntu is configuring them in raid array, hence software raid.
But there are still small tweaks for grub in that situation too.
I don't know much about raid so I can't help more, sorry. I was considering it and I have few links bookmarked when I was researching.

---

### Post by oshunluvr on 2010-02-09
IMO fakeraid is a huge PITA. Whereas linux software RAID is easier and safer. Safer because if your computer dies (not a drive) your data is also gone unless. With software RAID, you could install the SSD's in another computer and access all your files.

Partition each SSD with a 4gb swap as primary1, 400gb /boot (non-raid) primary2, then the remainder as logical divided up how you like.

---

### Post by darkod on 2010-02-09
> **oshunluvr said:**
> IMO fakeraid is a huge PITA. Whereas linux software RAID is easier and safer. Safer because if your computer dies (not a drive) your data is also gone unless. With software RAID, you could install the SSD's in another computer and access all your files.

You could??? I haven't heard that before.


> Partition each SSD with a 4gb swap as primary1, 400gb /boot (non-raid) primary2, then the remainder as logical divided up how you like.

You mean 400MB for /boot right? 400GB is waaaaay toooo much. :)

---

### Post by allg33k on 2010-02-09
I got it to install.  SSSSSSSsssssssssssssswwwwweeeeeet!  So at this point I'm not exactly sure why it installed.  LMAO, I didn't use the Alternative CD.  I'm thinking it's because the advanced option I changed at the confirmation screen before the install starts.  It seems to me that by default the location it's trying to install the bootloader (grub) is set to hd0.  I used the drop down and choose the partition that I knew was "/" (root).  I had a few different options.  One was the entire Raid Array.  I tried that one yesterday and it didn't work.  Then there was the partition I knew was root, and the one that was my home, than a last one that I wasn't sure what it was.  Either way I think the fix for me was setting it to the root partition.  Anyways, thanks for all your help out there and hopefully this helps someone else out there.

---

### Post by darkod on 2010-02-09
Did you try to reboot? Usually if you install grub onto a partition like you did, you have to somehow "call it", or called chainloading. But maybe it will work like this too, haven't used raid myself.
Can you please confirm you are rebooting without problem.

---

### Post by allg33k on 2010-02-09
Yeah, that's the first thing I tried.  I read a bunch of posts about getting it to work then on the reboot it was hosed.  I rebooted, it booted right up, and i logged in and ran all the updates.  It rebooted again.  The only thing I have to do is add my windows partition into the bootmanager so I can choose it to boot from.  Haven't verified that part yet.

---

### Post by oshunluvr on 2010-02-09
> **darkod said:**
> You could??? I haven't heard that before.

You mean 400MB for /boot right? 400GB is waaaaay toooo much. :)


Lol - yeah 400MB Geez - that would be a HUGE kernel ;)

With mdadm RAID you can re-assemble the raid devices on any linux system (I use that term loosely) as long as your filesystems are intact. 

One example - I had four 400gb (yes GB :D ) drives with several RAID devices on them. Various levels and numbers of devices. I decided to switch to Kubuntu from openSUSE, I installed kubuntu, ran "mdadm --assemble --scan" and all my RAIDs started up.

---

