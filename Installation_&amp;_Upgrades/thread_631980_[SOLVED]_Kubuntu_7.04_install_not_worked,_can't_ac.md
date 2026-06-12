---
title: "[SOLVED] Kubuntu 7.04 install not worked, can't access windows"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by Dreaming on 2007-12-05
Hey guys. I'm new to linux, well I've tried it before but everytime it has gone wrong for me or I couldn't get something to work so I've gone back to Windows and not bothered with linux. Thought I'd try again. I have 4 hard drives:
2 x 160GB WD1600YS in Raid0 (through the Intel onboard chipset). This is where windows is installed.
1 x 250GB HDT7K500 where Kubuntu was installed
1 x 500GB WDAAKS which has my data (NTFS formatted).

I booted on the live cd, it saw my raid array as two seperate drives which was peculiar (something to do with fake raid?). Anyway, I just went ahead and installed it on my empty safe drive - or so I thought.

From what I can gather, it's formatted the correct hard drive /dev/sdc according to qtparted (which crashes if you look at the raid hard disks - /dev/sda and /dev/sdb). There is / and there is a swap.

But I don't know where it put the boot loader! On starting up, my motherboard is configured to Raid mode, so sees the two hard disks as one, and that's the first that should boot. However, instead it says loading Grub 1.5, error 17. Or words to that effect.

So, I think - this has happened before - to get windows back I need to insert windows cd and fix mbr. Only, when inserting the vista cd it says all is well, and there's nothing to fix.

Really now I just want to find the bit of my hard drives that has grub on it, nuke it, fix windows, then start from scratch but put the bootloader on a different hard disk if that's possible. Although... it still probably wouldn't be able to see Windows, would it?

My priority at the moment is to get Windows back, as it's got documents on. They're still there - I navigated to them in the command prompt on the CD. Though Windows has a less than robust copy system which only enables copying single files. And I've got several hundred. These 'were' backed up but I copied all the backups to my main disk to have a play with linux...

If anyone could help, I'd really appreciate it. It's 6:20am in the morning, I've been trying all night!

Also, Windows version is Vista 32bit. Edit -> I have tried 'fixmbr' and so on, doesn't work in Vista. They have a program to autofix the boot record, but it just says there's nothing wrong with it. All I want to do is say 'I don't care, rewrite it anyway'.

Would it be worth trying to repair Windows install? Would I lose my settings and so on?

---

### Post by Dreaming on 2007-12-05
bump :)

Still on my live cd.

Tried from the microsoft recovery console:
E:/boot/bootsect.exe /nt All which replaced the boot sector, but grub is still popping up first.

If I can find out where Grub is located, I think if I manually delete it then redo the vista one it might work. I don't know... Any help guys?

---

### Post by Pumalite on 2007-12-05
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Dreaming on 2007-12-05
> **Pumalite said:**
> [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Thanks. For the time being though, do you have any ideas how to return my PC to a pre-linux state so I can start from scratch, other than formatting everything?

---

### Post by Pumalite on 2007-12-05
You could try with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
But I think the Raid is your problem.

---

### Post by Dreaming on 2007-12-05
> **Pumalite said:**
> You could try with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
But I think the Raid is your problem.

Yea, I agree. Windows still recognises it, everything is still intact, the bios is set to boot first from the 'Intel Operating' array, which is my two disks. So I have no idea where grub is installed. If it can't read raid, then it installed to one half of the stripe. In which case it shouldn't load anyway because the bios is trying to read both sides. And Windows hasn't complained about it, either. I can't get my head round it.

I'm considering installing vista on a seperate partition, let it do its own bootloader, booting to that vista, using the read/write priveledges to copy the data I need, and then format the array and start from fresh. I would lose my settings this way though.

There must be a way round it that I don't know of.

---

### Post by Pumalite on 2007-12-05
I would get rid of Raid. Save data and fresh reinstall everything. Work with separate drives. Software Raid= minimal improvement and lots of headaches. Unless you have hardware Raid, you are wasting your time.

---

### Post by maybeway36 on 2007-12-05
Find a DOS bootdisk and type
```
fdisk /mbr
```
or from Knoppix type
```
sudo ms-sys -m /dev/hda
```

---

### Post by Dreaming on 2007-12-06
I've got this fixed now. In the end, I changed the boot order of my hard disks, then installed vista again on another partition, and the vista bootloader allowed me to load up my initial partition where I can get at my files.

All files saved (would have been executed if I lost holiday pics!), and am now using the philosophy of PC case modding (or any workshop stuff really) - measure twice, cut once. So before I jump in, I've got the latest 7.10 dvd image which should let me do everything, I'm thinking how my drives will be partitioned, and the best way to do it.

Since I have 4 disks, 2 160gb, 1 250 and 1 500, someone I was speaking to in a bar last night advised maybe I should split the OSs one to each disk. (It's a uni bar, so unfortunately linux and some incredibly complicated computer science stuff was being discussed, which I barely understood *management studies student*).

Thanks for your help all, it really did help :) I see why the RTFM philosophy is used because doing it yourself really does make you learn! How do I change the thread to [Resolved] ?

---

