---
title: "Booting issues"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by rhunt915 on 2016-11-10
Hello,
I am in the process of setting up my home server with Ubuntu 16.04.1 LTS, and experiencing trouble.  When I try to boot my system, I see the GRUB bootloader, but when Ubuntu is selected, my screen goes black, and no signal is received by my monitor.  I previous iterations of trying to fix this, I have updated the intel drivers (I'm not using a graphics card) and the xserver, neither of which seemed to fix this issue.  My boot drive is a 120GB SSD, and am using a Gigabyte MB (GA-H170-D3HP).  I have tried to do the default install (with EFI, ext4 and swap partitions), I have tried using the whole drive as an ext4, I have created a 200 MB EFI partition, and none of these work.  For a while, I was able to get the system to reliably boot with the whole drive as an ext4, but after I added a dvd drive, it boots to a black screen again.  

I have tried boot-repair 3 times, with the most recent returning the url: [paste2.org/8M0hwd3F]("http://paste2.org/8M0hwd3F") 

The most recent version of boot-repair seemed to have done the most work, as I now see a 'Windows...' device in my boot options, where I have not before.

Could someone help me parse the output on paste2 to help me determine where my problem lives?

Thanks,

Kyle

---

### Post by oldfred on 2016-11-10
I have a Gigabyte Z170N-Gaming 5 and installed Ubuntu 16.04 (before release as I knew I needed newer version).
I did change some settings in UEFI and updated to newest UEFI from Gigabyte.
[https://ubuntuforums.org/showthread.php?t=2315007&page=2&p=13449024#post13449024](https://ubuntuforums.org/showthread.php?t=2315007&page=2&p=13449024#post13449024)

You now show mixed UEFI/BIOS with MBR(msdos) partitioning and gpt errors. Cannot be both MBR & gpt.
Best to stay with gpt partitioning whether you want UEFI or BIOS boot. Boot-Repair then can convert from UEFI to BIOS or vice-versa. But with MBR, you should only boot in BIOS mode. Windows only boots in BIOS mode from MBR and only in UEFI from gpt. 
How you boot install media is then how it installs.

I still add both the ESP - efi system partition and a bios_grub partition, but now have only used UEFI boot. But with bios_grub I could easily convert to BIOS boot.


These are my partitions on my other UEFI system. I typically have a small 25GB / (root) partition on SSD and then on HDD have large data partition and several other installs for testing.
[https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

Best to start over with gpt partitioning and UEFI install.
Usually black screen is video driver issue, but Intel normally just works.
What cable are you using HDMI, display port or other?

       gpt(GUID)) partitioning
Required for UEFI, and for drives over 2.2GB.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting. 

Several suggestions on partitioning.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk](http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk)

---

### Post by rhunt915 on 2016-11-10
Thanks!  I'll work to implement these this afternoon, and update the status as necessary.

Thanks again!

---

### Post by rhunt915 on 2016-11-10
Good afternoon,
I started fresh, even going so far as to delete the master boot record, just for good measure.  I used gpt, with the aforementioned partitioning scheme (500 mb for esp/boot, ~25 GB for /, rest for /home).  I elected not to use a swap partition, as I feel i have sufficient RAM, and plan to add more later on.  System still did not boot into the GUI, and inconsistently booted into GRUB.  I ran boot-repair again, and that generated [this]("http://paste2.org/IwP4Vet1").  

As far as the cable, etc.  I'm using an old VGA cable with no other adapter, that leads to a (admittedly large) samsung flatscreen tv.  

Also, if I am able to get to grub, and can select advanced options -> Linux 4.4.0-47-generic (recovery mode).  Then, I can select resume, and the system will boot into the GUI.  The GUI is a bit laggy, but seems pretty stable.

Thanks in advance,

Kyle

---

### Post by oldfred on 2016-11-10
This is mine which is virtually identical to yours and mine has worked without issue:
```
fred@Z170N:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1912] (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Gigabyte Technology Co., Ltd Skylake Integrated Graphics [1458:d000]
    Kernel driver in use: i915_bpo
```

But I am using a HDMI cable to a 23" HP monitor. I also had it connected to a TV for a short time until I bought new monitor.
Your vga out & vga cable may not match TV well, I might invest in a new cable.

Advanced options includes the nomodeset, but usually that is only required with nVidia or AMD.

---

### Post by rhunt915 on 2016-11-10
I agree.  Running the same command displays the same information.  As far as the physical connection between the tv and the computer goes, I think I disagree that the cable is the issue, since prior to adding the new dvd drive, I was able to successfully boot (and reboot) a number of times with no issues whatsoever.  

Is it possible that I have something marked incorrectly in my UEFI?  I have fast boot disabled, trusted platform disabled, I'm pretty sure I have the boot order right, but as there is no size information displayed, only the drive name and total size, I can't be certain.  Is there anything else I should check?  Is there a better tutorial of the UEFI than the MB instruction booklet?

Thanks again for all of your time.

Kind regards,

Kyle

---

### Post by oldfred on 2016-11-10
Have you looked at the link in my signature? :)

I have found drive order important. Both my old BIOS and my newer UEFI systems.
My old BIOS I had skipped a SATA port. Flash drive would be sdf when plugged in and then sdb when I rebooted with it still in. That caused me issues if I did not pay attention.
New UEFI system was similar. I had two drives, but plugged DVD inbetween them. Second drive was sdb, but in grub has hd2, not the hd1 it should have been. Moved DVD to higher port solved that.

Also UEFI forgets all entries saved in NVRAM when you disconnect a drive. Some UEFI find entries in ESP when new drive added or a cold boot, but some only look for Windows and usually the fallback or /EFI/Boot/bootx64.efi.  Best to check with efibootmgr before & after unplugging a drive and always back up ESP.

---

### Post by rhunt915 on 2016-11-11
After reading through some of the information provided from the link in your signature, I set the nomodeset flag in grub, and that seemed to do the trick.  To verify that was the issue, an not the uefi, I changed the sata port where the ssd connected, and rebooted.  System rebooted with no issues at all.  So, it seems as though the nomodeset flag was the answer, even though I am not running an AMD based system.

Thanks so much for your help!!  I will mark this thread as 'Solved'.

Thanks again,

Kyle

---

