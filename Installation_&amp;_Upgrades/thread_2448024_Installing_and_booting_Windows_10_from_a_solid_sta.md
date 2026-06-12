---
title: "Installing and booting Windows 10 from a solid state drive"
date: 2020-07-30
forum: Installation &amp; Upgrades
---

### Post by Rockwell32001 on 2020-07-30
Hi.  I couldn't find a separate thread on this, so here goes:  I'm putting Windows 10 on a separate SSD for a fun environment at lower cost than buying RAM for a virtual machine.  Gaming, that sort of thing.  Ubuntu is my every day distro.  My question is how do I go about installing 10 on the SSD and booting from it without screwing up this system?  Thanks.

---

### Post by oldfred on 2020-07-30
Make sure you install Windows in same boot mode as Ubuntu, or both UEFI/gpt or both BIOS.
Windows installs boot loader & boot partition to drive set as default in UEFI/BIOS. It does not correctly see Linux in most cases and has been known to just overwrite the beginning of the default drive even if it is a Linux partition.

I would just unplug either physically or logically in UEFI and then install to blank drive.
I might keep Windows as first drive as SATA port order determines drive order.

Some UEFI forget Ubuntu/grub entries in UEFI when a drive is disconnected.You may need to use efibootmgr to install a new UEFI boot entry or reinstall grub which also runs the efibootmgr command.

Be sure to have good backups, including ESP.
And have current version live installer of Ubuntu for your install.

---

### Post by Rockwell32001 on 2020-07-31
Yes, I was planning on unplugging the main linux drive.  After that, I should be ok?  Thank you.

---

### Post by Rockwell32001 on 2020-08-03
So, I finally got the update done, and something went wrong.  I can boot into Windows 10 on the solid state or Ubuntu on the old hard drive, but I have to go all the way into BIOS/UEFI to pull it off.  I think GRUB got erased, but I'm not sure.  Everywhere I've found on the net has addressed a full, fresh install and not this scenerio (existing system+sidegrade).  How do I figure out what's going on?  Thanks.

---

### Post by CelticWarrior on 2020-08-03
If you can boot both then, in Windows, make sure Fast Startup is disabled. Then set the UEFI to boot from Ubuntu and run 'sudo update-grub'. Window should now be detected and added to the Grub menu.

---

### Post by Rockwell32001 on 2020-08-04
So, my system is destroyed, and I don&#8217;t know how to get it back.  Everything I have found is for dual boot on one drive, not two.  Grub didn&#8217;t load correctly, it didn&#8217;t reinstall through command line, and the full reinstall failed because grub didn&#8217;t go where it was supposed to.  HELP!!!!

---

### Post by Impavidus on 2020-08-04
Can you boot a live disk, install [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and create a bootinfo summary? That may tell us what's going on.

---

### Post by Rockwell32001 on 2020-08-04
No idea how to do that (install a program to a live cd).  I&#8217;m new to this.  I can&#8217;t get a hold of my hackerspace, and this is a turnaround.

---

### Post by oldfred on 2020-08-04
You install it only in memory.
See Second Option on instructions on how to use Boot-Repair.

> sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

---

### Post by zebra2 on 2020-08-04
It is my opinion that a linux "home" should always be on it's own partition /home.  Root should be on it's own partition /root.  Ubuntu doesn't need UEFI for its self. It is only necessary if you are dual booting Windows with UEFI on Windows.  You don't have to have UEFI on Windows for it to work given that the HD is 2t or less. UEFI is to protect against Windows Root Kit Virus.  
If you format your Windows to NTFS it will automatically install without UEFI because NTFS will by default be MBR. If you dual boot Ubuntu, Ubuntu should install without UEFI if "boot" is pointed to MBR. In this case Ubuntu can use a choice of partitions, usually EXT4.  Hence you will have Windows and Ubuntu dual booting without UEFI.  In either case you will want to turn off "Fast Boot" in Windows because Fast Boot is a partial "sleep" shutdown and can allow Ubuntu to boot when Windows is not actually completely  shut down which can result in an unstable situation.  You will also want to verify that Fast Boot is still turned off after a Windows update. On the other hand if you want UEFI on the Windows partition you will have to install Ubuntu in UEFI even though normally it would not have a use for it. 
The bottom line in all of this is BACKUP you home partition before you do anything. Backing up Windows can be a complicated procedure since it doesn't store all of its data in the same place. Hence you may be stuck with needing to backup the entire Windows drive depending on how you use it.
I personally run both Windows and Ubuntu without UEFI since I only use Windows a couple of times a year. The install is simple and uncomplicated. Nice thing about all of this is you have choices.

---

### Post by oldfred on 2020-08-04
How you boot install media, UEFI or BIOS, is then how it installs.

The newer gpt partitioning is an improvement over the 35 year old MBR, but Windows in BIOS mode only installs in BIOS mode to MBR. If you force install that converts drive from gpt to MBR or vice-versa, then it will erase drive.
I started using gpt with Ubuntu in BIOS boot mode in 2010, before PCs were UEFI.

Newer Windows 10 with its fast start up is difficult to dual boot on one drive. It keeps turning fast start up back on with updates and then grub will not boot it. Bit of a hassle to install Windows boot loader to MBR, fix Windows & restore grub. With 2 drives (and Windows boot in one & grub in other)  or UEFI then much less hassle.

---

### Post by pbear42 on 2020-08-04
> **Rockwell32001 said:**
> ... full reinstall failed because grub didn’t go where it was supposed to.  HELP!!!!
Unlikely this is the problem if you unplugged the Ubuntu drive when installing Windows.  Rather, sounds like an NVRAM problem.  
With both drives attached, boot a live session, run efibootmgr -v, and report the output,

---

### Post by Rockwell32001 on 2020-08-05
So, partial solution.  Windows and Ubuntu will now both boot.  However, updating to 20.04 is being problematic (I have an 18.0x cd).  Restarting after the update hangs the system and does bad things.  I hope this hard drive is good.  If anyone else tries this, these are the steps:  Here's the process.
&#8226; Remove the linux drive. 
&#8226; Re install windows
&#8226; Remove the windows drive.
&#8226; Re install Linux
&#8226; Plug both drives in, set the BIOS to boot to the Ubuntu drive
&#8226; use sudo os-prober to check for a windows install. If you see it run: sudo update-grup
&#8226; Done. 

Please note:  where it says remove, REMOVE!!  Well...at least Window$ will work for DEFCON.  A simple install takes a week of rocket surgery.

---

### Post by Rockwell32001 on 2020-08-08
Fully solved.  Had to redownload Ubuntu and burn a DVD.  Not sure why I have crap luck with USB's, but I just do.

---

