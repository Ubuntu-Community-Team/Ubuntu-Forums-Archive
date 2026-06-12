---
title: "Multi-Boot DOS, WinXP &amp; Ubuntu 12.10 on 2 Hard Drives"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by chux.junk on 2014-02-15
From the Master Boot Record on Disk 0, Partition 1, I am able to boot to DOS or WinXP successfully but not to Ubuntu. Here are my partitions:

Partition: /dev/sda1     <<My DOS boot partition>>
File System: fat32
Label: DOS710
Size: 1.95 GiB
Flag: boot

Partition: /dev/sda2
File System: extended
Size: 26.00 GiB
Flag: lba

Partition: /dev/sda5     <<My WinXP partition>>
File System: fat32
Label: WINXP
Size: 26.00 GiB

Partition: /dev/sdb1     <<My Ubuntu /boot partition>>
File System: ext4
Size: 476.00 MiB
Flag: Boot

Partition: /dev/sdb2
File System: extended
Size: 111.32 GiB

Partition: /dev/sdb5     <<My Ubuntu / partition>>
File System: ext4
Size: 13.97 GiB

Partition: /dev/sdb6     <<My Ubuntu /home partition>>
File System: ext4
Size: 36.32 GiB

Partition: /dev/sdb7     <<My Ubuntu /swap partition>>
File System: linux-swap
Size: 3.72 GiB

Partition: /dev/sdb8     <<My common data partition>>
File System: fat32
Size: 57.31 GiB

When creating the partitions during installation of Ubuntu 12.10 from the LiveCD, I pointed the bootloader to /dev/sdb.

I have run 'dd if=/dev/sdb of=bootsect.lnx bs=512 count=1' and copied the bootsect.lnx file to c:\.  I have added 'c:\bootsect.lnx = "Ubuntu 12.10"' to the end of c:\boot.ini.

Here is the results.txt file from bootinfoscript:

[ATTACH]250382[/ATTACH]

Apparently, the information in the bootsect.lnx file is not allowing Ubuntu to boot.  What changes do I need to make to boot Ubuntu from my Master Boot Record on the c: drive?

---

### Post by Bucky Ball on 2014-02-16
Tried Boot Repair? 

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by chux.junk on 2014-02-16
Thanks, Bucky.  I'll look into that but what went wrong?  What is the error that I'm fixing?

---

### Post by oldfred on 2014-02-16
Years ago I have seen users copy a PBR - partition boot sector to a file and use that to boot. It worked better then  as grub legacy would fit into a PBR. But grub2 does not and converts to blocklists or hard coded addresses which may change on every grub or kernel update, then requiring reinstall of grub.

But grub2 is a good boot manager as well as Ubuntu's boot loader. 
Just install grub2 into MBR and use it to boot everything. Not sure if it will find DOS but relatively easy to add a boot stanza for DOS boot.

Shows Vista, but how BIOS/MBR systems work (not for new UEFI)
  Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Some DOS entries in grub menu:

      
 menuentry "FreeDOS" {
    linux16 /boot/memdisk
    initrd16 /boot/floppy.img
}


 menuentry "Msdos 7 (on /dev/sda2)" {
set root='(hd0,msdos2)'
chainloader +1
} 


 #Add menu entry to 40_custom,
gksudo gedit /etc/grub.d/40_custom

      
 Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by chux.junk on 2014-02-16
Thanks, Fred.  Between you and Bucky, I've got a LOT to wade through and try to understand.  I'm a complete newbie to Linux and try to understand what I'm doing and why before I do it. So it may take me awhile to get to either of you with "kudos, it worked!" or more questions.

From what I am gather so far, it looks like the information I had read when I first started this adventure that had me copy the first 512 bytes of the Ubuntu boot loader and make it available to the Windows boot loader was pertaining to Grub Legacy.  From your message, I gather Ubuntu 12.10 uses Grub2 and the information I need is no longer in that location.  It seems Bucky's remedy is to move the Ubuntu boot information to /dev/sda and you agree.  However, you also propose an additional possibility of leaving the information in /dev/sdb (where I think I have it now) and adding custom menu(s) to allow for booting my DOS and WinXP systems.  Please forgive me if I am not using exactly the right terminology.  I've only be involved with Linux for a few days.

---

### Post by oldfred on 2014-02-16
Can you in BIOS choose to boot sdb and set it as default? 
Or from a one time boot key as a test (its f12 on my system but varies by vendor).

With multiple drives I do prefer each install be on a different drive and have its boot loader in the MBR of that drive. But some older systems only boot from sda. Or if IDE/PATA, not SATA you have to have jumpers correct.

---

### Post by chux.junk on 2014-02-16
Fred,

No. I can boot off several different devices but for hard drives, it's only the first partition of the first hard drive.  In order to multi-boot, I need to update the boot.ini file in that partition to tell it about the other systems.

From what I've read so far, I too prefer to keep the boot loaders in the MBR of the respective drive.

I'm still processing the information you and Bucky have provided.  Thanks for your suggestions so far!

---

### Post by chux.junk on 2014-02-17
Bucky,

I have downloaded and run Boot Repair as you suggested but did not elect (yet) to allow it to make any corrections.  Instead, I selected the 'Create a Boot Info Summary' option so you could see my current situation.  The file is at [http://paste.ubuntu.com/6947126/](http://paste.ubuntu.com/6947126/).

I have two physical hard drive devices with DOS and Windows XP successfully installed and dual-booting on the first device.  I have installed Ubuntu 12.10 on the second device and pointed the bootloader to /dev/sdb during the installation. Using a set of instructions from a thread on another website, I executed the following (sudo dd if=/dev/sdb of=bootsect.lnx bs=512 count=1) and copied the resultant bootsect.lnx file to c:\.  I edited the c:\boot.ini file to reference the bootsect.lnx file.

Can Boot-Repair allow me to boot into Ubuntu without loading GRUB2 into /dev/sda?  If not, what else can I do to boot Ubuntu without destroying my Windows MBR?

---

### Post by Bucky Ball on 2014-02-17
Just out of curiousity, and we may have been here already, but can you simply boot into Ubuntu, open a terminal and:

sudo update-grub

? Keep an eye on the output and see if you see XP being probed. After this command, reboot and see if everything is present and correct.

You can do a lot with Boot Repair. From memory it will allow you to put the grub wherever you like (there is a Grub tab somewhere with options for grub).

---

### Post by chux.junk on 2014-02-17
Fred,

Reference my comments to Bucky in my post above.

I'd would prefer not to but if I must install GRUB2 into dev/sda, can I just add this to 40_custom as you suggest and get all 3 of my OS on the menu and bootable?

menuentry "MSDOS 7 (on /dev/sda2)" {
set root='(hd0,msdos2)'
chainloader +1
}

---

### Post by chux.junk on 2014-02-17
Bucky,

Yes.  I could boot Ubuntu from my LiveCD and into the update-grub command but wouldn't that destroy my Windows MBR on dev/sda?  That's what I'm trying to avoid.

EDIT:  That should be '... _*input*_ the update-grub ..."

Yes.  Boot-Repair has a 'GRUB Location' tab.  By default, it has:

     'OS to boot by default [sdb5 (Ubuntu 12.10)]'   <<< can by changed to [Windows (via sdb5 menu]>>>
     'Separate /boot partition [sdb1]'   <<< can be changed to [sdb6]>>>
     'Place GRUB in all disks (except USB sticks without OS)   <<< this is pre-selected>>>
     'Place GRUB into [sdb]   <<< this is selectable in place of the above>>>

There is also an MBR tab but it is greyed out.

---

### Post by Bucky Ball on 2014-02-17
> **chux.junk said:**
> Bucky,

Yes.  I could boot Ubuntu from my LiveCD and into the update-grub command but wouldn't that destroy my Windows MBR on dev/sda?

No. It updates grub, wherever it is. It doesn't move it anywhere. And no, sorry, thought you could boot to Ubuntu. This won't work from a Live boot, although there are other commands that will do the same (this particular command won't work there). I'll have a look later (getting a bit busy at the mo).

PS: Have a look at 'The Terminal Way' [HERE.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using_the_Ubuntu_CD_.28Recommended.29")

---

### Post by fdrake on 2014-02-17
@Bucky Ball 
yes you can update your grub with a live cd . just chroot the / partition :[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

@OP
how are the hdds connected (master slave scheme? or 1 is connected to the cd-rom?)

---

### Post by chux.junk on 2014-02-17
The two HDDs are IDEs on one controller and jumpered as CS (cable-select).

Thanks for the link.  I take a look at it.

---

### Post by fdrake on 2014-02-17
@OP:
are able with a live cd to access/mount your second drive?
-----------------------never mind . I just sau yout results.txt file ---------------------

---

### Post by oldfred on 2014-02-17
Even with cable select you must use the newer 80 conductor cable. I once used a nice new 40 conductor that came with a new CD for a hard drive and it was not bootable.

 If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.



Boot-Repair will default to install to all MBRs. Best not to use default, but choose which MBR to install into.
Some have had to install grub to the Windows drive as system only boots from sda. Also some do not reset BIOS enumeration of drives correctly, so Windows only boots if grub is on same sda drive.

You should be able to boot everything from grub menu. As part of a sudo update-grub it also runs os-prober which finds Windows. Not sure if it finds DOS or not, but you can add that entry.

You only can directly run sudo update-grub from inside your install or from a chroot into your install. You cannot just run it from liveCD/DVD as that would try to update CD/DVD which obviously will not work.

You can always use XP to restore its boot loader or use Boot-Repair which adds syslinux boot loader which works just like Windows in MBR.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by chux.junk on 2014-02-18
Okay, guys.  I finally took the plunge.  After trying several Boot-Repair attempts with putting GRUB2 on sdb, I took your advice and put GRUB2 on sda.  Now I get the a boot menu with Ubuntu, advanced options for Unbuntu, 2 memory tests, and a Windows option.  I am able to boot Ubuntu with this menu but trying to boot Windows gives me an "Invalid system disk, Replace  the disk and then press any key" error.  Also, my DOS selection has disappeared.  I am becoming VERY discouraged with Linux!!

The latest Bootinfo Summary is at [http://www.ubuntu.com/695485/](http://www.ubuntu.com/695485/).  How do I correct this mess or do I re-partition my hard drives, re-install DOS and WinXP and scrap Linux?

EDIT:  Oops!  That should be [http://paste.ubuntu.com/6954851/](http://paste.ubuntu.com/6954851/).  Sorry!

---

### Post by oldfred on 2014-02-18
Your link does not work, it normally is a pastebin?

I did not think grub2's os-prober would find and old DOS, but we should be able to add that manually.
But we need to see BootInfo report, but Boot-Repair cannot normally fix Windows. It may need some repair like chkdsk. Did Windows boot, just before you installed grub to MBR of sda. Or does using Boot-Repair to add a Windows boot loader to sda let Windows work?

---

### Post by chux.junk on 2014-02-18
Hi, Fred.

Sorry for the link.  I've corrected it to [http://paste.ubuntu.com/6954851/](http://paste.ubuntu.com/6954851/).  Angry fingers were at work.

Yes.  DOS and Windows both would boot from the Windows bootloader (or whatever it's called) menu before GRUB2 was installed to sda.  Now, the Windows bootloader menu does not appear.  It has been replaced with the GRUB2 menu (or whatever it's called).  As I mentioned in my last post, the menu has Ubuntu and Windows listed but only Ubuntu works.  Selecting Windows does not.

---

### Post by oldfred on 2014-02-18
Your sda1 boot.ini says Windows is in sda2 
       default=multi(0)disk(0)rdisk(0)[COLOR=#ff0000]partition(2)[/COLOR]\WINDOWS

And your boot.ini in sda5 says it was sda3?
default=multi(0)disk(0)rdisk(0)[COLOR=#ff0000]partition(3)[/COLOR]\WINDOWS

Windows/DOS only boots from the one partition with the boot flag which you have on sda1. And then boot.ini will have entries for additional installs of Windows.
You also show both Windows boot files and DOS boot files in sda1, which is typical for Windows, as second installs add/replace other boot files in the partition with the boot flag.

So all your boot.ini do not look correct and even if you reinstall MBR with Windows boot loader it will not work.
Did you convert partitions on sda around.

Windows only can directly boot from a primary partition. You can repair or make sure you have all the boot files in each Windows install and boot directly if there are primary partition. Not sure why you have Windows in sda5 as you only have two actual partiitons on sda. 
I would use fixparts to convert sda5 to sda2. You then need to run chkdsk on all the Windows/Dos partitions and edit boot.ini to be correct. 

 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You will have to edit boot.ini. Better to use Windows tools as some Linux tools may use wrong line endings.
Gedit does have an option to save with DOS/Windows endings, but you have to choose that.
 If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.


 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)


 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

---

### Post by chux.junk on 2014-02-18
Okay, Fred.  Let's take this from the top.  Please refer back to my original message which describes my partitioning and note that sda1 contains my DOS files while sda5 contains my WinXP files.  My boot.ini file on sda1 contained (before messing around with Ubuntu):

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
C:\ = "MS-DOS 7.10"

This configuration allowed me to boot my system and brought up a menu allowing me to choose between WinXP or DOS.  If I chose WinXP, WinXP would boot properly.  If I chose DOS, another menu came up asking me if I wanted to boot with or without CD-ROM support.  After making a selection, DOS would boot properly.

Then, after reading many, many threads on this and other Linux forums and websites, I decided to install Ubuntu in a multi-boot environment.  From my reading, I decided, like you, that I wanted to keep everything separate so I installed Ubuntu 12.10 from a LiveCD on my second hard drive (sdb).  Both hard drives are IDE drives, jumpered for CS and are attached with the correct Ultra ATA/100 ribbon cable.  My BIOS provides the capability to boot from multiple devices but only one HDD (the first partition of the first hard drive).  During the installation of Ubuntu, I purposely partitioned sdb into 5 partitions; 4 for Ubuntu (sdb1 as /boot, sdb5 as /, sdb6 as /home, and sdb7 as swap) and 1 as fat32 for a common DOS/Windows/Ubuntu file repository (sdb8).  The installation appeared to go smoothly with no error messages.  At this time, my system was still dual-booting DOS and WinXP properly but there was no way to boot Ubuntu.  It did not show up on the boot menu.

Then, based on the guidance contained in [http://archive09.linux.com/articles/113945](http://archive09.linux.com/articles/113945), I ran "dd if=/dev/sdb of=bootsect.lnx bs=512 count=1" and copied the resultant file to C:\ (my sda partition).  I modified C:\boot.ini to include 'C:\bootsec.lnx = "Ubuntu 12.10"' at the end.  Upon rebooting, Ubuntu was displayed in the boot menu but would not boot; going to a blank screen with a blinking cursor in the upper, left-hand corner.  The DOS and WinXP options worked as they were previously.

This is where I started posting to this forum.  Based on input from here, I downloaded and executed Boot-Repair but did not allow it to make any changes.  The resultant BootInfo report is at [http://paste.ubuntu.com/6947126](http://paste.ubuntu.com/6947126).  Since then, I have run Boot-Repair several times allowing it to make changes.  The report files are at:

[http://paste.ubuntu.com/6954443/](http://paste.ubuntu.com/6954443/)
[http://paste.ubuntu.com/6954657/](http://paste.ubuntu.com/6954657/)
[http://paste.ubuntu.com/6954725/](http://paste.ubuntu.com/6954725/)
[http://paste.ubuntu.com/6954851/](http://paste.ubuntu.com/6954851/)

Please note that Boot-Repair never changed the boot.ini file on sda.  It kept changing the boot.ini file on sdb, even when I pointed Boot-Repair to sda.

This is the contents of D:\boot.ini as created(?)/changed by Boot-Repair:

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Windows" /noexecute=optin /fastdetect

It was only after I deleted the C:\bootsect.lnx file and pointed Boot-Repair to sda that I finally got a menu with Ubuntu on it. However, the windows option of that menu doesn't work.  It gives the error message, "Invalid system disk. Replace the disk and press any key."

I hope this helps you understand my dilemma and can offer advice on how I can get DOS, WinXP, and Ubuntu to happily co-exist and boot.  If necessary, I'm willing to repartition my hard drives and re-install my OS's.  However, if I go that route, Ubuntu will not be a player!

---

### Post by Bucky Ball on 2014-02-18
```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(3)\**WINDOW S**
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="**Windo ws**" /noexecute=optin /fastdetect
```

The gaps in the two I have bolded inspire my curiousity ...

---

### Post by chux.junk on 2014-02-18
Chalk it up to bad typing.  There are no spaces between the letters.  Sorry 'bout dat!

---

### Post by oldfred on 2014-02-18
Boot-Repair would not modify boot.ini.
I do not see how your Windows ever booted it that was the original boot.ini. 
We have seen many XP installs and boot.ini has to call out the correct partitions.
And it just is better if Windows is in a primary partition. Since you have an available one, I would change it.

---

### Post by chux.junk on 2014-02-18
Thanks for you insight, Fred.  If Boot-Repair did not create or change the boot.ini file on sdb then I don't know where it came from.  DOS 7.10 was installed first on a clean disk partitioned into sda1 and sda5.  WinXP was then installed to sda5.  The instructions I referenced told me to create the bootsect.lnx file and copy it to my boot partition and then edit boot.ini.  When I opened boot.ini, it showed the partition(2) entry and a line for C:\DOS.  It wasn't until I was messing with Ubuntu that I noticed the boot.ini file on sdb (as you know, it is a hidden file).  When I opened it for the first time, it showed the partition(3) entry which we know is not right.

I cannot now find the reference I was using to install WinXP into a logical partition but these references may shed some light as to why it can be done that way:

How to create a multiple-boot system in Windows XP
[http://support.microsoft.com/default.aspx?scid=kb;en-us;306559&Product=winxp](http://support.microsoft.com/default.aspx?scid=kb;en-us;306559&Product=winxp)

(Note the second bullet under "Precautions":
"Each operating system must be installed on a separate _**[COLOR=#ff0000]volume[/COLOR]**_."

(See the definition of volume at the bottom of the page):
"Volume - A volume is an area of storage on a hard disk that is either a primary _**[COLOR=#ff0000]or a logical drive in an extended partition[/COLOR]**_."

How to run several Operating Systems on one computer
[http://clubweb.interbaun.com/~mward/multiboot.html](http://clubweb.interbaun.com/~mward/multiboot.html)

Customize Multiboot Startup Options
[http://oreilly.com/pub/h/591](http://oreilly.com/pub/h/591)

So, at this point, I think I need to repair my Windows MBR with Recovery Console.

---

### Post by Bucky Ball on 2014-02-18
I can find no reference to installing XP to a logical partition on your links. In fact, one says 'Create a Primary partition of 5Gigs for Windows' and make the rest an extended partition. I have never heard of XP or any other Windows existing on a logical partition and, as oldfred advised, much less problematic to use a primary.

Logical partitions might be classed as 'volumes' but that doesn't mean Win was designed to install on a logical partition. ;) 

The rule of thumb for Win, and the path of least resistance, is primary partition, first partition, first hard drive (sda1).

---

### Post by chux.junk on 2014-02-18
First reference:
[http://support.microsoft.com/default...&Product=winxp]("http://support.microsoft.com/default.aspx?scid=kb;en-us;306559&Product=winxp")

About half way down the page to the paragraph labeled, "Precautions".

Second bullet: "Each operating system must be installed on a separate _**[COLOR=#ff0000]volume[/COLOR]**_."

Near the bottom of the page, in the glossary of terms: ""Volume - A volume is an area of storage on a hard disk that is either a primary _**[COLOR=#ff0000]or a logical drive in an extended partition[/COLOR]**_."

I'm not going to argue what is the best or the path of least resistance because it sounds like you guys know a WHOLE not more than I do but I can attest to the fact that my setup (DOS on sda1 and WinXP on sda5) works.

I have now run fixmbr and bootcfg /rebuild from Recovery Console, restored c:\ntldr and c:\ntdetect.com from my backups I had fortunately made, and re-booted.  Everything is now back to the way it was yesterday and dual-booting DOS and WinXP perfectly.  I have run Boot-Repair-Disk without making any changes and created the bootinfosummary file.  It is located at [http://paste.ubuntu.com/6958170/](http://paste.ubuntu.com/6958170/).  If you would, please take a look and tell me what I need to do to be able to use Ubuntu without destroying my Windows MBR again.

---

### Post by sudodus on 2014-02-19
I suggest that you continue like this:

0. If you have two hard drives, keep the DOS + Windows drive as it is now, we know it will boot.

1. Then you can install Ubuntu into the other drive. And I would suggest that you disconnect the DOS + Windows drive during that process to avoid messing with it.

2. When Ubuntu is installed and works, you can re-connect the DOS + Windows drive and reboot.

3. If the computer boots from the DOS + Windows drive, change the boot order in the BIOS menu system and reboot.

4. When the computer boots from the Ubuntu drive, create a grub menu entry to ***chainload*** the DOS + Windows drive according to this link (with the 40_custom method)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

---

### Post by oldfred on 2014-02-19
Was not original issue you cannot boot from sdb? If you cannot which some systems are set up that way, then you have to have grub in sda's MBR.

Windows only boots from the hard drive set in BIOS as boot, and the partition with the boot flag which must be a primary partition. Most now are NTFS, but like your old XP install FAT32 will work. All second installs of Windows will put boot files into the primary partition with the boot flag. With Windows you cannot put a boot flag on a logical partition and have the Windows boot loader boot it. There are some work arounds if you use lilo boot loader which boots with boot flag and can have boot code in a logical partitions boot sector.

And we have seen where Windows will not even run fixes on installs in extended partition really prefers to be in primary.

Since you really only have two partitions (extended is just container for sda5), you can easily convert sda to two primary partitions with fixparts (post #20) and edit boot.ini. Then from grub you can directly boot both DOS & Windows. Otherwise you will always have one entry in grub and from boot.ini choose which Windows or DOS to boot.

---

### Post by chux.junk on 2014-02-19
Sudodus,

That sounds interesting but I can't change the boot order in my BIOS to a second hard drive.  It only has the option for one bootable hard drive and that is the first partition of the first drive.

---

### Post by chux.junk on 2014-02-19
Thanks again, Fred.  You've been a wealth of information and I appreciate you sticking with me throughout this process.  However, I've decided to go a different (and much simpler route).  I've got a spare WinXP laptop laying around not being used.  I'll leave the dual-boot desktop we've been playing with alone for now and replace the laptop's OS with Ubuntu.  Then I can play around and learn Linux on the laptop without the possibility of screwing anything else up.  If and when I need some of the power tools on my other systems, I can just plug the laptop into my network and have at it.

Thanks, too, to Bucky Ball and fdrake for pitching in.  Your input has been valuable.

Chuck

---

### Post by chux.junk on 2014-02-19
Hmmm.  Is there a way of marking this thread closed (but not solved)?  The Thread Tools only have an entry for "Mark(ing) this thread as solved..."

---

### Post by sudodus on 2014-02-19
> **chux.junk said:**
> Sudodus,

That sounds interesting but I can't change the boot order in my BIOS to a second hard drive.  It only has the option for one bootable hard drive and that is the first partition of the first drive.

I see.

(I guess it is described in some post, that I overlooked).

---

### Post by oldfred on 2014-02-19
Many threads just stay open. It is only the solved (if OP does add that) that get changed.

If an older laptop, you probably need Lubuntu.

---

### Post by chux.junk on 2014-02-19
Hmmm. Okay.  I hadn't heard of Lubuntu before.  I'll have to check into that.

How old is "older"?  I've got a Toshiba Satellite M45-S265, model PSM40U.  I can't find a date it was assembled.  It came with WinXP Professional.

---

### Post by oldfred on 2014-02-19
Full Ubuntu needs a fair amount of RAM and good video card/chip processor. But I run Ubuntu on my laptop from 2006 with 1.5GB of RAM and Intel default video. But I do not run Unity as it is slow, but install fallback which is a bit lighter.
Really old PCs get into only 32 bit or PAE issues. Newer kernels support only chips with PAE.

       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)


 8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)

---

### Post by sudodus on 2014-02-19
> **chux.junk said:**
> Hmmm. Okay.  I hadn't heard of Lubuntu before.  I'll have to check into that.

How old is "older"?  I've got a Toshiba Satellite M45-S265, model PSM40U.  I can't find a date it was assembled.  It came with WinXP Professional.

I checked the specs via internet. If less than 1 GB RAM you should definitely use Lubuntu or some other alternative for old computers. If 1 GB RAM or more you might also try Xubuntu. See also the first and last posts of this thread, where some other alternatives are also described
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by chux.junk on 2014-02-19
Well, looks like I'm right on the cusp so I'll be doing a lot of reading about Lubuntu.

What I've got:

Toshiba Satellite M45-S265, model PSM40U
Intel Pentium "R" 1.60 GHz processor
2.0 GB RAM
100 GB ATA HDD
BIOS 1.80, 8/11/2005

---

### Post by sudodus on 2014-02-19
Download Lubuntu 13.10 (the 32-bit desktop iso file) and try it (run it live without installing).

Before you decide, you can do the same with Xubuntu and some other alternative, if you have a good internet connection.

---

### Post by chux.junk on 2014-02-19
Thanks, sudokus.  That's a good suggestion and I'll try it.

Fred - Holy Cow!!  How do you know all this stuff?  It'll take me weeks to read through and absorb all that Lubuntu information; but it's something I'm eager to do.

In reading the information provided by sudodus, I see a lot of reference to Physical Address Extension (PAE).  What is it and how do I tell if I need to be concerned about it?

---

### Post by sudodus on 2014-02-19
I don't think you need to worry about PAE. If the link I found about your laptop is correct, it is just a bit newer than the Pentium M CPUs without PAE flag (the **Front Side Bus**  533.0 MHz tells me about that).

---

### Post by chux.junk on 2014-02-19
Thanks!  That had me concerned.

Now, back to my reading!

---

### Post by Bucky Ball on 2014-02-19
As we don't have a 'resolved' button please mark this thread as solved and post a new thread with a descriptive title in the appropriate section for any further questions/issues. Where you're heading now has nothing to do with the thread title here and any questions asked re. your new quest buried 40+ posts deep will receive a much better response in a new thread. 

Good luck.

---

### Post by chux.junk on 2014-02-19
Thanks, Bucky.  Will do.

---

