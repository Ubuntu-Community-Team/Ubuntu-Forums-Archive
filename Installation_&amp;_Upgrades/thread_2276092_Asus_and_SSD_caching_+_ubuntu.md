---
title: "Asus and SSD caching + ubuntu"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by Emma_Arthur on 2015-04-30
Hello,

I just bought the Asus K551LN XO551H and it has a 1to HDD and a 24go SSD. It's supposed to be a caching (hybrid) system on Windows 8, probably with Conductiv Technologies' ExpressCache, although this software does not seem to be intalled (it is in Programmes but nowhere else) and the boot is AHDI and not RAID.
I want to install Xubuntu as a dual boot with Windows, but I want to be able to install /root on the SSD.
At this point, the SSD has a partition on it, and I wish to know whether I can format it safely? Anyone has done that before on an Asus laptop?

---

### Post by oldfred on 2015-04-30
A lot of systems used Intel SRT but I believe that was a UEFI/BIOS setting also.

Several have posted with the SRT they just turned that off, set to AHCI for drives, and installed / to the SSD.

Best to make good backups. I just followed the backup procedures we post here and it did take a bit, including going to the store for more flash drives. I ended up wit 5 DVDs & two flash drives. I made the Dell recovery - 3 DVDs, the Windows recovery - 8 GB flash, and a full recovery with Macrium - 32GB flash needed as it used 20+ on brand new system and two recovery DVDs one Linux and one Windows PE.

May be similar models? What processor and video is your model?Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
 [http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)

Older thread with older Ubuntu, using Dell & SRT, install to SSD.
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Newer versions of Ubuntu do not need RAID meta-data removed, it seems.

---

### Post by Emma_Arthur on 2015-04-30
Thanks !
The thing is I don't know how to disable the cache : I don't have anything like Intel SRT, the drives are in AHCI with no other option, the partition on the SSD is jsut marked OEM by Windows and Unknown by Gparted or Boot-Info. I don't even know if the cache function is really enabled... (is there a way to know?)
Processor is an Intel i5 and video card is an Nvidia Geforce.
I booted on a liveUSB 15.04 Xubuntu without a problem (except I have to change the boot order twice in a row for it to boot).
I am not very worried about the actual installation, jsut about removing that partition.
I did the back-up procedure I saw somewhere (I think the French Ubuntu doc) which involved a bootable USB and a system image : is it enough ? That's just windows, should I also back up Asus stuff? How can I do that?

---

### Post by oldfred on 2015-04-30
Do not know Asus. For either backup or what cache system it is now using. The Intel version was common among all vendors, so maybe they  wanted to be different.

With my new Dell when I did the Windows recovery, it offered to delete the recovery partition and I made a mistake and said no. I should have said yes as I really do not plan on using Windows, but am not ready to totally erase it as I assume somewhere I paid for it. And Dell had its own recovery partition and procedure to copy it to DVDs and it also offered to delete after backup to DVDs. I would expect Asus to have a similar procedure but do not know it. The only reason for the vendor recovery backup is if you may sell or give away system and want it back to like new without any of your data.

Are you booting installer in UEFI or BIOS boot mode? How you boot is then how it installs, and since Windows is UEFI, you really want Xubuntu in UEFI mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

You may also have some issues with nVidia, what model? And what model Intel? Haswell or Broadwell?
My older nVidia cards on my Desktop always needed nomodeset boot parameter. But you may have dual video or may be able to set in UEFI which video is used for booting. Intel may need one type of boot parameter where nVidia needs a different one. Live installer is probably just using a VESA video mode, but once installed it will want to use a different mode. But 15.04 has a lot of fixes from Intel to kernel, support software & video drivers that have finally made it into distributions.


 Bumblebee may not be required with nVidia Optimus, as that was before nVidia Prime.
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime was just nVidia, but now updated:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04](http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)


 Dual graphics nVidia GT840M
[http://ubuntuforums.org/showthread.php?t=2262882](http://ubuntuforums.org/showthread.php?t=2262882)
Dual graphics install nVidia prime and newer nVidia driver
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

---

### Post by Emma_Arthur on 2015-04-30
I'm booting the installer in UEFI and I think I went through as much doc as I could about the installation already. The troubleshooting will be done as I go along now, for what I can't foresee. But thanks a lot for your trouble aud all the info, I will come back to that when I have decided how to intall exactly.

Asus does not have a recovery partition of its own (unless it's that one on the SSD, i really can't tell), nothing on the website that I can find about either the cache function or the a recovery not through Windows. 

Still looking for an answer on the SSD partition, but I know some people have just formatted it and nothing happened, so maybe I'll just do that...

---

### Post by oldfred on 2015-04-30
Does UEFI see SSD as a separate drive?
Post this from live installer terminal:
sudo parted -l

I reference to a hybrid drive. Many with SSD had a small SSD soldered onto motherboard. 
I thought hybrid drives had more memory or SSD to speed up drive, but was not a separate drive from system view, but there maybe different versions for space on laptop consideration.

---

### Post by gmoutso on 2015-05-01
I have an ASUS TP500LN. In order to use the SSD, I first removed the caching software in MS windows. Simply remove the program ExpressCache by Condusiv technologies.

Instead of installing linux on the SSD, I used the hdd for the linux system and used the ssd as a cache by using lvm/lvmcache. In order to do that, I had to install ubuntu on an lvm. See [http://ubuntuforums.org/showthread.php?t=2247232](http://ubuntuforums.org/showthread.php?t=2247232)

---

### Post by Emma_Arthur on 2015-05-03
oldfred : the UEFI doesn't see the SSD as a boot option, but sees it in the SATA connexions as SATA 2. Both Windows and gparted see the SSD.
I managed to remove the ExpressCache in Windows and formated the SSD in gparted without a problem (at least not yet) + I added a new partition table (GPT) on the SSD. I didn't install anything yet, wanted to see if Windows booted OK (it does).

I will do the installation soon : do you think my computer can boot on the SSD even if it doesn't see it as a boot option yet ?
Would it be doable to have both / and /home on about 22go (the data would be on the HDD) ? My old computer with Xubuntu 14.04 took about 10go for both, but I don't want to run out of space...


gmoutso : thanks, I actually figured it out before you posted, but you confirm it ! I really want to use the SSD as / at least for Xubuntu, but I would be interested to know how fast your system is and how the cache works...

PS : sorry if I'm not always very clear, I'm struggling with English a bit...

---

### Post by oldfred on 2015-05-03
I have always recommended that each drive be bootable and have its own install and boot loader. Then data can be on any drive. And with UEFI an efi partition on every drive, only one per device/drive.

But with my UEFI desktop, I boot 14.04 from SSD. And I added a separate efi partition on hard drive so it could be configured to boot. But when I installed 15.04 to sdb and with Something Else told it to install to sdb (expecting it to use the efi partition in sdb) and watching install closely saw it even say installing to sdb. But it overwrote the ubuntu efi partition in sda. I had to manually copy files to sdb and either grub or my UEFI has issues with any boot files in sdb.

Or your system will install a new ubuntu folder in the ESP (efi system partition) on your hard drive. But that will boot grub/ubuntu on your SSD. Some UEFI will just work as you will have a new ubuntu entry in the UEFI boot menu. Some vendors particularly Sony & HP have modified UEFI to only boot an UEFI entry that says "Windows", but will boot a hard drive entry (bootx64.efi in efi partition) so we have work arounds. Other vendors like Acer require a UEFI password and you specifically authorizing another boot choice.

So you should just be able to install to SSD and we will see what works.

---

### Post by Emma_Arthur on 2015-05-03
Okay thanks so basically I just put an EFI on the SSD and see if it decides to boot from SSD or the windows EFI on the HDD?
Doing this tonight I think...

---

### Post by oldfred on 2015-05-03
If SSD is integrated in the hard drive, not physically separate, having the separate efi partition is probably not required. It will end up as unused space. 

If separate physically I would still add it, but it still may not normally be used. If you do create one then you may be able to use 100MB which is more the Windows standard. We otherwise suggest 300 to 500MB, but that is more for future use and on drives that have room for a larger efi partition.

---

### Post by Emma_Arthur on 2015-05-04
All done ! I installed root on the SSD + an EFI partition, as the disks are separate, but I think Xubuntu still uses Windows' EFI on the other disk... But well, whatever, it works.
Everything works with the dual-boot, haven't even had to do a boot-repair, both Xubuntu and Windows seem fine. I still have a couple problems, like my touchpad isn't recognized correctly, and I haven't checked what going on with the video yet, but they aren't part of this thread. I'm changing the title to solved. Thanks so much for your help !

---

### Post by oldfred on 2015-05-04
Glad it worked. :)

---

