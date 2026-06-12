---
title: "Ubuntu not seeing third drive when installing"
date: 2018-07-28
forum: Installation &amp; Upgrades
---

### Post by bojangels on 2018-07-28
Hey all, 

Recently decided to scrap windows 10 since microsofts bluetooth is flakier than a leper colony and drops all the time. Since I've been using
Linux in various forms at work for the past 10 years, I figured why not do it at home as well. 

Been running Ubuntu 18.04 from a USB for a week, and haven't had a single BT drop. So I sat down 6 hours ago to install it, and I haven't gotten anywhere. 


Current set up. 

Dell XPS 8920
Pre-installed windows 10
1tb HDD
1tb HDD
1 256gb SSD (windows installed)

The 256gb drive with windows installed does not show up in the file manager on ubuntu, whereas the other two drives works fine.

When I try to install Ubuntu, it says I don't have an OS installed. And when I choose "erase disk" the 256gb SSD does not show up
in the drop down. Neither does it show up in the list when I choose "do something else"


I've tried just about anything I can find online, in this forum and other. 

- turned off hibernation
- turned off fast start up 
- set everything I can find to never turn off (HDD etc.)
- turned off secure boot in BIOS
- both ubuntu and windows BIOS mode is UEFI as far as I can tell 


Both of my other drives are being used for storage, and I would like to avoid installing ubuntu on one of them, also I have no idea how
to go about it without messing everything up. 

At this point I'm about to flip my desk and pop downstairs to the apple store and buy a machine that "just works" ;)


Any help would be greatly appreciated!

---

### Post by TallDaveOS on 2018-07-28
I had a similar problem and after trying everything else, I just manually disconnected the cables for the extra drives inside the case. Then the install didn't ask where to put it. After rebooting and shutting down, I connected the other internal drives and all good.

---

### Post by bojangels on 2018-07-28
Thanks TallDaveOS,

I was fearing that I would have to get crawling under the desk to try just that. 
Did it ask you to install along side windows 10 when you had them disconnected, or did you just end up erasing and installing Ubuntu? 

cheers

---

### Post by TallDaveOS on 2018-07-29
Hey. So I'm on a proper machine, and here's my more long-winded answer...

My main PC is a 120GB SSD (for system files); and two 4TB drives (for material), and it was time recently to do a clean upgrade to 18.04 LTS, and for a few days I couldn't get the install to complete properly.

The machine had a default Win (7??) on it when I first bought it, but has only had Linux Ubuntu for the last 6~ish years

I tried two things which seemed to make the upgrade install complete properly, though I've no idea which was the one that actually helped...

Besides physically popping the connectors for the 2 big drives inside the case, which negated the problem for the Install disc of where to install the OS, the other thing that might have caiused the problems was to toggle the "enable secure boot" switch in Bios/ Security/ Advanced - which according to the internets is maybe a problem involving machines with a VirtualBox VM thing.

Hope that helps, Dave

---

### Post by oldfred on 2018-07-29
Dell also needs UEFI updated from Dell and if SSD firmware update from SSD mfg.
Dell also seems to have default setting of RAID or Intel SRT on drives. If using Windows install AHCI driver first and then change UEFI setting to AHCI.

If multiple drives only use Something Else install option.

       Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)

---

### Post by bojangels on 2018-07-30
Thanks guys,

@oldfred - updating BIOS, installing AHCI drivers and then changing to the EUFI setting to AHCI seems to have done the trick. 
The SSD (windows install) now shows up in the list, and the install prompt asks to install alongside windows 10. 

Will run a test installing it as soon as I have time to sit down with it. Might have to update the SSD firmware still, we'll see. 

Also, how did I manage to not find those threads in my hours of googling the the issue haha. 

Thanks again!

---

### Post by oldfred on 2018-07-30
Multiple drive UEFI install is a bit more complicated. I like to have boot files on same drive as Ubuntu, but Ubuntu's grub only installs to ESP on first drive. So I have to manually copy files.

I only use Something Else and always partition in advance, so I have an ESP on second internal or external drive. Before I had UEFI, I started using gpt partitioning and added the bios_grub for BIOS boot. Then when Windows converted to UEFI, I  added both ESP (for future UEFI) & bios_grub (BIOS) to all drives as first two partitions. I still add both, but every install has been UEFI.

---

