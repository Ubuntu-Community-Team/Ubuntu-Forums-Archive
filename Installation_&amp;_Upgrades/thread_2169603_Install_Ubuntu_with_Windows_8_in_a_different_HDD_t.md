---
title: "Install Ubuntu with Windows 8 in a different HDD than Windows OS"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by carlos7 on 2013-08-22
Hi,

I recently bought a new computer, with pre-installed Windows 8. However, I need to install Ubuntu too (apparently, I cannot get some of the C++ libraries that I need to work under Windows 8 with Cygwin, and when I use them under Linux I usually do not have problems). And, yes, I have read all these issues with secure boot and UEFI... Since I do not want to destroy my new computer, I am just asking for advice. My computer has 2 hard drives, an SSD one, where Windows OS is installed, and a 1TB HDD, where I have my Data and Documents. I would like to install Ubuntu in a partition of the Data disk (I wouldn't like to touch the Windows OS one). I will try to follow these instructions,

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

but I just want to make sure that it will work if both systems are on different drives, before I try it. 

Just in case, I want also to say that I try to run Ubuntu, both 12.04 and 13.04, from a LiveCD, without installing it, and it did not work. I also disabled SecureBoot, but when I select on the screen "Try Ubuntu without installation", it does not go through and I have to shut down the computer manually.

Thanks!

---

### Post by oldfred on 2013-08-23
What computer? What video card/chip?
Did you also disable fast boot.

Several earlier users with UEFI installed on separate drives. And several with Ultrabooks that have 16 to 32GB SSD have just installed Ubuntu on SSD and turned off the Intel SRT.

More info on UEFI in general and two drive dual boot in link in my signature.

---

### Post by carlos7 on 2013-08-23
Thank you! So, there we go. The computer is a Dell XPS 8500, intel core i7-3770 3.40, 32 GB of RAM memory, graphic card Nvidia GTX 660. The hard drives are 256 GB SSD (with Windows 8 64 bit installed) and 2TB SATA, that I use for data/documents (currently I only use around 75 GB. I am not so much worried about it because everything is on my Dropbox). Also, yeah, I disabled fast boot. Any advice on what is the best I can do without running into problems is more than welcome!

---

### Post by oldfred on 2013-08-23
Another thread.
 Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

With two drives you need to make sure both are gpt partitioned and Ubuntu is installed in UEFI mode, not BIOS. And I would put an efi partition at the beginning of the hard drive even though system will probably use just the efi partition on the SSD to boot. I like to have system configured to boot from the MBR if BIOS or efi partition if UEFI on the same drive as the install (even if not curent default in UEFI/BIOS). Then system can boot if one drive fails. My goal is reliability or at least fallback capability, other may want speed or different configurations.

Not sure how current hard drive is configured or ease of adding new partition at beginning. But efi partition is supposed to be first on drive per UEFI spec. Windows often makes it second or even third, but it still is near beginning of drive. You then could have current data partition if you do not want to backup & reinstall later on drive. And then have Ubuntu partitions after that.

One suggestion for partitioning, but every user has own requirements and my own optimal partition scheme is usually outdated after a year or two of changes of what I may want to do.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

With 32GB of RAM you will not use swap but allocating a couple GB on large drives does not waste any space and may let system boot a bit faster as it looks for swap and has to timeout if none found. Only if something wicked happens would your system ever use swap.

You may also want to look at the options of mounting tmp folders/files in RAM to speed system. I do not do that and with installs to SSDs that is usually suggested to reduce writes to SSD, but it also speeds system as RAM is faster than SSD or a lot faster than hard drive.

---

### Post by carlos7 on 2013-08-23
Thanks. Anyway, I have tried almost everything, but I cannot pass from the GRUB, when I select "Try Ubuntu without installation", I just get a blank screen, and I have to shut down the computer manually. I guess that I will have to give up, I am not really a computer expert, and all those things look way too complicated, and I do not want to damage a quite expensive computer. Will have to wait until Ubuntu developers come up with something better...

---

### Post by ubfan1 on 2013-08-23
Did you try adding the "nomodeset" to the linux line with the "quiet splash", (or with a function key option when legacy booting)?  Your NVidia graphics probably require that.

---

### Post by carlos7 on 2013-08-23
Yup, I tried it. And I ended up with a command line, and I didn't know what else to do... I read something, but it was way too complicated

---

