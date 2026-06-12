---
title: "Upgrading to Ubuntu 14.04.1 LTS fails on Dell Inspiron 3542"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by yahya4 on 2014-10-13
Hello community members.

I recently bought Dell Inspiron 3542, which came with ubuntu preinstalled. That was the whole point of buying it anyhow cuz i wanna shift to open source completely. However, when I try to upgrade the installed version (12 i believe) to the latest LTS (14.04), after mutliple errors the installer quits and the final displayed messege says that it is a third part linux installation and is not supported. For support, I should uninstall this distro and install the official one. So please advise: should I install a fresh copy of Ubuntu 14? Or else, what should I do to fix the problem?

Also, I wanna setup dual boot on my laptop. So would it be better to first install windows and then a fresh copy of Ubuntu?

BTW, this is a new, out of the box machine by dell and nothing has been tempered with.

Thank you all for your support for open source. I believe this is the future of the cyber world.

Regards ):P

---

### Post by TheFu on 2014-10-13
Yes, install Windows first. Most Linux install guides will work that way and I've never, ever, seen a Windows guide assume Linux. I haven't dual booted in years - virtual machines are much more convenient and on a fast system with enough RAM and CPU, there isn't much lost by using it. It is also less risky for disk partitions.

Whether you should install 14.04 is a completely different question. Newer is NOT always better and 12.04 has a few years of support, so I'd stay with that unless you absolutely need something newer.  Plus it is unclear about your current skill level with Linux, so waiting as you gain more knowledge could be smart.  Installing any OS is a non-trivial thing.

If you can, perhaps finding a local installfest would be helpful? Then there are lots of experienced people to help. Most LUGs will be willing to help too.

I've had a few dell machines over the years. Most things work, but I don't know anything about that specific model and sometimes a little extra effort is necessary to get sound or wifi working. I assume these will not "just work" immediately post-install, so be prepared to use wired ethernet to avoid disappointment.

---

### Post by yahya4 on 2014-10-13
Thank you for your quick reply sir. Much appreciated. 

My skill level with linux is that of a newbie. I have worked on windows all my life. Consequently, I wanted to have a dual boot on my laptop so I could continue my work on windows as i learn linux along the way. Plus since I do a lot of graphics designing, there will always be the learning curve of moving away from adobe cs to open source alternatives.

However, I think your advice is sound. I have already tried installing ubuntu and windows on one of my desktop computers which turned out to be a disaster with one of my partitions rendered unsuable (or thats what i think as yet. i have another thread posted about that if you are interested: [http://ubuntuforums.org/showthread.php?t=2247966](http://ubuntuforums.org/showthread.php?t=2247966))

So i am confused right now. I guess i'd leave the laptop alone as is for now and not experiment with it. But doing so would definitely add to my migration time to linux and open source.

Btw sir, I live in Pakistan. There aint no installfests around here no matter how much i'd like one to take place :)

Thank you for your time once again. 

Regards :)

---

### Post by TheFu on 2014-10-13
Google found an Ubuntu Pakistan group. Perhaps they can help?

Windows has warped your mind for Linux.  80% of the OS is different, even if it seems similar.
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) tries to explain the differences.  Mainly - don't look to download programs and run "setup.exe" - always, always, always use the package manager to install, update, and remove programs.

Linux desktops actually need maintenance. [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) explains. Don't just leave it running without doing these things weekly or monthly (depends on your risk factors).

And using only the GUI is a mistake, IMHO. Other people may say it is fine, but I strongly believe it is extremely limiting for the power of Linux/UNIX systems.  There is a great introduction to Linux book - FREE - [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) get the PDF.  There are also [GUI Books]("http://ubuntuguide.org/"), if you want that, just know that GUIs in Linux tend to provide 40%-80% of the capability of the CLI/shell method.  Don't forget about help.ubuntu.com - lots of reading. Lots of effort to gain understanding.

Learning the GUI means dealing with changes every 1-2 yrs.
Learning the shell/CLI means 95% of things work the same for 20+ yrs. I'm using the same CLI knowledge today from 1993.

---

### Post by oldfred on 2014-10-13
Slightly different model. But Dell's seem to be very similar even across the lower end & very highend models, just options & upgrades of hardware are different.

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)


There was some discussion of sputnik which I knew nothing about. But it is some Linux updates for 12.04 for Dell hardware to work or work better, supposed all those are in 14.04.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by yahya4 on 2014-10-14
> **TheFu said:**
> Google found an Ubuntu Pakistan group. Perhaps they can help?

Windows has warped your mind for Linux.  80% of the OS is different, even if it seems similar.
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) tries to explain the differences.  Mainly - don't look to download programs and run "setup.exe" - always, always, always use the package manager to install, update, and remove programs.

Linux desktops actually need maintenance. [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) explains. Don't just leave it running without doing these things weekly or monthly (depends on your risk factors).

And using only the GUI is a mistake, IMHO. Other people may say it is fine, but I strongly believe it is extremely limiting for the power of Linux/UNIX systems.  There is a great introduction to Linux book - FREE - [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) get the PDF.  There are also [GUI Books]("http://ubuntuguide.org/"), if you want that, just know that GUIs in Linux tend to provide 40%-80% of the capability of the CLI/shell method.  Don't forget about help.ubuntu.com - lots of reading. Lots of effort to gain understanding.

Learning the GUI means dealing with changes every 1-2 yrs.
Learning the shell/CLI means 95% of things work the same for 20+ yrs. I'm using the same CLI knowledge today from 1993.

Thank you for your reply sir. I read through the article that you linked to in the first paragraph. However, the link you have provided on maintenance doesnt work ([http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint)). Can you please point me to another source?

I do understand that CLI is actually what makes linux such a powerful os/kernel... and i intend on learning it as i go along. I have downloaded the book that you have pointed to and would like to thank you for pointing me to it.

I'll definitely bee seeking more guidance from you guys as i progress in linux.

And oh by the way, i joined the Pak Linux Community that you pointed out :D

EDIT: Never mind about the link. It works now :)

> **oldfred said:**
> Slightly different model. But Dell's seem to be very similar even across the lower end & very highend models, just options & upgrades of hardware are different.

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)


There was some discussion of sputnik which I knew nothing about. But it is some Linux updates for 12.04 for Dell hardware to work or work better, supposed all those are in 14.04.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

Thank you for your reply. I have read through the links that you have provided (took me a whole day but i made it a point to read through them all :D). However i am a little confused, and would like a bit of your time if you could guide me in this regard. I know sometimes there arent any straightforward answers and much is left to various factors including one's inclinations, skill level and the amount of time one decides to dedicate to something. My confused questions to you, however, would be:


[LIST=1]
[*]when all is said and done, would you rather advise me to keep the same version on my laptop or should i setup a dual boot first installing windows and then ubuntu's latest version? i do not own win8 so i'll be installing windows 7 64bit. the reason for this question is that there are a lot of different posts, as you have shown, that discuss issues with ubuntu's detecting/running some hardware on dell. right now, every thing works fine on my laptop. so if i decide to setup that dual boot, would i be then finding it problematic to smoothly run everything on my laptop in linux?
[*]what would be the ideal way of going about learning linux? do you advise on reading a book, going through a video tutorial or learning with hit and miss methodology of instant immersion? please don't say all of the above :D
[/LIST]

Thank you for your time. Looking forward to your reply :)

---

### Post by TheFu on 2014-10-14
> do you advise on reading a book, going through a video tutorial or learning with hit and miss methodology of instant immersion? please don't say all of the above
I'm not oldfred, so all of the above. ;)

There is at least 250+ yrs of knowledge to learn - so using a mix of techniques really is the best answer. Some things you need to know TODAY, but without some background (like that book provides), you'll waste days with relatively simple things.

Looks like Pakistan, India and Thailand eash block my blog now. The older version of that article is also on lifehacker.com. Any idea why? Is there something offensive that my cultural bias isn't able to recognize?

The first link isn't a big deal, until you have been trying to do things "the Windows way" and it doesn't work, then get frustrated. Better to spend the 5 min to read it, catch the important things now and never worry about it again.

---

### Post by oldfred on 2014-10-14
I normally suggest dual boot, especially if not real familar with Linux. Linux is not Windows. Many try to immediately convert but find one app or game they have to have that only runs in Windows. It took me several years before I could give up that one app.

Is Windows installed in BIOS or UEFI boot mode.

Normal installs of Windows 7 seem to be BIOS mode and convert a gpt drive to MBR(msdos) but does it incorrectly and leads to more issues.

But you can convert Windows 7 installer to UEFI boot if desired.
Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
But Ubuntu will boot in either BIOS or UEFI from gpt drives and sometimes leads to boot confusion as Windows 8 pre-installed is always UEFI with gpt partitioning. 
Best just to have both sytems in same boot mode, even if hardware supports both UEFI or BIOS.

I bought a book to learn basics, but all info is on Internet. I then also looked up many of my issues with Google but found most answers here in the forum. So I joined forum and think I learned more just by trying to help users on a few issues I know enough to be dangerous on, and read up on other issues I am interested in. 
Or just use system, ask for help in forum when you get totally stuck. Often searches in forum will find most issues already answered.

---

### Post by yahya4 on 2014-10-18
Sorry for not being able to reply earlier. Internet in Pakistan is never a definitive thing. Sometimes we don't get to connect to internet for days due to different reasons :(

> **TheFu said:**
> I'm not oldfred, so all of the above. ;)

There is at least 250+ yrs of knowledge to learn - so using a mix of techniques really is the best answer. Some things you need to know TODAY, but without some background (like that book provides), you'll waste days with relatively simple things.

Looks like Pakistan, India and Thailand eash block my blog now. The older version of that article is also on lifehacker.com. Any idea why? Is there something offensive that my cultural bias isn't able to recognize?

The first link isn't a big deal, until you have been trying to do things "the Windows way" and it doesn't work, then get frustrated. Better to spend the 5 min to read it, catch the important things now and never worry about it again.

I am sure it is all of the above :D

To answer your question, I don't think there is anything offensive in your blog posts. But since our govt. bans many Google products, I think your blog must have been a victim of the ip range blockade. 

I have studies the pages that you linked to and they helped. So thank you for pointing me to those once again :)

---

### Post by yahya4 on 2014-10-18
> **oldfred said:**
> I normally suggest dual boot, especially if not real familar with Linux. Linux is not Windows. Many try to immediately convert but find one app or game they have to have that only runs in Windows. It took me several years before I could give up that one app.

Is Windows installed in BIOS or UEFI boot mode.

Normal installs of Windows 7 seem to be BIOS mode and convert a gpt drive to MBR(msdos) but does it incorrectly and leads to more issues.

But you can convert Windows 7 installer to UEFI boot if desired.
Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
But Ubuntu will boot in either BIOS or UEFI from gpt drives and sometimes leads to boot confusion as Windows 8 pre-installed is always UEFI with gpt partitioning. 
Best just to have both sytems in same boot mode, even if hardware supports both UEFI or BIOS.

I bought a book to learn basics, but all info is on Internet. I then also looked up many of my issues with Google but found most answers here in the forum. So I joined forum and think I learned more just by trying to help users on a few issues I know enough to be dangerous on, and read up on other issues I am interested in. 
Or just use system, ask for help in forum when you get totally stuck. Often searches in forum will find most issues already answered.

So what I gather from your post sir, is that I should first install Windows and then reinstall ubuntu. I'll do as you suggest. Still have to look into the matter concerning uefi boot and the bios. I'll try to figure that out and would ask you for any help if required. 

Thank you for your time, you have been very helpful :)

---

### Post by yahya4 on 2014-10-18
After thinking a lot on the subject, I am going to keep the preinstalled ubuntu 12 on my laptop as i don't wanna mess around with it. I'll keep a dual boot on my desktop, with windows 7 and ubuntu so i could goto my desktop if i wanna use windows. So my question now is, how do i install the updates, as it always gives me errors when i try to install updates or try to upgrade to ubuntu 14 trusty...

Also, the graphics on my machine (Dell inspiron 3542) show as unknown. How to fix that problem.

Awaiting your reply. Thanks a lot in advance. :)

---

### Post by oldfred on 2014-10-18
I do not know specifics on your Dell.
Some possibly similar systems, different models of Dells are very similar install wise, just different hardware options:

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by yahya4 on 2014-10-18
> **oldfred said:**
> I do not know specifics on your Dell.
Some possibly similar systems, different models of Dells are very similar install wise, just different hardware options:

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)


Thank you for the reply. Very helpful links. Finally able to upgrade my ubuntu. Upgrade in process right now :D Will report back with updates

---

### Post by yahya4 on 2014-10-18
The upgrading process froze in the middle of installing the updates... i waited for over an hour but nothing happened so had to force hot restart. Now it boots but ubuntu doesnt start. So i guess ill have to setup that dual boot we talked about earlier after all :(

---

### Post by oldfred on 2014-10-18
Did you have any ppas or proprietary video drivers? 
Those always cause issues and must be removed before an update.

---

### Post by yahya4 on 2014-10-18
i dont think i had any of those. it was just as it came. i didnt alter/install anything at all. primary reason being, i dont know how to use ubuntu to install or uninstall apps/drivers :)

---

### Post by oldfred on 2014-10-19
Are you still trying to upgrade the pre- installed version? That probably did have ppa as Dell needed sputnik which was many changes to 12.04. Supposedly all those changes are by default in 14.04, so a Dell should work with 14.04 without issues.

Did you back up all you data and make a list of installed apps that you installed before your upgrade? Then reinstall would be easy as you can just restore /home and reinstall apps.

But if re-installing only use Something Else. 
Is system UEFI with gpt partitioning or BIOS with MBR partitioning?

---

### Post by yahya4 on 2014-10-19
> **oldfred said:**
> Are you still trying to upgrade the pre- installed version? That probably did have ppa as Dell needed sputnik which was many changes to 12.04. Supposedly all those changes are by default in 14.04, so a Dell should work with 14.04 without issues.

Did you back up all you data and make a list of installed apps that you installed before your upgrade? Then reinstall would be easy as you can just restore /home and reinstall apps.

But if re-installing only use Something Else. 
Is system UEFI with gpt partitioning or BIOS with MBR partitioning?

No sir, I am trying to setup dual boot now. My laptop has both UEFI and Bios (Legacy) option and i am using the later (BIOS) option. 

I tried setting up dual boot on my desktop but now i am stuck with Win7 not booting at all. Here is what I did, following the install guide here [http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

1. I booted the system with Win7 dvd. Then deleted all partitions that were created by ubuntu previously. This gave me an unallocated total space of 80 gb. I created a primary partition of 25 gb. Windows created another partition before it of 100 gb reserved for system. I left the rest of the space unallocated.

2. I installed windows7 on this 25gb primary partition. It installed successfully.

3. Then i booted the system with Ubuntu 14 dvd and went into the live session. I started gparted and made an extended partition of the unallocated space. Then i created three logical partitions in this extended partition: 15gb, 4gb (Installed RAM is 2gb), 34 gb. Then i exited the gparted.

4. I clicked on install and chose 'something else' when prompted. There i assigned the 15gb partition to root, the 4gb parition to swap and the rest to /home. It also asked me where i wanted to install grub, and i chose the sda1 (where the windows boot record was originally saved), because the guide mentioned above said i needed to use grub to boot both linux and windows.

So Ubuntu was installed successfully. When restarted I saw the options of booting Ubuntu or Win7. 

**Now the problem is, ubuntu boots up successfully. But when i select win7, nothing happens and after a momentary blank screen, i am presented again with the dual boot screen.**

I have tried to search the forums but couldnt get what i needed. Please advise, what did i do wrong.

Thanks a bunch.

---

### Post by oldfred on 2014-10-20
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair cannot fix most Windows issues but the summary report may tell us what the issue is.

---

### Post by yahya4 on 2014-10-21
> **oldfred said:**
> Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair cannot fix most Windows issues but the summary report may tell us what the issue is.

Here you go sir:

[http://paste.ubuntu.com/8616668/plain/](http://paste.ubuntu.com/8616668/plain/)

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 62513496 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1117064 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    53,848,063    53,641,216   7 NTFS / exFAT / HPFS
/dev/sda3          53,849,878   156,232,124   102,382,247   5 Extended
/dev/sda5          53,849,880    86,622,479    32,772,600  83 Linux
/dev/sda6          86,622,543    94,815,629     8,193,087  82 Linux swap / Solaris
/dev/sda7          94,815,693   156,232,124    61,416,432  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            128     7,864,319     7,864,192   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        20502A5F502A3C42                       ntfs       
/dev/sda2        86642DA1642D9549                       ntfs       
/dev/sda5        f165afa0-ec69-4f38-af78-e88a17d2a56e   ext4       LRoot
/dev/sda6        5a8ba791-e0af-4319-8297-4f9592c95d92   swap       
/dev/sda7        166697f8-0e86-4679-9e59-d64a5555fe51   ext4       LHome
/dev/sdb1        F26E-8505                              vfat       ANGEL

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f165afa0-ec69-4f38-af78-e88a17d2a56e
else
  search --no-floppy --fs-uuid --set=root f165afa0-ec69-4f38-af78-e88a17d2a56e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f165afa0-ec69-4f38-af78-e88a17d2a56e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f165afa0-ec69-4f38-af78-e88a17d2a56e
    else
      search --no-floppy --fs-uuid --set=root f165afa0-ec69-4f38-af78-e88a17d2a56e
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=f165afa0-ec69-4f38-af78-e88a17d2a56e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f165afa0-ec69-4f38-af78-e88a17d2a56e' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-f165afa0-ec69-4f38-af78-e88a17d2a56e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f165afa0-ec69-4f38-af78-e88a17d2a56e
        else
          search --no-floppy --fs-uuid --set=root f165afa0-ec69-4f38-af78-e88a17d2a56e
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=f165afa0-ec69-4f38-af78-e88a17d2a56e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-f165afa0-ec69-4f38-af78-e88a17d2a56e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f165afa0-ec69-4f38-af78-e88a17d2a56e
        else
          search --no-floppy --fs-uuid --set=root f165afa0-ec69-4f38-af78-e88a17d2a56e
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=f165afa0-ec69-4f38-af78-e88a17d2a56e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f165afa0-ec69-4f38-af78-e88a17d2a56e
    else
      search --no-floppy --fs-uuid --set=root f165afa0-ec69-4f38-af78-e88a17d2a56e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  f165afa0-ec69-4f38-af78-e88a17d2a56e
    else
      search --no-floppy --fs-uuid --set=root f165afa0-ec69-4f38-af78-e88a17d2a56e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-20502A5F502A3C42' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  20502A5F502A3C42
    else
      search --no-floppy --fs-uuid --set=root 20502A5F502A3C42
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=f165afa0-ec69-4f38-af78-e88a17d2a56e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=166697f8-0e86-4679-9e59-d64a5555fe51 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=5a8ba791-e0af-4319-8297-4f9592c95d92 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.808803558 = 32.006959104   boot/grub/grub.cfg                             1
  29.808784485 = 32.006938624   boot/grub/i386-pc/core.img                     1
  26.722106934 = 28.692643840   boot/vmlinuz-3.13.0-32-generic                 1
  26.722106934 = 28.692643840   vmlinuz                                        1
  40.771373749 = 43.777929216   boot/initrd.img-3.13.0-32-generic              3
  40.771373749 = 43.777929216   initrd.img                                     3

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^32bit session
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^32bit session (failsafe)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  b8 3c c0 3c d8 3c dc 3c  f4 3c 04 3d 08 3d 0c 3d  |.<.<.<.<.<.=.=.=|
00000010  14 3d 2c 3d 3c 3d 40 3d  50 3d 54 3d 58 3d 5c 3d  |.=,=<=@=P=T=X=\=|
00000020  60 3d 68 3d 80 3d 84 3d  9c 3d ac 3d b0 3d b4 3d  |`=h=.=.=.=.=.=.=|
00000030  b8 3d c0 3d d8 3d e8 3d  ec 3d f0 3d 04 3e 08 3e  |.=.=.=.=.=.=.>.>|
00000040  18 3e 1c 3e 20 3e 24 3e  28 3e 30 3e 48 3e 4c 3e  |.>.> >$>(>0>H>L>|
00000050  64 3e 74 3e 78 3e 7c 3e  80 3e 88 3e a0 3e b0 3e  |d>t>x>|>.>.>.>.>|
00000060  b4 3e b8 3e cc 3e d0 3e  e0 3e e4 3e e8 3e ec 3e  |.>.>.>.>.>.>.>.>|
00000070  f0 3e f4 3e fc 3e 14 3f  18 3f 30 3f 34 3f 4c 3f  |.>.>.>.?.?0?4?L?|
00000080  5c 3f 60 3f 70 3f 74 3f  84 3f 88 3f 98 3f 9c 3f  |\?`?p?t?.?.?.?.?|
00000090  a0 3f a8 3f c0 3f d0 3f  d4 3f e4 3f e8 3f ec 3f  |.?.?.?.?.?.?.?.?|
000000a0  f0 3f f4 3f f8 3f fc 3f  00 90 07 00 d4 00 00 00  |.?.?.?.?........|
000000b0  04 30 1c 30 20 30 38 30  48 30 4c 30 50 30 54 30  |.0.0 080H0L0P0T0|
000000c0  58 30 5c 30 70 30 74 30  84 30 88 30 8c 30 94 30  |X0\0p0t0.0.0.0.0|
000000d0  ac 30 bc 30 c0 30 d0 30  d4 30 d8 30 dc 30 e0 30  |.0.0.0.0.0.0.0.0|
000000e0  e4 30 e8 30 f0 30 08 31  0c 31 24 31 34 31 38 31  |.0.0.0.1.1$14181|
000000f0  3c 31 40 31 44 31 48 31  5c 31 60 31 70 31 74 31  |<1@1D1H1\1`1p1t1|
00000100  84 31 88 31 8c 31 90 31  98 31 b0 31 b4 31 cc 31  |.1.1.1.1.1.1.1.1|
00000110  dc 31 e0 31 f0 31 f4 31  04 32 08 32 10 32 28 32  |.1.1.1.1.2.2.2(2|
00000120  e4 3c ec 3c f4 3c 10 3d  18 3d 3c 3d 48 3d 50 3d  |.<.<.<.=.=<=H=P=|
00000130  70 3d 78 3d 80 3d 9c 3d  a4 3d c8 3d d4 3d dc 3d  |p=x=.=.=.=.=.=.=|
00000140  f4 3d fc 3d 20 3e 2c 3e  34 3e 4c 3e 54 3e 78 3e  |.=.= >,>4>L>T>x>|
00000150  84 3e 8c 3e a4 3e ac 3e  d0 3e dc 3e e4 3e fc 3e  |.>.>.>.>.>.>.>.>|
00000160  04 3f 18 3f 28 3f 3c 3f  44 3f 5c 3f 68 3f 88 3f  |.?.?(?<?D?\?h?.?|
00000170  90 3f 98 3f a4 3f c4 3f  cc 3f d8 3f 00 a0 07 00  |.?.?.?.?.?.?....|
00000180  00 02 00 00 00 30 14 30  20 30 28 30 40 30 48 30  |.....0.0 0(0@0H0|
00000190  50 30 58 30 70 30 78 30  84 30 a4 30 b0 30 d0 30  |P0X0p0x0.0.0.0.0|
000001a0  dc 30 fc 30 08 31 28 31  30 31 3c 31 5c 31 68 31  |.0.0.1(101<1\1h1|
000001b0  88 31 94 31 b4 31 c0 31  e0 31 ec 31 0c 32 00 fe  |.1.1.1.1.1.1.2..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 f8 11 f4 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff fa 11  f4 01 7e 04 7d 00 00 00  |..........~.}...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/2506/mounts) leaked on lvscan invocation. Parent PID 10673: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-10-21__21h09 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/2506/mounts) leaked on lvs invocation. Parent PID 4128: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 24avr2013, raring, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 14.04.1 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="20502A5F502A3C42" TYPE="ntfs"
/dev/sda2: UUID="86642DA1642D9549" TYPE="ntfs"
/dev/sda5: LABEL="LRoot" UUID="f165afa0-ec69-4f38-af78-e88a17d2a56e" TYPE="ext4"
/dev/sda6: UUID="5a8ba791-e0af-4319-8297-4f9592c95d92" TYPE="swap"
/dev/sda7: LABEL="LHome" UUID="166697f8-0e86-4679-9e59-d64a5555fe51" TYPE="ext4"
/dev/sdb1: SEC_TYPE="msdos" LABEL="ANGEL" UUID="F26E-8505" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root        4096 Jul 22 22:15 grub.d
total 76
-rwxr-xr-x 1 root root  9424 May 15 19:01 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:01 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:01 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15 19:01 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:01 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:01 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:01 41_custom
-rw-r--r-- 1 root root   483 May 15 19:01 README


=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sda7    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda7.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HDS728080PLA380 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  106MB   105MB   primary   ntfs            boot
2      106MB   27.6GB  27.5GB  primary   ntfs
3      27.6GB  80.0GB  52.4GB  extended
5      27.6GB  44.4GB  16.8GB  logical   ext4
6      44.4GB  48.5GB  4195MB  logical   linux-swap(v1)
7      48.5GB  80.0GB  31.4GB  logical   ext4


Model: Corsair Flash Voyager (scsi)
Disk /dev/sdb: 4027MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      65.5kB  4027MB  4026MB  primary  fat16        boot

=================== parted -lm:

BYT;
/dev/sda:80.0GB:scsi:512:512:msdos:ATA HDS728080PLA380;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:27.6GB:27.5GB:ntfs::;
3:27.6GB:80.0GB:52.4GB:::;
5:27.6GB:44.4GB:16.8GB:ext4::;
6:44.4GB:48.5GB:4195MB:linux-swap(v1)::;
7:48.5GB:80.0GB:31.4GB:ext4::;

BYT;
/dev/sdb:4027MB:scsi:512:512:msdos:Corsair Flash Voyager;
1:65.5kB:4027MB:4026MB:fat16::boot;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart alarm ashmem autofs binder block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri dvd ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  42 3c 2a 50 5f 2a 50 20  |........B<*P_*P |
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 80 58 e1 b9 03  |.....3......X...|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  f6 07 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |...t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..|f..f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f...D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d 5a 84 d2 0f  |...p.v....s.Z...|
000000f0  83 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  73 73 69 6e 67 00 0d 0a  |...<.u..ssing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 7f 32 03 00 00 00 00  |..........2.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  49 95 2d 64 a1 2d 64 86  |........I.-d.-d.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1004M   20M  985M   2% /
udev           devtmpfs   989M   12K  989M   1% /dev
tmpfs          tmpfs      201M  732K  201M   1% /run
/dev/sdb1      vfat       3.8G  546M  3.3G  15% /cdrom
/dev/loop0     squashfs   431M  431M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1004M  8.0K 1004M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs     1004M     0 1004M   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user
/dev/sda1      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     26G   11G   16G  40% /mnt/boot-sav/sda2
/dev/sda5      ext4        16G  3.0G   12G  21% /mnt/boot-sav/sda5
/dev/sda7      ext4        29G   47M   28G   1% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e44f4

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    53848063    26820608    7  HPFS/NTFS/exFAT
/dev/sda3        53849878   156232124    51191123+   5  Extended
/dev/sda5        53849880    86622479    16386300   83  Linux
/dev/sda6        86622543    94815629     4096543+  82  Linux swap / Solaris
/dev/sda7        94815693   156232124    30708216   83  Linux

Disk /dev/sdb: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128     7864319     3932096    6  FAT16



=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda5 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
```

---

### Post by yahya4 on 2014-10-21
I just used the recommended setting for boot-repair and it repaired the boot issue. However, now i am presented with two options to boot windows. One is from sda1 and the second from sda2. Selecting to boot win7 from sda1 fails, however the windows does boot with sda2 option selected.

Can you please tell me why that is, and what should i do next time i setup the dual boot so this doesnt replicate?

Thank you again for your time. Boot-repair did solve the issue :)

EDIT: the boo-repair report after solving the issue...

[http://paste.ubuntu.com/8616784/](http://paste.ubuntu.com/8616784/)

---

### Post by oldfred on 2014-10-21
Just need links. If posting long text please use code tags. You can easily add code tags using the # in the advanced editor.

Boot-Repair did not really fix your issue, but because many users do not know teh 100MB boot partition is essential to Windows booting, Boot-Repair copies bootmgr & BCD back to main install. Grub then finds both copies of bootmgr & BCD and adds boot options for both.

But you installed grub to the partition boot sector or PBR of sda1. All NTFS partitions have to have Windows boot info or Windows info in the NTFS PBR. While tools may say your grub is ok as it is correctly installed to a PBR, it never is correct to have grub in a NTFS partition's PBR.
And with grub in PBR most Windows tools will not fix it. You can use testdisk and from Windows bootsect.exe. 

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

 Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by yahya4 on 2014-10-21
Thank you for the instructions about pasting long text... i'll keep that in mind.

And thank you for the links. I went through them quickly. Those helped. Just a little question: Grub should be installed on sda2 (the primary windows installation partition) instead of sda1 then?

---

### Post by oldfred on 2014-10-21
You never install grub to a NTFS partition. And almost never to any partition.

Normally with BIOS/MBR you install grub to the MBR or first sector (sector 0) of the hard drive. BIOS only boots from a MBR.  During install or installs you specify a drive like sda, sdb etc, not partitions like sda1 or sda2.

And grub2 is not supposed to be installed to a partition as it has to convert to blocklists as it does not really fit. And block lists are hard coded address, so grub update may move grub files on drive and address it looks for is then wrong. You then have to reinstall grub.

---

### Post by yahya4 on 2014-10-21
oh alright. thank you for clearing that up. so i'll just select the default option that ubuntu gives me where it wants to install grub. hopefully that helps. gonna try and setup the dual boot on my laptop now.

thank you for all your help once again :D

---

