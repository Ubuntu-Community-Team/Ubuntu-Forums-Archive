---
title: "How to safely install Ubuntu on external drive without corrupting Windows dual boot?"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by hwan on 2012-04-07
tl;dr: Installed Ubuntu to an external drive while internal Windows drives were disconnected. I plugged my internal drives back in and booted to Ubuntu on the external just fine. Then when I shutdown and unplugged the external drive my Windows dual boot loader was gone and files were corrupted. Is there any Windows safe way to run Ubuntu from an external drive without always unplugging the internal drives first? 


 Background (skip down, if you like):  

I've dabbled with a number of different distros over the years on hardware and in VMs, but I got myself into trouble the other day. 

I have a dual-boot Windows 7 and XP system, with both OS installs in different partitions on the same drive. The boot loader is an older version of GRUB4DOS and set up with EasyBCD. It's also set up to hide the Windows 7 partitions when booted into XP, so XP doesn't mangle the Windows 7 drives with system recovery and other conflicts. 

I already have Linux Mint running in VirtualBox, but I wanted a new install of Ubuntu 11.10 running on hardware. After looking into Wubi or repartitioning and adding a third OS to my internal drive, I decided to try installing Ubuntu 11.10 to an external drive. 


Issues: 

I started by unplugging all my internal HDs (Windows OS and data drives), then connected my external USB drive and booted to the Ubuntu 11.10 live cd installer. I followed [this guide]("http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/") almost exactly, setting up the external drive with 4 partitions: /boot, /, /swap, /ntfs. 

Everything went fine, then I took out the cd and booted into Ubuntu 11.10 from the external drive. I did some updates, configuration and installed a few applications. 

After that, I plugged my internal Windows drives back in and tried to boot Ubuntu from USB. Again, it seemed to work find and I could see all my internal Windows drives from Ubuntu. I didn't touch the Windows OS drives, but I did open a couple files from the Windows data drive. 

On one of the reboots into Ubuntu on USB, I noticed the Ubuntu/Debian GRUB loader had added my two Windows systems 7 and XP to the GRUB boot options. I didn't think it would be a problem, since I had a dedicated boot partition on the external USB drive. 

Anyway, once I finished up with Ubuntu. I shut it down and unplugged the external USB drive. Then I tried to boot back into my Windows machine. 

First thing I noticed was that my old GRUB4DOS boot loader was completely gone. The system started to load the Windows XP login screen, then I got all sorts of errors about corrupted files and corrupted \$Secure on multiple drives. I couldn't get past those errors to login, so I shut down and grabbed some recovery boot cds. 

The Windows 7 Recovery disc gui failed, but I was able to do some repairs from the command prompt. 

That allowed me to boot into my internal drive running Windows 7, but on boot Windows 7 detected many errors and ran CHKDISK trying to repair a lot of corrupted files and security settings (apparently only on the XP partitions). After some more work and system and disk scans of both internal OSes I think I have got things mostly back the way they were before my Ubuntu experiment. I say mostly, because I have seen at least one unexplained new glitch in XP. 


Questions: 

1) Why did this happen? (Besides my ignorance) When I booted Ubuntu from the external USB drive, why did it decide to rewrite my internal drives OS bootloaders and corrupt many other Windows XP system drive files, without notice and without confirming whether or not I wanted to change the existing MBR/boot loader for those drives? 

2) Are there any settings or configuration files I can edit so I can run Ubuntu from an external USB drive without it ruining the existing boot setup on my internal drives? 

3) Is unplugging all my internal drives every time the only option to safely run Ubuntu from an external USB drive? 

Most of the time, I won't have my Ubuntu USB drive connected when running my either of my internal Windows dual boot systems. So, I'm not sure that I want to try adding the Ubuntu external install to my internal GRUB4DOS Windows boot loader (if that's even possible). 


Thanks for your help.

---

### Post by Herman on 2012-04-08
I'm sorry to read of your unfortunate run of bad luck. I can only guess that you might be the victim of some kind of hoax or a practical joke, or else maybe you entered some commands you didn't understand and have since forgotten about.
Or maybe by coincidence something unrelated happens to be going wrong with your hardware at the same time as you decided to begin your Ubuntu experience, so it appears to you as if it has something to do with Ubuntu. It's quite understandable for a person to think that way but it would be a shame to be too quick to jump to conclusions and blame Ubuntu.

I have been dual booting Ubuntu with various kinds of Windows since the first Ubuntu came out. I started off dual booting Windows 98 and even Windows 95 computers with Ubuntu 4.10 Warty Warthog. Back in those days we weren't able to write to NTFS. (EDIT: For PCs with Windows XP). Full NTFS support first became standard in Ubuntu with Ubuntu 7.10 Gutsy Gibbon back in October 2007. The have been very few reports of NTFS file system damage since then. 

Over the years I have tried just about every kind of disk partitioning and boot loader installing experiment I can think of and set up a lot of dual boots. Very often I have even deliberately set out to destroy things so I could find out what happens and learn how to set things right again. Ubuntu has never done anything like the kind of things you're describing to any computer I have ever been in control of except when I have told it to.
Well, maybe some of the Ubuntu installers have been a little tricky with where they hide the options for where to install GRUB, but that's about as far as it goes. As long as you follow a good install how-to you'd be okay. You did follow a good how-to and you got through that part okay so I don't know what could have gone wrong. A competent person under normal circumstances shouldn't need to go unplugging drives even to install Ubuntu, much less to run Ubuntu normally. Whatever could have happened to bring about the circumstances you're describing is unusual to say the least.

I hope you stick around and keep on trying Ubuntu out. It's really a great operating system, (in my opinion it's the best), and in time you will come to trust Ubuntu and see it for the great operating system it is. :)

---

### Post by hwan on 2012-04-08
> **Herman said:**
> I'm sorry to read of your unfortunate run of bad luck. I can only guess that you might be the victim of some kind of hoax or a practical joke, or else maybe you entered some commands you didn't understand and have since forgotten about.

Thanks for the reply, Herman. That doesn't give me a lot of hope for figuring out a safe solution. I certainly didn't knowingly issue any commands to destroy the OSes on my internal drive. The only thing boot related I did was setup the /boot partition on the external drive during the Ubuntu live CD install while the internal drives were disconnected.

My goal was to have Ubuntu on the external drive, which would only boot itself when connected and selected during the BIOS startup. I wanted Ubuntu to be able to see the internal NTFS drives and files, but not boot into Windows. If I wanted to boot into Windows, I would likely have the Ubuntu drive off and disconnected. As in the guide linked above, I added a 4th NTFS partition after the Ubuntu swap because I also wanted to have the option to boot Windows from the internal drive, then connect the USB drive and use the NTFS partition for Windows storage (as if there were no OS on it). That's the way I expected it to work. 

Again, I installed and updated Ubuntu on the external drive with no internal drives connected (to avoid exactly this kind of situation). My motherboard doesn't support setting a permanent option in the BIOS to boot from USB, but I can press an F-key and select the external USB drive manually each time.

 When I plugged my internal drives back in, I was a bit surprised to see the Ubuntu GRUB boot loader automatically add my Win 7 and XP to its menu without any prompt or confirmation. Is that supposed to happen? Would it have had to write to the internal drive boot sectors to add those entries? I assumed it was only making changes to GRUB on my external /boot partition to enable those options.

 Are there any deeper configuration options to disable or force GRUB and Ubuntu auto-detection of other drives into a hands-off mode, so they don't automatically add my internal drives to their boot loader? Are there any other options that could possibly cause this?

 Any ideas for further troubleshooting to narrow down the cause of this? I don't think I'll be experimenting with a live system anymore, but I could set up a spare internal drive to test.

---

### Post by darkod on 2012-04-08
Grub2 adding windows to the boot menu is normal, it is designed to do that. Imagine all the complaints from windows users if it didn't and they had to "hack" to simply add windows.

Since grub2 is installed on the ext hdd I see no reason or relation to touch any of your int disks.

If you don't want grub2 to add other OSs, simly make the 30_os-prober script unexecutable:
sudo chmod -x /etc/grub.d/30_os-prober

Then run:
sudo update-grub

That should sort it out.

Win7 wanting to do disk checks sounds like some corruption of windows files, which again should not be related to the boot process. Even with windows bootloader it wanted to do them.

One question: why grub4dos? Why not simply windows bootloader to boot both versions of windows?

You mentioned something about "hiding" win7 from XP. Have you actually seen it doing some damage before? Once you boot XP it's working from its own partition, no reason to touch the win7 system partition. It seems you are just creating issues with yourself like this.

EDIT: Yes, it is possible grub4dos to boot ubuntu, but only if the ext disk is connected of course.

---

### Post by hwan on 2012-04-08
> **darkod said:**
> Since grub2 is installed on the ext hdd I see no reason or relation to touch any of your int disks.

If you don't want grub2 to add other OSs, simly make the 30_os-prober script unexecutable:
sudo chmod -x /etc/grub.d/30_os-prober

Then run:
sudo update-grub

That should sort it out.

Ah, thank you. That sounds like what I'm looking for. I'll have a look at it.

 > **darkod]Win7 wanting to do disk checks sounds like some corruption of windows files, which again should not be related to the boot process. Even with windows bootloader it wanted to do them.[/QUOTE]

I did do system and disk scans for both OSes afterward and didn't find anything after Win 7 ran its repairs on the XP parition. I have had to reinstall one program on XP, but everything else I've looked at is working so far.  I admit there is a chance that these are two unrelated problems that coincidentally happened at the same time.  [QUOTE=darkod]One question: why grub4dos? Why not simply windows bootloader to boot both versions of windows?

You mentioned something about &quot said:**
> 

Well, it was part of a package that I've used successfully for years to dual boot XP, Vista and now 7. It wasn't broken until now, so I had no reason to change things. Among other things, one reason to hide Windows 7 partitions is that XP has a constantly monitoring system recovery option that is older and incompatible with the updated function on 7, so it could write conflicting changes to the 7 drives. It is possible to manually deactivate the function on a per-partition basis, which I have done for shared data partitions. I believe there may be a few other potential issues like this that the hiding function is supposed to prevent, and I prefer to stay on the safe side. 

[MS Support: No restore points are available in a dual-boot configuration together with an earlier Windows]("http://support.microsoft.com/Default.aspx?kbid=926185") explains the main issue and the fix mentioned doesn't always work. 

I just came across this link about 10.04 which shows that this kind of issue isn't entirely out of the realm of possibility. It's bugs like these which probably led to the recommendations I saw to disconnect the internal drives during the install. 

[Installing Ubuntu 10.04 to external HDD overwrites the MBR of the internal HDD](http://askubuntu.com/questions/115849/installing-ubuntu-10-04-to-external-hdd-overwrites-the-mbr-of-the-internal-hdd) 

One of the replies: [quote]And yes this is a bug in the 10.04 installer. I just took my Windows 7 VM, added a second disk in VirtualBox and installed Ubuntu 10.04. You can see in the first screenshot that, while I chose to install to sdb the bootloader is installed to sda, thus overwriting the Windows 7 bootloader.

---

### Post by Herman on 2012-04-08
> I started by unplugging all my internal HDs (Windows OS and data  drives), then connected my external USB drive and booted to the Ubuntu  11.10 live cd installer. I followed [this guide]("http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/") almost exactly, setting up the external drive with 4 partitions: /boot, /, /swap, /ntfs. 
That should be okay.
> Everything went fine, then I took out the cd and booted into Ubuntu  11.10 from the external drive. I did some updates, configuration and  installed a few applications. When you received updates in Ubuntu sometimes they include a new kernel. The new kernel will require a boot entry in GRUB's Menu and in order to write that to GRUB's configuration file a program called grub-mkconfig is run automatically. That only updates the GRUB menu though. It doesn't update any boot sectors, it only writes a text file for the boot menu. It runs grub-probe to scan the computer for other operating systems and adds them to the new boot menu too.
> After that, I plugged my internal Windows drives back in and tried to  boot Ubuntu from USB. Again, it seemed to work find and I could see all  my internal Windows drives from Ubuntu. I didn't touch the Windows OS  drives, but I did open a couple files from the Windows data drive. That's normally fine. I read and write to files in Windows from Ubuntu quite often and I think there are lots of others who do that on a regular basis too. 
> On one of the reboots into Ubuntu on USB, I noticed the Ubuntu/Debian  GRUB loader had added my two Windows systems 7 and XP to the GRUB boot  options. I didn't think it would be a problem, since I had a dedicated  boot partition on the external USB drive.  That's normal after a kernel update and shouldn't affect Windows at all.
> Anyway, once I finished up with Ubuntu. I shut it down and unplugged the  external USB drive. Then I tried to boot back into my Windows machine. 

First thing I noticed was that my old GRUB4DOS boot loader was  completely gone. The system started to load the Windows XP login screen,  then I got all sorts of errors about corrupted files and corrupted  \$Secure on multiple drives. I couldn't get past those errors to login,  so I shut down and grabbed some recovery boot cds. Interesting, but this seems like a freak occurrence. I am wondering if the NTFS file system's backup boot sector was used to restore the XP  boot sector with. There's a backup of the boot sector in the last sector  on an NTFS partition if I remember correctly. That has nothing to  do with Ubuntu, or at least I can't see the connection. Maybe Windows XP decided to do that by itself for some strange reason. 
> The Windows 7 Recovery disc gui failed, but I was able to do some repairs from the command prompt. Okay.
> That allowed me to boot into my internal drive running Windows 7, but on  boot Windows 7 detected many errors and ran CHKDISK trying to repair a  lot of corrupted files and security settings (apparently only on the XP  partitions). After some more work and system and disk scans of both  internal OSes I think I have got things mostly back the way they were  before my Ubuntu experiment. I say mostly, because I have seen at least  one unexplained new glitch in XP. That's very interestinig. It will be even more interesting to find out if it happens again or if it was just a freak occurrence, and whether or not it does turn out to be Ubuntu related. The only way to find out will be to keep experimenting.

---

### Post by hwan on 2012-04-08
> **Herman said:**
> Interesting, but this seems like a freak occurrence. 

... 

The only way to find out will be to keep experimenting. Yes, the experiment continues. Let's hope lightning doesn't strike twice. 

 > **darkod said:**
> If you don't want grub2 to add other OSs, simly make the 30_os-prober script unexecutable:
sudo chmod -x /etc/grub.d/30_os-prober

 I've been reading up on GRUB2 and found the option below. Would this be better than changing permissions?

 /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=&quot;true&quot;
``` > **Herman said:**
> When you received updates in Ubuntu sometimes they include a new kernel. The new kernel will require a boot entry in GRUB's Menu and in order to write that to GRUB's configuration file a program called grub-mkconfig is run automatically. That only updates the GRUB menu though. It doesn't update any boot sectors, it only writes a text file for the boot menu. It runs grub-probe to scan the computer for other operating systems and adds them to the new boot menu too. 

In that case, it sounds like changing the permissions would be safer since the GRUB update might wipe out one of my options. I may just do both. Is there any way to prevent grub-probe from running (or at least exclude non-Linux systems)? EDIT: After more reading, it sounds like I shouldn't need to do anything about grub-probe.

---

### Post by Herman on 2012-04-08
I don't know, I've never tried that. I agree with darkod's method from post #4.
I don't understand your and darkod's logic in thinking there's any harm in allowing GRUB to work normally though, but do whatever you think is best.

---

### Post by darkod on 2012-04-08
> **Herman said:**
> I don't know, I've never tried that. I agree with darkod's method from post #4.
I don't understand your and darkod's logic in thinking there's any harm in allowing GRUB to work normally though, but do whatever you think is best.

I have nothing against grub2 running the show, or os-prober detecting all OSs. I have it running on my computer.

But since the OP was determined not to allow it to add windows to the grub menu, I just suggested how to disable the execution of os-prober.

I also agree it sounds strange for this to be ubuntu related, but I can't say more as it's not my machine. :)

---

### Post by hwan on 2012-04-08
Well, no luck with that. I disconnected all internal drives again and booted Ubuntu from the external USB. I looked at all the grub folders and files, then did "sudo chmod -x /etc/grub.d/30_os-prober" and also added GRUB_DISABLE_OS_PROBER="true" to /etc/default/grub, then sudo update-grub.

I restarted again to check the GRUB screen to confirm Windows entries were gone and then double-checked all the grub files and folders again. There were definitely no Windows entries. 

Then I shutdown. Disconnected my external USB and reconnected the internal drives. I booted into Windows 7 and XP to make sure they were running before booting with Ubuntu. They were fine. 

Next I plugged the external USB Ubuntu drive back in and booted into Ubuntu. I opened the file browser, just to see if the Windows drives were visible, which they were. I also checked all the grub files and folders again. No Windows entries. I restarted Ubuntu once more. Opened the browser for a few minutes then shut down. 

Next, I unplugged the external USB drive and tried to boot off the internals. Nothing. Black screen and cursor. I tried to reboot to see if I could get into Windows Safe Mode. Nothing. So, I pulled out my Windows Recovery Disc and used the same commands to attempt to fix the boot records. 

```
bootrec.exe /fixmbr bootsect.exe /nt60 all /force bootrec.exe /rebuildbcd
```

After that, I booted into Windows 7 and XP, thankfully without any Corruption \$Security or CHKDISK errors. 

So, there's obviously something going on. I guess we've eliminated the GRUB OS auto-detection as the culprit. Any ideas about what booting Ubuntu from an external USB could be doing to the internal drives? How can I trace that? Is there a log of all disk activity that I could search for odd entries when my internal drives are mounted? I don't know why Ubuntu would being doing anything to affect the internal MBR when I'm not even installing the system or updating the kernel or anything.

---

### Post by oldfred on 2012-04-08
I might run the boot info script to see what is installed where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

You might run it just as you boot for from a liveCD before you boot. And then if you have the boot issue again, run the script again to see what has changed.

You can run this also. But it does write backups into each system, so some writing into the NTFS partitions will occur. This can make repairs and is another way to run bootinfoscript.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.


The only other time we have seen corruption in Windows from Ubuntu is when the user has hibernated in Windows and tried to write from Ubuntu into the Windows system partition. Best to only mount the Windows system partitions as read-only.

---

### Post by hwan on 2012-04-08
> **oldfred said:**
> I might run the boot info script to see what is installed where.
Thank you. I just happened to find that script and run it from the Live CD. Thankfully, the Live CD didn't cause any trouble booting Windows afterwards.

Note that this is a working dual booting Windows system (after I repaired with fixmbr).

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /menu.lst /BOOTMGR /Boot/BCD 
                       /Windows/System32/winload.exe /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /grldr /BOOTMGR /Boot/BCD /grldr /NTLDR 
                       /NTDETECT.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /NTLDR /NTDETECT.COM

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    86,018,047    86,016,000  17 Hidden NTFS / HPFS
/dev/sda2          86,018,048   421,658,054   335,640,007  17 Hidden NTFS / HPFS
/dev/sda3    *    421,658,055   484,006,319    62,348,265   7 NTFS / exFAT / HPFS
/dev/sda4         484,006,320 1,953,520,064 1,469,513,745   f W95 Extended (LBA)
/dev/sda5         484,006,383   547,495,199    63,488,817   7 NTFS / exFAT / HPFS
/dev/sda6         547,495,263 1,953,520,064 1,406,024,802   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,907,028,991 3,907,026,944   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 3,907,028,991 3,907,026,944   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        68CCE1F4CCE1BD06                       ntfs       win7
/dev/sda2        0C1CEFD61CEFB93A                       ntfs       win7_files
/dev/sda3        30AEF119AEF0D7F4                       ntfs       xp
/dev/sda5        7C4E08354E07E72C                       ntfs       xp_files
/dev/sda6        B8DE12ADDE126442                       ntfs       media
/dev/sdb1        1400A7E7063C0813                       ntfs       backup1
/dev/sdc1        AA38C50C38C4D909                       ntfs       backup2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/menu.lst: ================================

--------------------------------------------------------------------------------
# NeoSmart Technologies' Vista Hide 'n Seek Beta
# DO NOT MODIFY!!! YOU HAVE BEEN WARNED!

timeout 10
default 1
splashimage=/vhns.xpm.gz
foreground 000000
background ffffff

title Windows 7
find --unhide /Vista.C.HnS
find --unhide /Vista.D.HnS
find --set-root /BOOTMGR.HNS
makeactive
chainloader /BOOTMGR.HNS
boot

title Windows XP
find --hide /Vista.C.HnS
find --hide /Vista.D.HnS
find --remap-root /XP.H.HnS
find --set-root /XP.H.HnS
makeactive
chainloader /ntldr
boot

# All your boot are belong to NeoSmart!--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       0

================================ sda3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Vista Hide 'n Seek: Windows XP" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

========================== sda3/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
default 0
timeout 1
fallback 1
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  00 18 c6 58 9b 01 80 55  d5 6c 08 32 42 d2 ba ef  |...X...U.l.2B...|
00000010  f2 7a ae a4 53 82 80 04  00 80 80 30 40 1a 00 54  |.z..S......0@..T|
00000020  00 68 20 03 00 06 08 03  06 00 00 90 04 00 a0 0d  |.h .............|
00000030  00 18 80 01 c0 88 a0 04  00 18 a0 04 00 19 01 40  |...............@|
00000040  1a 00 04 00 60 03 22 00  10 10 06 0c 50 06 00 06  |....`.".....P...|
00000050  88 01 00 06 00 48 08 01  40 02 a0 05 00 08 05 00  |.....H..@.......|
00000060  1a 00 04 40 02 00 01 02  00 c0 01 f0 40 60 80 c4  |...@........@`..|
00000070  02 20 18 42 dd 00 60 00  55 60 00 59 20 34 83 02  |. .B..`.U`.Y 4..|
00000080  de 0c 40 01 a0 04 00 60  14 04 83 10 00 80 41 82  |..@....`......A.|
00000090  40 01 aa 72 bc 04 b1 16  85 e7 a0 45 70 60 10 60  |@..r.......Ep`.`|
000000a0  24 19 01 85 86 20 80 34  54 00 8a 20 ac 40 00 c0  |$.... .4T.. .@..|
000000b0  18 80 04 00 6a 00 45 00  18 80 01 04 00 88 80 34  |....j.E........4|
000000c0  40 08 00 90 06 00 0c 00  01 8a 00 14 40 03 10 40  |@...........@..@|
000000d0  1a 2a 00 52 20 80 31 00  03 10 40 0a 88 01 41 01  |.*.R .1...@...A.|
000000e0  6a 00 05 56 a2 00 44 00  1a 20 04 01 22 a0 0d 14  |j..V..D.. .."...|
000000f0  00 80 04 00 02 00 38 a8  03 55 00 2a 00 35 48 80  |......8..U.*.5H.|
00000100  01 15 00 62 00 15 00 18  00 c0 80 d5 22 00 41 80  |...b........".A.|
00000110  41 c4 44 00 80 04 10 00  18 08 01 00 b6 c1 80 00  |A.D.............|
00000120  46 09 82 01 04 06 80 31  40 c6 12 38 e0 04 50 06  |F......1@..8..P.|
00000130  02 45 00 6a 02 40 20 09  40 19 00 08 30 07 a8 03  |.E.j.@ .@...0...|
00000140  10 02 a0 0d 56 02 00 c0  02 03 40 08 05 01 2c 18  |....V.....@...,.|
00000150  03 03 b0 22 10 5a d7 96  04 12 b5 c7 d1 b5 65 c6  |...".Z........e.|
00000160  8f 00 0a ac 00 1a 00 40  08 00 c4 00 80 01 01 aa  |.......@........|
00000170  c0 80 0d 40 18 00 15 48  03 88 80 04 40 08 80 0d  |...@...H....@...|
00000180  50 06 00 55 00 20 11 50  06 00 0c 50 06 a0 0d 00  |P..U. .P...P....|
00000190  24 06 a0 01 55 f1 40 02  c4 00 18 22 0c 00 12 80  |$...U.@...."....|
000001a0  02 45 01 1c 10 02 00 03  40 18 20 0c 00 28 09 10  |.E......@. ..(..|
000001b0  04 a8 00 45 00 60 2d 56  00 26 08 01 00 60 00 fe  |...E.`-V.&...`..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 31 c3 c8 03 00 fe  |......?...1.....|
000001d0  ff ff 05 fe ff ff 70 c3  c8 03 a1 3c ce 53 00 00  |......p....<.S..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```


Ubuntu Live CD output (which matches MBRFix backup output in Windows)
```
ubuntu@ubuntu:~/Downloads$ sudo hexdump -n 512 -C /dev/sda
00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1c fe  |.v..N..n...fas..|
000000a0  4e 11 75 0c 80 7e 00 80  0f 84 8a 00 b2 80 eb 84  |N.u..~..........|
000000b0  55 32 e4 8a 56 00 cd 13  5d eb 9e 81 3e fe 7d 55  |U2..V...]...>.}U|
000000c0  aa 75 6e ff 76 00 e8 8d  00 75 17 fa b0 d1 e6 64  |.un.v....u.....d|
000000d0  e8 83 00 b0 df e6 60 e8  7c 00 b0 ff e6 64 e8 75  |......`.|....d.u|
000000e0  00 fb b8 00 bb cd 1a 66  23 c0 75 3b 66 81 fb 54  |.......f#.u;f..T|
000000f0  43 50 41 75 32 81 f9 02  01 72 2c 66 68 07 bb 00  |CPAu2....r,fh...|
00000100  00 66 68 00 02 00 00 66  68 08 00 00 00 66 53 66  |.fh....fh....fSf|
00000110  53 66 55 66 68 00 00 00  00 66 68 00 7c 00 00 66  |SfUfh....fh.|..f|
00000120  61 68 00 00 07 cd 1a 5a  32 f6 ea 00 7c 00 00 cd  |ah.....Z2...|...|
00000130  18 a0 b7 07 eb 08 a0 b6  07 eb 03 a0 b5 07 32 e4  |..............2.|
00000140  05 00 07 8b f0 ac 3c 00  74 09 bb 07 00 b4 0e cd  |......<.t.......|
00000150  10 eb f2 f4 eb fd 2b c9  e4 64 eb 00 24 02 e0 f8  |......+..d..$...|
00000160  24 02 c3 49 6e 76 61 6c  69 64 20 70 61 72 74 69  |$..Invalid parti|
00000170  74 69 6f 6e 20 74 61 62  6c 65 00 45 72 72 6f 72  |tion table.Error|
00000180  20 6c 6f 61 64 69 6e 67  20 6f 70 65 72 61 74 69  | loading operati|
00000190  6e 67 20 73 79 73 74 65  6d 00 4d 69 73 73 69 6e  |ng system.Missin|
000001a0  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
000001b0  65 6d 00 00 00 63 7b 9a  a1 64 ca 75 00 00 00 20  |em...c{..d.u... |
000001c0  21 00 17 fe ff ff 00 08  00 00 00 80 20 05 00 fe  |!........... ...|
000001d0  ff ff 17 fe ff ff 00 88  20 05 c7 75 01 14 80 fe  |........ ..u....|
000001e0  ff ff 07 fe ff ff c7 fd  21 19 e9 5b b7 03 00 fe  |........!..[....|
000001f0  ff ff 0f fe ff ff b0 59  d9 1c 11 00 97 57 55 aa  |.......Y.....WU.|
```

---

### Post by oldfred on 2012-04-08
You did not have Ubuntu disk plugged in. It shows the normal Windows as near as I can tell. 
I did not know NeoSmart is using menu.lst which has been the old grub legacy name for a boot menu.

You have boot files in several partitions and what looks like  extra /grldr files??

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by darkod on 2012-04-08
I don't know if it has relation to the hide/unhide you are doing, but you have windows boot files all over the place. So it is difficult to know what is being used and what not.

I still think a better approach is using windows bootloader, no hiding, and if XP system restore has any issues just deselect all partitions and disks except the XP system partition.

But I am not dual booting XP and 7 so I can't be sure what implications exist.

People have mentioned here dual booting XP and 7 and never mentioned they need to do any hiding, or using a boot process like the one you have. And it still works for them.

But I guess that is a question for windows forums. How to dual boot XP and 7 without grub4dos and hiding one OS. Once you have that running, adding ubuntu is no problem.

---

### Post by Herman on 2012-04-08
> But since the OP was determined not to allow it to add windows to the  grub menu, I just suggested how to disable the execution of os-prober.
@ darkod, all respect and no offence intended.  :)

My 2 cents worth:
> Next I plugged the external USB Ubuntu drive back in and booted  into  Ubuntu. I opened the file browser, just to see if the Windows  drives  were visible, which they were. I also checked all the grub files  and  folders again. No Windows entries. I restarted Ubuntu once more.  Opened  the browser for a few minutes then shut down. 

Next, I unplugged the external USB drive and tried to boot off the   internals. Nothing. Black screen and cursor. I tried to reboot to see if   I could get into Windows Safe Mode. Nothing.Judging by the  information in post #10 it looks like accessing (just reading) the  Windows files from Ubuntu seems to have something to do with triggering  this strange behavior in Windows.
Ubuntu might be writing time stamps to the file, you know, so when you  right-click on the file and click 'properties', or if you view your  files in the detailed list view in Windows you can see the times and  dates they were originally created, last accessed, and last modified. That shouldn't cause any problems by itself, as Windows would be doing that too of course.
I agree with oldfred, try having Ubuntu mount your Windows drives 'read only'. Test to see if that helps or not.

There are a couple of things here I don't know about.
One is this $security thing. Can you explain more about what that is and how it works?
The other is your neosmart vista hide n seek beta, "all your boot are  belong neosmart", not that there is anything wrong with that. I'm familiar with the concept of 'hiding' partitions since Windows  95/98/ NT, but I didn't even know it was possible anymore to 'hide'  partitions since Vista came out, that seems to be a pretty clever trick  in my opinion. The only problem is that  we don't know how it works or what it might have to do with the odd  behavior you're encountering.

Also maybe try looking at your Windows files from other operating  systems such as other Windows or from your Ubuntu Live CD or some other  Gnu/Linux. The idea would be to test whether it's only accessing your  files from Ubuntu that seems to cause problems. 
If just having your files accessed at all by any outside system can  trigger a security scare within Windows then maybe you have some kind of  hyper security settings that include resetting the boot sector. I have  read that the Windows boot sector is a popular target for writers of  malware to use as a first base. For that reason it tends to be well  guarded by security software. It's within the realms of possibility that your security software /settings could be restoring the XP boot sector from it's backup automatically without your knowledge. (I'm just using my imagination and wondering if it scans the OS for timestamps written since Windows last boot time?).

Security settings for Windows can also include BIOS settings such as MBR write-protect, that's another thing worth taking into consideration. Can unplugging and booting, then re-plugging disks from the MBR by itself be causing problems?
I do know in one of my PCs, the BIOS it quite tempramental and it can get all mixed up after (IDE) disks are added or removed. Most newer computers mainly use SATA except maybe for the optical drives, and SATA seems less of a problem when it comes to the boot order.

More testing should isolate the cause of the problem. :)

---

### Post by hwan on 2012-04-08
> **darkod said:**
> But I guess that is a question for windows forums. How to dual boot XP and 7 without grub4dos and hiding one OS. Once you have that running, adding ubuntu is no problem.

Well, this has been working for years and survived an upgrade from XP/Vista dual boot to XP/7 dual boot. I don't see any fault at there, except possibly Ubuntu being unable to recognize and not access the drives without causing some unknown problem. As for being necessary or not, I linked the Microsoft Support database article earlier and other people being unaware of this issue simply means they're unaware of the issue.

> **Herman said:**
> My 2 cents worth:
Judging by the information in post #10 it looks like accessing (just reading) the Windows files from Ubuntu seems to have something to do with triggering this strange behavior in Windows.
Ubuntu might be writing time stamps to the file, you know, so when you right-click on the file and click 'properties', or if you view your files in the detailed list view in Windows you can see the times and dates they were originally created, last accessed, and last modified. That shouldn't cause any problems by itself, as Windows would be doing that too of course.

In that post, my second attempt to boot Ubuntu with internal drives plugged in, I didn't actually open the drives or access any files. I opened the Ubuntu file browser to see the drives listed in the left-hand pane without clicking them.

Is there an option in the Ubuntu System Settings GUI to prevent the Ubuntu file browser from opening drives as read-write or do I need to edit fstab or udev or something else to specify a rule to only open as read-only?

> **Herman said:**
> There are a couple of things here I don't know about.
One is this $security thing. Can you explain more about what that is and how it works?

I haven't seen that issue before, so I'm not sure. I imagine it might have something to do with Windows file permissions and ownership, but it only happened the first time. It could also just be part of the general file corruption on the XP partition which also only happened once. So, as suggested these may be two separate issues: possibly a one off unrelated file corruption and a repeatable situation with Ubuntu somehow conflicting with my working dual boot files and MBR.


> **Herman said:**
> Also maybe try looking at your Windows files from other operating systems such as other Windows or from your Ubuntu Live CD or some other Gnu/Linux. The idea would be to test whether it's only accessing your files from Ubuntu that seems to cause problems.

Well, I haven't opened any Windows files from the USB Ubuntu or even accessed any file properties since this first happened. Booting from the Ubuntu Live CD, I did run the Boot Info Script and save the output as well as hexdump info to two text files on one of the Windows non-boot drives. In that case, there were no issues booting Windows aftering running from the Live CD with internal drives connected and writing new files to a non-boot drive.

> **Herman said:**
> Can unplugging and booting, then re-plugging disks from the MBR by itself be causing problems?

No, I eliminated this possibility in post #10 by successfully booting Windows XP and 7 immediately after I had disconnected internal drives, booted Ubuntu twice with them unplugged, then shutting down, removing the USB cable and re-connecting the Windows internal drives. There were no problems booting then. So, the issue only happens when Ubuntu boots from USB while the internals are connected.


I've also contacted NeoSmart who designed the boot utilities (EasyBCD and the GRUB4DOS scripts) to see if they can offer any reasons why Ubuntu might have some kind of conflict. I'll wait to hear back from them before proceeding. My next step will be booting Ubuntu with the drives connected and running the Boot Info Tool and MBR hexdump again to compare the changes. I would also like to add in the configuration to mount internal drives as read-only.

---

### Post by oldfred on 2012-04-08
I am not expert on mount and fstab settings. Others may have updates or better ways.

Manually:
mkdir /media/win
sudo ntfs-3g -o ro /dev/sda1 /media/win

this is the entry I have used, my UUID shown:
To see your UUID
sudo blkid
```
UUID=04B05B70B05B6768     /mnt/cdrive         ntfs-3g  ro   0  0 

```

If in /mnt it will not show in left pane of Nautilus. If you want it in the left pane use /media or /home as places to mount it. You have to make mount point first with mkdir /mnt/cdrive or whatever you want as to location and name.

---

### Post by hwan on 2012-04-09
Well, I have had some success. I booted Ubuntu from the external USB once, shutdown, then successfully got my Windows (GRUB4DOS) boot menu to come up and booted into Windows 7 then XP without issue.

Thanks, oldfred. I was looking into your suggestion and found an alternative that seems to work.

The main solution involved booting the Live CD to get all the Windows drive unique UUIDs with:

sudo blkid

Then I disconnected internal Windows drives and booted into the Ubuntu USB external drive and created a new file:

/lib/udev/rules.d/81-nomount-win.rules

Contents of the file similar to this (one line for each partiton of all internal Windows drives):

```
# prevent auto-mounting of Windows drives

ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="ram*", GOTO="hide_partition_end"

# xp
ENV{ID_FS_UUID}=="6b7f8268-c6a2-4265-9563-78f808b3c1cd", ENV{UDISKS_PRESENTATION_HIDE}:="1"

# win7
ENV{ID_FS_UUID}=="6b7f8268-c6a2-4265-9563-78f808b3c1cd", ENV{UDISKS_PRESENTATION_HIDE}:="1"

LABEL="hide_partition_end"
```

The second thing I did which may not have had any effect was after shutting down from Ubuntu, I kept the USB drive on and connected while booting back into Windows 7 the first time. After that I disconnected the drive and also booted into XP without a problem.

I guess I will tentantively mark this [SOLVED]. I seem to be able to triple-boot now without issue, **but I never figured out exactly what was causing the MBR to be altered and fail booting** when Ubuntu had Read Write access to the drives. I'm pretty sure I should be able to have my Windows drives readable (and writeable) without fear of booting Ubuntu causing problems every time. Otherwise, there would be a lot more people reporting this issue.

Since hiding/disabling write access stopped the Windows boot problems, that makes me think some combination of Ubuntu, my USB drive, BIOS and dual boot (GRUB4DOS) setup are doing something mysterious in the background that I can't isolate.

During my tests, until the final successful attempt. I always disconnected the internal drives when doing anything on the USB Ubuntu drive and only used the Live CD when my internal drives were connected.

After a suggestion from someone else, I started looking at the BIOS setup screen on every single boot and making notes. The theory was that the BIOS might be auto-configuring the boot order, so that after I booted Ubuntu, somehow my internal boot drive would disappear from the boot device list or be replaced with one of my non-boot drives. Anyway, this was not the case. I tried every possible combination and the BIOS was always set to the correct boot order regardless of which drives I had plugged in or which OS I had previously been using. (My main boot drive is on SATA 1 as the Primary Master.)

I think that in the /lib/udev/rules.d/NN-xxx.rule it would probably safe to only block the 2 main system boot partitions (xp and 7 in my case) and allow read write access to one or more of the non-booting Windows data partitions, although I have them all blocked for now. Of course, I can always mount them manually from the console.

Thanks to everyone for all your helpful comments and suggestions.

---

### Post by hwan on 2012-04-09
Well, I'm stumped. I had to remove the SOLVED tag.

After my "success" I shutdown. This morning I booted up and got the same blank screen with a blinking cursor. No boot menu and no Windows.

I checked the BIOS to confirm the correct drive was selected and it was. Then I booted from the Ubuntu Live CD and made a dd copy of the MBR. I have a collection of MBR.bin files now, so I compared it with a known "good" file.

```
cmp -1 MBRwin.bin MBRnoboot.bin

447 200   0
451   7  27
467   7  27
479   0 200

1) 0x1be=446 to 0x1be=446 (1 bytes)    80 / 00
2) 0x1c2=450 to 0x1c2=450 (1 bytes)    07 / 17
3) 0x1d2=466 to 0x1d2=466 (1 bytes)    07 / 17
4) 0x1de=478 to 0x1de=478 (1 bytes)    00 / 80
```Then I just copied the good MBR.bin back onto the drive.

```
dd if=/boot/MBRwin.bin of=/dev/sda bs=512 count=1
```After that my boot menu was working again and got me back into Windows. Doing some searching on the subject, I found mention that the MBR goes to 446, then after that is actually the PBR. I can't be sure that exactly the same bytes were changed the last few times the boot failed, but this seems to indicate a problem with the PBR changing rather than the MBR.

Note that this time, it didn't happen immediately after running Ubunutu, but three boots later, after I had successfully booted into Windows 7, then XP and shutdown for a few hours. Neither 7 nor XP had shown any errors or signs of trouble on those previous boots.

Now I'm starting to wonder about a hardware issue, maybe bad SATA cables or the BIOS or something else on the motherboard is failing, or maybe the relatively new HD is developing bad sectors in the boot sector. It could be anything.

This is the first time I've tried to boot from USB although I hook up non-bootable thumb drives and other external drives all the time. I don't know if that could have exposed a fault in the BIOS.

Anyway, now I know that I can quickly restore the MBR with dd if it happens again. I have other things to get done, so I'll probably try to stick to using the Windows dual boot and see if the problem happens again or if any other glitches come along. I'll hold off on booting the USB drive for a while.

I'm going to ask the people who made my dual boot loader if they have any ideas.

---

### Post by oldfred on 2012-04-09
The MBR is the boot code in the first 440 bytes and the partition table. Windows often has some serial numbers in the space in between. (A PBR is the boot code in a partition).

The changes are what you are doing in hiding. In boot script it shows 07 for standard NTFS and 17 for Hidden. Often 80 is the code for the first drive.

Here is the specification of the partition table format:
[http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3](http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3)

Why are you hiding again? Many use grub to boot both XP & 7 from the grub menu.
To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by hwan on 2012-04-10
Thank you for the links and comments. I removed, reinstalled and reconfigured my Windows dual boot system and I haven't had any more problems booting Windows since then.

After consulting with the author and other users of my dual booting setup, it sounds like an unknown combination of factors including booting from USB, my motherboard, BIOS and my dual boot loader are likely causing this problem, rather than Ubuntu itself. I just happened to be trying out Ubuntu when this unlucky combination came together. The exact cause of this issue still remains a mystery.

So, for now, I will put Ubuntu on the shelf and hold off on any further attempts to boot from my USB drive. I will consider Wubi again or try to clear some space for a new Ubuntu partition on my internal drive. I'll also look options to replace my current Windows dual boot system with something else.

> **oldfred said:**
> Why are you hiding again? Many use grub to boot both XP & 7 from the grub menu.

As I mentioned and as was detailed in the Microsoft Support link I posted, Windows XP is incompatible with the Windows 7 recovery system restore points and volume shadow copy, so Windows 7 restore points are deleted when XP accesses those partitions. Windows 7 is XP aware, so the reverse isn't true. This is the reason I have been running my dual boot like this for years (since Vista).

Post marked as [SOLVED] again, although I haven't solved much of anything and won't be running Ubuntu in this configuration again.

---

### Post by oldfred on 2012-04-10
I do not dual boot XP and 7 but when dual booting with Windows and Ubuntu always suggest a separate NTFS partition and setting Windows as read-only so you do not corrupt the Windows install. 
If using two versions of Windows you probably should do the same, have a shared NTFS for data and only read from the other system. Not sure how to set read only in Windows.

---

### Post by hwan on 2012-04-10
> **oldfred said:**
> I do not dual boot XP and 7 but when dual booting with Windows and Ubuntu always suggest a separate NTFS partition and setting Windows as read-only so you do not corrupt the Windows install.

If using two versions of Windows you probably should do the same, have a shared NTFS for data and only read from the other system. Not sure how to set read only in Windows.

In fact, that's exactly the same reasoning which led me to the boot loader setup that I have now. Except that instead of setting the other system to read-only, it is being hidden which has the same result of preventing XP from corrupting Windows 7 (due to the special case of XP deleting system restore points). I have the systems on two separate partitions and a third shared data partition. I use the GRUB4DOS specifically because allows the possibity to retain the standard Windows 7 MBR loader, and be a part of a chain loading sequence that can use either BOOTMGR or NTLDR. It has worked quite well for years.

I'm holding off on any more experiments, but am continuing to read up on the various options.

From what I saw when I was booting USB then trying to return to Windows, it might be the case the the BIOS somehow retains an incorrect residual drive mapping and boot order after booting from USB. So, even though the BIOS settings and menu show the correct order, it somehow was not ordering the drives correctly, so it didn't find the bootable Windows MBR because it was looking for the wrong drive or partition.

The other possibility is that some of the chain loading boot files outside of the MBR/PBR were corrupted (such as NTLDR, BOOTMGR or grldr). Because once I did a full clean up and reinstall of those files, my dual boot is working normally again.

Everytime I checked the MBR file, it was correct for either my XP or 7 selection, whether from internal (with Windows MbrFix) or from Ubuntu on USB or Live CD, the MBR matched one of two working configurations, even when startup failed to find any boot device. So it had to be something else wrong, or the BIOS looking in the wrong place.

---

