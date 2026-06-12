---
title: "How to either delete Grub or modify Grub to include Win7 as an option"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by thrashercharged on 2015-09-09
I'm a total newbie to Linux, here's the deal:  I've a Dell M6800 with 2 physical HDs: SK hynix 256GB primary drive and a 1TB Toshiba secondary drive.  This is a work laptop (belongs to my employer).  This is what Ubuntu gives via "Disks": 

The primary SK drive:
Partition1: 315MB HPFS/NTFS bootable, /dev/sda1, contents unknown (I assume due to encryption)
Partition2: 256GB HPFS/NTFS, /dev/sda2, contents unknown
I have Win7 installed on Partition1 of this primary SK drive the entire drive is encrypted (because it's a work laptop)

The secondary Toshiba drive:
Partition1: Filesystem 20GB (15 GB free), dev/sdb1, Bootable Linux, EXT4 (version 1.0) mounted at Filesystem Root
Partition2: Linux Swap 2GB, dev/sdb2, Swap Version2
Partition3: MS_Drive 401GB HPFS/NTFS, dev/sdb3, contents NTFS - not mounted
Unallocated free space: 577GB, /dev/sdb

The Toshiba previously had Ubuntu 12.x installed but it was never fully working.  In the boot order, the primary SK drive was first and it would both successfully into Win7.  If I changed to boot order to boot off the secondary Toshiba, Grub 2.02 would come up, with the only boot option being Ubuntu.  If I tried booting into Ubuntu some error would occur - I forget what, never worried about it, I just always booted with the primary SK drive into Win7.  I was never able to successfully boot into Ubuntu 12.x with this setup.

Last night I installed Ubuntu 14.04 LTS using the AMD64 version and chose to replace the previously installed 12.x version (not a clean install - the option where you replace 12.x wtih 14.04 and keep your settings, etc.. Now here's my problems:

1.  Grub has now been installed onto my primary SK drive, with the only option being to boot Ubuntu off the Toshiba.  Win7 is not an option.
2.  If I change the boot order to boot off the secondary Toshiba, I get a *error*: symbol '*grub*-term-*highlight*-color' not found

My most pressing problem is I need to be able to boot into the encrypted Win7 as this is what I need to do my work (and it's a work laptop).  I'm a bit pissed that the Ubuntu update modified anything to my primary SK drive at all as I specifically did not want that to happen (it being an encrypted drive and all) and I'm still not understanding how it was able to put Grub on it as it's all NTFS.  How can I remove Grub and hopefully not affect my encrypted Win7 install?  i.e., how can I get back to booting into Win7 like before when I select the SK drive as my boot device?

If I can't remove Grub, can I at least get the encrypted Win7 to show up as an option so I can boot into it?

How can I fix the Grub on my secondary Toshiba drive to make it work?  I googled that error and apparently there's a bug in the Ubuntu 14.04  installation that has something wrong with respect to Grub that causes  this  '*grub*-term-*highlight*-color' not found error.  I'm too much of a newbie to understand the fixes that have been presented to fix this error - I need more of a step by step along with where to download these Grub install or Grub repair files.  

Ideally, what I wanted to do was to keep my primary SK drive untouched and install Ubuntu on my secondary Toshiba and manually switch between the 2 drives in BIOS to select which OS to boot to (Win7 for work, Ubuntu for home), which is what I thought I was doing but Ubuntu somehow decided by itself to put Grub onto my primary SK drive (did I mention I was pissed about that?).

But seriously, thanks for any help anyone can give!

---

### Post by oldfred on 2015-09-09
Grub always installs to drive specified as sda, unless you use Something Else and choose drive that is sdb.
Your Windows has/had a proprietary boot in MBR. I doubt if encrypted it was the standard Windows boot MBR. But normally grub will not boot encrypted Windows?
What encryption do you have, it may have a tool to repair it? 
[http://truecrypt.sourceforge.net/](http://truecrypt.sourceforge.net/)

Do you have a backup of the MBR for your Windows? Or procedures to recover it?

You must install grub to the Ubuntu drive's MBR. You probably have the old copy of grub there and because it is different version, it will not boot. You must also update the parameter that grub uses on reinstall/update. If you get a major grub update, it will just reinstall there. And if initial install was to sda, it will just reinstall to it.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by thrashercharged on 2015-09-09
Thanks @oldfred for the quick reply!

"Grub always installs to drive specified as sda, unless you use Something Else and choose drive that is sdb."
I wish I'd known that.  What is this "Something Else" you're referring to?  Was this the last choice on the Ubuntu installation menu?  I recall something about a custom install and looked at it, but didn't really know where to go from there.  I (obviously wrongly) assumed if I just updated my 12.x Ubuntu it'd only overwrite what was on the sdb drive and not touch the MBR on the sda.

"What encryption do you have, it may have a tool to repair it?  Do you have a backup of the MBR for your Windows? Or procedures to recover it?"
Unfortunately I don't know and don't have a repair tool.  My employer's IT dept does all this, we have not control over it or ability to mess with it.

"You must install grub to the Ubuntu drive's MBR. You probably have the  old copy of grub there and because it is different version, it will not  boot. You must also update the parameter that grub uses on  reinstall/update. If you get a major grub update, it will just reinstall  there. And if initial install was to sda, it will just reinstall to it."

I assume the Ubuntu 14.04 install iso doesn't automatically update Grub?  Does Ubuntu always need Grub? I have no intention of dual booting with this HD, can I get rid of Grub?

Ok, I figured out how to get a command line via the terminal.  I'm a bit fuzzy on what you meant in your instructions, am I correct in my understanding below?

To see what drive grub2 uses, enter this in the terminal command line:
sudo debconf-show grub-pc 
Use the above line (grub-pc) only if you're using legacy BIOS and not the newer UEFI
Look for this line: grub-pc/install_devices:
and see which drive it references, it will show drive model & serial number

To see drive info type in:
sudo lshw -C Disk -short 

What does this line below do?
    sudo grub-probe -t device /boot/grub

I get the response "/dev/sdb1"

   "To get grub2 to remember where to reinstall on updates type in:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions"

Since I'm using BIOS, I'd use grub-pc and not grub-efi-amd64, right?  Because efi-amd64 is for UEFI?

Also, when you say "do not choose partitions", is that a question asked after you've chosen your drive and accepted?  I'm wondering because I get the choice of either sda, sdb (which I assume means the whole drive) or sdb1 (which is the 1st partition of sdb, right?).  Are you saying not to choose that partition (even thought that's the partition when my Ubuntu is installed) but to choose the whole drive (sdb in this case).

Lastly, since I don't need Grub on sda, is there any way to get rid of it and "undo" the installation on sda?

Sorry for all the newbie questions!

---

### Post by oldfred on 2015-09-09
Better to copy & paste.
In Unity search for terminal. 
sudo gives you temporary admin control of system to change system files. password is whatever you used to install it, and will not be shown as you type it.  Of if live installer there is no password, just hit enter.

Grub/UEFI/BIOS does not know about sda, or sdb drive. BIOS sees drives by SATA port and reports that to grub/ubuntu. Grub sees drives as hd0, hd1 etc or by full drive name, model, serial number. So hd0 usually is sda, but not necessarily. Some systems promote a flash drive to sda. So Ubuntu changed to using UUIDs which should be unique to drive/partition.

If you want to boot Ubuntu, you just about have to have grub2. There are other boot loaders but grub2 is the standard. It is both a boot manager or menu and the boot loader to start up Ubuntu.

The other safe way to make sure you do not damage another drive is to physically disconnect it, so you for sure are only installing to the drive you expect. 
Also some BIOS allow you to turn off a drive, so the same as disconnecting it.

---

### Post by grahammechanical on 2015-09-09
To open a terminal click on the Ubuntu symbol at the top of the Launcher (panel at the left side of the screen). That opens the Dash. Or, tap the Windows key and search for terminal. Once we know what drive Grub is installed on and whether Windows is sda (the first drive) or sdb (the second drive). Then we can tell you what command to run to install Grub on to the Ubuntu hard disk which should give you an option to load Windows.

For your information, the main componant of a boot loader resides in a special area of the hard disk called the Master Boot Record (MBR). The format of the hard disk is irrelevant as the MBR is not included in the space that is formatted.

---

### Post by thrashercharged on 2015-09-09
Thanks again Fred for replying - I think you must have replied as I was editing my last post.  I did figure out how to find terminal and run command lines in the meantime.  I understand about the need for having Grub, and I think I've successfully installed it on my secondary Toshiba drive following your instructions.  I used grub-pc and not grub-efi-amd64 and it must have worked, and I took a chance and chose the whole drive and not the Linux partition assuming that's what you meant.

So is there any way to uninstall Grub from my primary drive?

---

### Post by oldfred on 2015-09-09
Grub-pc is the BIOS boot loader version of grub.
grub-efi-amd64 is the UEFI boot loader version.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by thrashercharged on 2015-09-09
Thanks [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") for the reply. I've verified that sda is the encrypted win7 drive and sdb is the Linux drive, and I was successful in getting Grub installed correctly on sdb - I physically took sda out and only left sdb in, and booted off sdb into Ubuntu (that's how I'm sending this message). 

Thanks for clarifying the fact that the MBR isn't in the space that's formatted - I never knew that.  Now I'm wondering if I can uninstalll Grub from sda in the usual ways (either repairing with fixboot and fixmbr) or burning a Super Grub ISO disc and not damage my entire disk encryption the IT dept put on and be able to still boot into that encrypted Win7 after Grub is gone.

I don't have a Win7 rescue disk (since the IT dept handles those things) so maybe burning a Super Grub ISO is my only choice.  Any recommendations on how to best erase Grub from sda and retain my encryption stuff?

So if my Win7 wasn't encrypted, would the Grub install on sda have included Win7 and allowed me the choice to boot into either Win7 or Ubuntu?  Again, this wouldn't have been my choice because I'm really trying to keep Win7 and Ubuntu totally separate and have no trace of Ubuntu on that primary sda drive - I want it to be totally a Win7 machine unless you know to change the boot order and boot off that secondary drive.

"Grub always installs to drive specified as sda, unless you use Something Else and choose drive that is sdb."

What is this Something Else?
 
I do hate to gripe but if it were made more clear to a Newbie installing Linux for the first time that
1.  Grub has to exist - that it's not just for dual booting, that it's both a boot manager or menu and the boot loader to start up Ubuntu
2.  Installing Ubuntu will cause Grub to be installed onto sda **always even though I specifically told it to install Ubuntu over an older version on sdb and no Grub existed on sda and it gave me no warning that i would be writing to the MBR of sda!**
3.  Maybe I should have used this "Something Else" but it clearly wasn't very evident (to me) in any documentation I found for installing Ubuntu.

Knowing this would have saved me (and perhaps other Newbies) a lot of headache.  I'm sure I'm not the only one that's wanted to put Linux on a second drive and not change anything on the primary drive at all, and use the BIOS to choose which drive to boot.

Thanks again for all the quick responses and help - y'all are great!

---

### Post by oldfred on 2015-09-09
Most new users pick the auto install options. And if a single drive and standard installs it usually works. 
But when you have more than one drive or any special case (encryption) you need to use manual install, so you have total control over process, but new users often do not even know what a partition is, much less that they need at least / (root) & swap.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

[       ]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html")
 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

You can use Boot-Repair to install the syslinux boot loader which is a standard Windows type boot loader. If you used a standard MBR, it should also work. But most encryption systems also control MBR.

If Supergrub boots your Windows, then it has a standard MBR.
You can from Ubuntu on sdb, install the lilo boot loader which is still another boot loader that works like Windows. It is a full boot loader, but you only want the part that installs to the MBR.

       
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

### Post by yancek on 2015-09-09
The MBR is on the first sector of the hard drive and is outside any partition regardless of the operating system installed.

> 
"Grub always installs to drive specified as sda, unless you use Something Else and choose drive that is sdb."

You don't indicate which Installation Type method you use.  The "Something Else" option is what used to be referred to as Manual and is the option which gives the user the most control over the installaation.  You can select drives/partitions on which to install and of course have the option of where to install the bootloader.  On the Installation Type window, near the bottom you will see "Device for bootloader installation".  Just below that you will see "/dev/sda" and probably the name of the drive.  This has been the default behavior with Grub2 (which you are using) and Grub Legacy, the predecessor to Grub2.

Grub "GRand Unified Bootloader' has been the bootloader of choice for most Linux systems for well over a decade.  Others are LiLo (Linux Loader) which is still used by a few distributions (Slackware and some derivatives) and syslinux/isolinux which is primarily used to boot a CD/DVD/flash drive.

>  **always even though I specifically told it to install Ubuntu over an  older version on sdb and no Grub existed on sda and it gave me no  warning that i would be writing to the MBR of sda!**

Which Installation Type option did you choose?    I would guess you used the semi-auto-install, Install Alongside windows?   The second link below to the Ubuntu site gives a simple explanation of Installing Alongside windows and I don't see any option to select where to install the bootloader.   There doesn't appear to be that option.  Take a look at the link below which is a very detailed tutorial on installing Ubuntu and has  a step by step guide on dual booting if you scroll down the page.  It also has a section further down on bootloaders.

  [B][http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

I'd suggest reading through at least the two sections mentioned above.  

[/B][http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by thrashercharged on 2015-09-15
Thanks again for everyone's help with this - I've read and bookmarked the suggested sites and have a much better understanding of installing Grub and Ubuntu, but I still wish the "official" Ubuntu sites would've had this info or links to the dedoimedo.com guides.  Sorry I didn't thank people sooner but the IT dept has had my laptop since those postings to reimage my encrypted (Symantec Full Drive Encryption) Win7 drive as I was not able to "undo" the Grub installation on that drive's MBR at all as no trace of any Win7 boot stuff was found due to it being encrypted.

"[COLOR=#000000]Which Installation Type option did you choose? I would guess you used the semi-auto-install, Install Alongside windows?"

No, since it detected a previous installation (Ubuntu 12.x) on sdb, there was an option to upgrade that 12.x to Ubuntu 14.04.  I should mention that that Toshiba sdb drive was at one point the primary sda drive in another laptop when it had Ubuntu 12.x installed.  That's how I ended up with sda being a Win7 drive (with no Grub) and a sdb with Grub and Ubuntu 12.x installed.

[/COLOR]So I assumed that upgrading 12.x to 14.4 on the sdb drive would not write Grub to the sda drive.  Seemed to be a logical assumption at the time since it was an upgrade and Grub was currently existing on sdb and no Grub was on sda.

Anyway, everything is good now (except I don't understand how some Linux things work/don't work, but I'll start another thread for that.) and I'm able to boot Win7 off sda and Ubuntu off sdb by switching the boot drive in BIOS.

---

