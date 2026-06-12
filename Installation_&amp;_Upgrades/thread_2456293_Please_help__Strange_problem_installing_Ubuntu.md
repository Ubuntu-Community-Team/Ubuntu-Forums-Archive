---
title: "Please help:  Strange problem installing Ubuntu"
date: 2021-01-08
forum: Installation &amp; Upgrades
---

### Post by jeffjot on 2021-01-08
While installing Ubuntu, most recent version (20) I can never get past the 4th screen.    
Its on a brand new computer which has Windows 10, and I've already shrunk the filesystem to create a dual boot, and there is a huge (700 gig) unallocated space on the disc.

I boot Ubuntu off a bootable USB iso, click the install Ubuntu icon.... go past Language, Keyboard, and Install Multimedia Codecs.   And thats where things tank.

Instead of the next screen expected, it goes directly to a page which shows "Installation Type" with a bunch of headers:  Device, Type, Mount Point, Format?, Size, Used, System.

There is a blank white empty space underneath that.

At the bottom is:  "Device for boot loader installation:" and there is only /dev/sda, nothing else selectable on the drop-down.  I'm assuming, /dev/sda is the USB flash drive where the bootable Linux is.

Now, everyone says "SET THAT TO /!"  but there is no possiblity or way to do that.  
Nothing can be typed.  
The only option is to click "Change", and that causes the installation to crash.
What could be causing this?    No instructional walk-thru mentions anything of the sort.

I also can't see any way to view the unallocated space on the hard drive.  I appear to only be seeing the USB stick, nothing more.
?????

---

### Post by SeijiSensei on 2021-01-08
No, /dev/sda is the primary hard disk in the computer.  It's where you want the boot loader to be installed.

---

### Post by GhX6GZMB on 2021-01-08
As SeijiSensei says, sda is your primary disk, but this still has to partitioned.
/ and boot are not the same, boot is a small separate partition with a size of around 1 GB (may vary) that contains the boot loader.

Where you place / and /home etc. is a different issue.

---

### Post by jeffjot on 2021-01-08
I have no choice to go any further is what I am saying.
If I click "Install Now" with the preselected /dev/sda, I get a message:

No Root Filesystem
No root filesystem is defined.  
Please correct this from the partitioning menu

My only option is to click "OK". 
When I click OK, I'm still at the same screen, stuck.

The drop-down allows no other selection.
"Change" and "+" cause the installation to crash.
"-" does nothing.

There is no way forward.

---

### Post by QIII on 2021-01-08
@jeffjot -- given that a picture is worth a thousand words, could you take a shot with your cell phone and post it here?

---

### Post by jeffjot on 2021-01-08
It looks exactly like this:

---

### Post by #&amp;thj^% on 2021-01-08
Looks to me to be a UEFI issue.

---

### Post by jeffjot on 2021-01-08
Uefi?

---

### Post by jeffjot on 2021-01-08
What is it supposed to look like?
Every option goes nowhere.   Except Quit, which of course quits.

---

### Post by #&amp;thj^% on 2021-01-08
Your supposed to see a drive in blank area you show on your photo.
If your still using the live-installer, open a terminal and run: 
```
sudo dmesg | grep "EFI v"

```
If it shows anything your in UEFI mode.
**EDIT:** I just read your first post "New machine with Win 10" your definitely in UEFI.

---

### Post by GhX6GZMB on 2021-01-08
I'm a Lubuntu user, but not unfamiliar with Ubuntu.
I've never seen that screen before, but it seems more like you're in live boot, not installation. And the reference to "loading multimedia codecs" is also strange.

Where did you get the .ISO file for the installation?

---

### Post by jeffjot on 2021-01-08
I tried that and there was no output

---

### Post by #&amp;thj^% on 2021-01-08
Well the only other thing i can add here is, <Bios>>> Secure-Boot, is that disabled?

---

### Post by QIII on 2021-01-08
That appears to indicate that the installer cannot find a partition.  It could be that the partition was created, but it is still mounted in Windows because of the fakery used by Windows to convince you that it is starting more quickly.  It's not "starting" more quickly.  It is resuming from a hybrid sleep mode.  The partition may still be mounted, in which case Linux, and by extension the installer, will not touch it.

When you created the partition, did you quit Windows, go to your BIOS/EFI and disable Secure Boot and Fast Boot, then make sure that only UEFI boot is allowed.

Do that and start Windows.  Shut down Windows.

---

### Post by jeffjot on 2021-01-08
OK will try hang on

---

### Post by yancek on 2021-01-08
Turning off the fastboot and other related options is the first step, then boot into windows and turn off anything related to hibernation.  Linux systems won't mount hibernated operating systems and unless a user manually turns it off, neither Ubuntu or any other Linux will mount it as there is too much likelihood of damage/data loss.  Countles sites explain this in detail.  A link to the microsoft site is below.  It's not a 'strange' problem, very common.

  [https://support.microsoft.com/en-us/windows/shut-down-sleep-or-hibernate-your-pc-2941d165-7d0a-a5e8-c5ad-8c972e8e6eff](https://support.microsoft.com/en-us/windows/shut-down-sleep-or-hibernate-your-pc-2941d165-7d0a-a5e8-c5ad-8c972e8e6eff)

---

### Post by jeffjot on 2021-01-08
The partition it can't find is unallocated space.  Do I need to set it up in Windows, Disk Management maybe as a formatted partition, maybe?

---

### Post by oldfred on 2021-01-08
Do not use Windows, it cannot create ext4 formatted partition for / (root). 

Did you change drive to AHCI? From RAID or Intel RST?
But you first must install AHCI drivers into Windows or else it will not boot.

What brand/model system? What video card/chip?
Have you updated UEFI and if drive is SSD, updated SSD firmware. 

See also link in my signature.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both, You want UEFI boot.
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by jeffjot on 2021-01-08
I'll look it over.
I'm on my 3rd day now, gave up trying to load Linux Mint and now I'm over here.
I've always liked Linux, except its always been such a kidney stone to install and upgrade.  Why has that never changed in decades?  uchhh.
Crimeny if someone only invented a distro that installed as easy as Windows, they would be on every PC in the country

---

### Post by QIII on 2021-01-08
It installs faster than Windows.  I can install Ubuntu and be up and running with all of my software within 30 minutes. Try that with Windows.  The problem is that in designing the hardware for Windows, the OEMs make it hard to use anything but.  You have to learn how to clear the roadblocks first.  Notice that every post so far helping you is directing you how to move a roadblock.  That has nothing to do with Linux itself.

---

### Post by jeffjot on 2021-01-09
>>> It installs faster than Windows >>>

Not for me.  Though I used to work on Windows desktops way back when and loaded things as old as (gasp) Windows 2000 and XP.    It may take awhile but most of that is just letting it load, just pretty straightforward.   Stick in the CD, enter the serial code, follow the prompts.
I've never had that with Linux, though I'd love to say it.   I'm on 3 days now and 2 distros.   I can't get anything to load and I have a brand new 1 TB Dell computer here, Intel Core I-5 preloaded with Windows 10, it seems to be resisting Linux with every byte on its disc.   All I want is to set up a simple boot partition.   The Live instance of Ubuntu boots easy enough off the USB, but the Windows PC won't let Linux touch it.



[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Well it looks like my Windows 10 partition is UEFI, if that helps.   I wonder if this "Boot-repair" procedure might help the installer to recognize the 700 gig unallocated space I have there ready, off the installer?
I still can't get past that blingin' go nowhere screen I attached.  "root filesystem not defined".     Been monkeying with settings all day it refuses to budge.

---

### Post by QIII on 2021-01-09
> **jeffjot said:**
> Not for me.

Again:  You are encountering the roadblocks that stand in your way.  Once you learn to remove them, it will install faster.

---

### Post by deadflowr on 2021-01-09
> **oldfred said:**
> Do not use Windows, it cannot create ext4 formatted partition for / (root). 

Did you change drive to AHCI? From RAID or Intel RST?
But you first must install AHCI drivers into Windows or else it will not boot.
<snip>

More on Intel RST and Ubuntu here:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347]("https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347")

---

### Post by jeffjot on 2021-01-09
>>>Do not use Windows, it cannot create ext4 formatted partition for / (root). >>>

Maybe this is the cause.   I originally "shrunk" the Windows filesystem using the Disc Management feature in Windows 10, then created the unallocated space there. 
Maybe I can launch some other, Linux utility to do this?   And then create a recognizeable unallocated filespace, it can see?

---

### Post by jeffjot on 2021-01-09
Nope, not so lucky.
If I run Gparted off the Live Linux USB, it only shows the USB stick, does not let me see or partition the PC itself.   
there is only /dev/sda available, 15 Gig flash drive.   Nothing else.
As far as I can see, the only way to shrink filesystems, partition or set aside unallocated space on the drive is through the OS already preinstalled on the PC, Windows 10.   Which I did, but then the unallocated space is not recognized by the Ubuntu install.  
In fact, the Ubuntu install only sees the USB drive, also.   The PC itself is not visible.
As far as turning off fastboot, and all the other settings mentioned in the BIOS, I've done all that.  The PC is a fortress and will allow nothing on it but Windows

---

### Post by QIII on 2021-01-09
> **jeffjot said:**
> The PC is a fortress and will allow nothing on it but Windows

Actually, that is possible.  There are models of computers that are specifically set up to make sure only Windows can be installed.

What is the OEM, the model and what are the specs?

---

### Post by jeffjot on 2021-01-09
Surely someone has seen this screen before, and what did you do to resolve?  I just want to get past step 3 in the installation process :/

---

### Post by QIII on 2021-01-09
jeffjot ... If you ask that, then I'm not sure what you think everyone here is helping you to do.

I started doing this computer thing in the 70s -- before Windows was a thing.  Micro Soft (which it was called then before it became Microsoft) was a company that produced a compiler for the Altair computer.  They hadn't even produced an OS yet.  There are those here who go back long before that.  Don't assume we don't have a clue what we are doing.

Thanks.

---

### Post by jeffjot on 2021-01-09
It is a Dell Inspiron 3880 Desktop I5-10400 
If you want more I'll have to reboot Windows back.  Im in the live USB Linux instance now.

---

### Post by jeffjot on 2021-01-09
>>jeffjot ... If you ask that, then I'm not sure what you think everyone here is helping you to do.>>
Just a little frustrated on my 3rd day now.   In fact I think I'm going to give up for tonight.

---

### Post by QIII on 2021-01-09
Dell is an ally of Linux, and in particular Ubuntu.

I would recommend reading through some of Dell's documentation [here]("https://www.dell.com/support/kbdoc/en-us/000131253/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc"), which specifically outlines dual booting, to see if you can find any resolution.

---

### Post by oldfred on 2021-01-09
Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
 Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

you may need 20.10 and then even newer kernel.
Dell often has updated drivers that evenually are included in kernel & then into a distribution. But that can take a bit of time.

Bit older system, issues often common by brand and then if Intel Or AMD by generation of system.
Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)

General UEFI install info in link in my signature.

---

### Post by yancek on 2021-01-09
If you have turned off fast boot and whatever in the BIOS, have you also disabled hibernation (default on windows 10) as explained in the link to the Microsoft site in post 18?  You will never see a hibernated drive from a Linux installer.

---

### Post by tbhesswebber2 on 2021-02-21
I just got a brand new Dell XPS 17 today.  While installing, it says that I need to turn off RST and tells you to open the link from OldFred.  It's important to note that [B][I]not all machines will be able to recognize that RST is the issue.

[/I][/B]On your windows machine, you can go into your Device Manager and then IDE ATA/ATAPI Controllers. In Device Manager, the name of one of my Storage Controller had RST in it, which made it easy to identify.  Be sure to follow the directions in the link to the letter - I screwed up and am now recovering my Windows machine so that I can try again.

> **oldfred said:**
> Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
 Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)


---

