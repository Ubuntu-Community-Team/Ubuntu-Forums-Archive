---
title: "New Install Borked WIN 10"
date: 2021-06-30
forum: Installation &amp; Upgrades
---

### Post by ToshibaLaptoplinux on 2021-06-30
For what its worth...I was an Ubuntu user back in the day. So after about 15 years or so decided to see how it was doing nowadays. 

Did a quick install from the LiveCD from a USB. Nothing fancy install wise. I just used the Installer. Even kept the default suggested partition allocation. I did select Yes when the installer notified me that a "Win install was detected would I like to install next to it?" .

When I boot it does see the Win partition and if I select it runs the Win auto repair dialogue and fails. 

My data is still there because I can mount in Ubuntu and view but it is encrypted so useless unless can get the Win 10 part back up.

Any ideas suggestions?

---

### Post by TheFu on 2021-06-30
Is dual booting "simple" when either OS is encrypted?  Does the release notes cover that situation for the release you are running (you didn't say).

Dual boot is inherently dangerous. Always has been. For years, MSFT would wipe Linux off the drive during installation.  It was this standard practice that got me to use virtualization rather than dual booting.  Over the years, my host OS has changed from Windows to Linux, but I'm still running both, just with Windows as the guest VM and Linux as the host/hypervisor.

>  Any ideas suggestions? 
Do you have backups that can be restored?
Windows issues need to be fixed by Windows tools.

---

### Post by yancek on 2021-07-01
You haven't indicated which version of windows you are running nor did you indicate if windows and Ubuntu were both installed in UEFI mode or Legacy mode or if you mixed installs.  If you haven't resolved this problem, at least post that information.

---

### Post by TheFu on 2021-07-01
Title says win10. The other info would be useful.

---

### Post by ToshibaLaptoplinux on 2021-07-01
Sorry about that. I am running Windows 10. Both WIN10 and Ubuntu were installed in UEFI mode. I used the Ubuntu-provided "installer" tool thinking that would be the simplest and it went off without a hitch until I test booted into both partitions. Ubunto...no problem. Win10...borked... It did prompt re Secure Boot and I did provide a requested password for Ubuntu to set it up.

---

### Post by ToshibaLaptoplinux on 2021-07-01
Understood and I actually agree in principle but in that case wouldn't it be wise to put that info in the Installer when prompting that Win is detected would you like to use both?

---

### Post by ToshibaLaptoplinux on 2021-07-01
Yes, I am backed up. But they are encrypted under Win. I can mount and see the encrypted files with no issue. The best solution is to be able to get the WIN 10 partition to boot.

Could Ubuntu have borked the MBR/Boot Configuration Data?

---

### Post by oldfred on 2021-07-01
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair cannot fix Windows issues, but may show details we need to evaluate configuration.
Boot-Repair's main fix is just reinstall of grub or update grub menu.

---

### Post by ToshibaLaptoplinux on 2021-07-01
> **oldfred said:**
> Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair cannot fix Windows issues, but may show details we need to evaluate configuration.
Boot-Repair's main fix is just reinstall of grub or update grub menu.

Thank you Old Fred. Much appreciated. Here is the pastebin...

[https://paste.ubuntu.com/p/7GmD8264H5/]("https://paste.ubuntu.com/p/7GmD8264H5/")

---

### Post by TheFu on 2021-07-01
> **ToshibaLaptoplinux said:**
> Understood and I actually agree in principle but in that case wouldn't it be wise to put that info in the Installer when prompting that Win is detected would you like to use both?

In the last 15 yrs, Microsoft has made all sorts of changes to the way that Windows works. They don't exactly have any history attempting to work with Linux distros for a great boot experience. You may recall when Windows would wipe any prior Linux installations.  I do.   Then we have vendors who don't follow the standards for UEFI booting. I can't recall if my toshiba or acer laptop required a manual copy of the efi-stub to boot Linux, but it was one of those.  I don't think Windows is nearly as hostile towards different OSes as they were, but it is impossible for them (or anyone) to test every possible combination.

Some of the changes: UEFI, Secure Boot, Windows 8+ doesn't close file systems anymore, added advanced file systems that use volume managers and dynamic resizing, added disk encryption and GPT support. That are all huge changes, each needs to be reverse engineered to even work. Alas, SecureBoot and UEFI booting can work with some systems. Dynamic disk volumes under Windows can be mounted, but aren't fully supported.  Disk encryption is 1 OS per system - I think - at least for easy setups. The Ubuntu encryption setup in the installer is full-disk-wipe only.  People do manually configure it in more complex situations, but not me. Not closing file systems between reboots is something Linux cannot handle. In that situation, it punts.  That's a Windows failure with no known work-around except to boot into Windows and disable it.

Rather than dangerously dual booting, perhaps you'd consider using a virtual machine?  Today, computers have so much excess RAM, excess storage, excess CPU available that for many workloads, using a virtual machine is 100% fine - even good.  It doesn't risk the system boot either, since the VM runs in a well contained storage area under well supported virtual hardware.  Some of us have been doing this since around 2007-ish.  Abstracting away hardware issues into a VM means never having to fight with drivers, since only the most well-supported devices with extremely well-supported drivers are used in hypervisors.

I understand that Microsoft will update boot settings and re-enable some of the things that break Linux dual boot environments a few times each year.  Using a virtual machine avoids those issues too.2

Just putting out alternatives to be considered.

---

### Post by ToshibaLaptoplinux on 2021-07-01
Could it be this?

> nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, nvme0n1p3 
                       has 189589503 sectors, but according to the info from 
                       fdisk, it has 564632681 sectors.
    Operating System:  
    Boot files:        

---

### Post by oldfred on 2021-07-01
If NTFS is resized, it then needs chkdsk to update PBR so sizes match.
Run chkdsk from your Windows repair/recovery flash drive.
Or you may be able to directly boot Windows from UEFI boot menu and f8 into its own internal repair console. 

Did you mention what brand/model system? 
Some require unique settings.

You show a second small SSD. Often Optane or Intel RAID.
Even if  not Asus may be similar Optane issue.
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

Or:
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483)

---

### Post by ToshibaLaptoplinux on 2021-07-01
> **oldfred said:**
> If NTFS is resized, it then needs chkdsk to update PBR so sizes match.
Run chkdsk from your Windows repair/recovery flash drive.
Or you may be able to directly boot Windows from UEFI boot menu and f8 into its own internal repair console. 

Did you mention what brand/model system? 
Some require unique settings.

You show a second small SSD. Often Optane or Intel RAID.
Even if  not Asus may be similar Optane issue.
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

Or:
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483)

I'll give chkdsk a try and YES...this laptop does have an Optane small SSD! Looking through the links now. Running and HP Spectre 360 15 inch

---

### Post by tea for one on 2021-07-01
Alternatively, this is a recent PC and you may be able to boot into Windows 10 via the UEFI shell?

Do you have a UEFI shell in your UEFI set-up?

---

### Post by oldfred on 2021-07-01
Seems like HP used 360 for many models. Not sure how related they all are.

HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by ToshibaLaptoplinux on 2021-07-01
Do we know that it is the Optane "Feature" that is causing the failure to boot WIN 10 issue? And if so, just so I can understand, what did the Ubuntu Installer "do" that created the problem. I am only asking because my immediate priority now is just to get Win back up and running. Thanks for the assistance everyone

---

### Post by ToshibaLaptoplinux on 2021-07-01
> **oldfred said:**
> Seems like HP used 360 for many models. Not sure how related they all are.

HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

Thanks. I'll take a look at these and see if it is the cause and if I can suss out what's going on.

---

### Post by tea for one on 2021-07-02
> **ToshibaLaptoplinux said:**
> Do we know that it is the Optane "Feature" that is causing the failure to boot WIN 10 issue? And if so, just so I can understand, what did the Ubuntu Installer "do" that created the problem. I am only asking because my immediate priority now is just to get Win back up and running. Thanks for the assistance everyone

If Optane is enabled, a dual boot installation sometimes falls over after Ubuntu is installed with a grub failure.
i.e. Windows boots but Ubuntu does not boot.

e.g. [https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)

It looks like your issue is connected to an encrypted Windows 10 because the boot-repair report only shows one OS detected [COLOR="#0000FF"]Lines 72 - 74[/COLOR].
However, your Windows boot manager is still present [COLOR="#0000FF"]Line 93[/COLOR].

Booting from a UEFI shell is a bit fiddly but possible. Do you have a UEFI shell?
Possibly, you can try to access, decrypt, repair using a Windows 10 bootable USB?

---

### Post by ToshibaLaptoplinux on 2021-08-23
Hello all. My apologies for the long silence. It has taken me some time and considerable effort to suss out what was going on and more importantly what caused my issue.

VERY long story short, as best I can make out, Intel implements Optane as a form of RAID. During the installation of Ubuntu, the RAID was broken and some data that was critical was lost. Most likely during the partitioning phase. I was able to duplicate the problem on a test box. Lesson learned.

Maybe there should be a warning/FAQ concerning Intel Optane and the Ubuntu Installer? 

Anyway, I appreciate the feedback everyone gave me.

Oh yeah, that means the Win10 data is unrecoverable.

---

### Post by oldfred on 2021-08-23
I have seen one or two posts where users said the installer did complain about Optane or RST and suggested turning it off.
Probably one of the very newest Ubuntu versions.

Not sure how it knows Optane if it cannot see drive?

---

### Post by ubfan1 on 2021-08-23
You might try a Windows forum for the decryption problem.  I know the default (new machines) come with encryption, using some of the PCR registers -- and critically, if you don't back up the key (like create a Microsoft Account just for this purpose, or use one of the other four ways to get to the Volume Master Key), you only hope would be to try and restore your config so the TPM's PCR config is the same as it was.  What changes the PCR registers?  Not sure, could be a firmware update, or even a disk swap.

---

### Post by not-published on 2021-08-25
Neither freeBSD nor Ubuntu i just recently installed borked Win10.

However Win10 OVER-WROTE my boot partition on A NON-WINDOWS separate hard-drive.  Took me a while to learn unix rescue disk commands to get back into freeBSD since I am not really a freeBSD user.

Ubuntu doesn't "write over" Win10's EFI unless you tell it to (via not reading the directions).

Win10 is pretty clear:  you put in your Win10 USB and it will repair it's boot manager.  (you get no boot manager if you didn't install win10 with EFI enabled in the BIOS - i learned that the hard way by;  not reading the directions :)

So really: I don't see what the question is.  Win10 has very clear web frontage that it will automatically fix this for you.

Your question should be:  should I make an ubuntu recover disk or re-install ubuntu?  What option during install should I have used?  (i suggest the "i want to do something else ... choose boot drive or usb for boot loader" option btw.  but i suggest reading the directions)

---

