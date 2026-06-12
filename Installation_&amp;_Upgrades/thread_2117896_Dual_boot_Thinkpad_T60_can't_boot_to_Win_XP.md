---
title: "Dual boot Thinkpad T60 can't boot to Win XP"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by nmallam on 2013-02-19
My daughter has a Thinkpad T60p which was running XP.  She tried to intall Ubuntu 12.04.1 as dual boot, but when she selects XP during boot, the system ends up in the IBM/Lenovo Rescue and Recovery program and selecting restart from here seems to end up in a circle (ie can't get to XP).  I guess we've messed up the master boot record, but am unsure what's gone wrong and how to fix it.  Getting back to just XP would be a good result, but working dual boot would be good too.
Anyone come across this before and could offer advice (in very simple language please)?
Ta.
Neil (and Zoe)

---

### Post by oldfred on 2013-02-19
Welcome to the forums.

With Vista grub often reversed the recovery and the system boot entries. But XP should just work.

Best to see details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

### Post by nmallam on 2013-02-20
Hi and thanks for your reply.
I have run the boot_repair info request and the result can be found at the following url:
[http://paste.ubuntu.com/1689424/](http://paste.ubuntu.com/1689424/)
I have not attempted any repair and would welcome your advice as to how best to proceed.

Many thanks,
Neil & Zoe

---

### Post by oldfred on 2013-02-20
BootInfo is not showing anything abnormal as near as I can tell. It has a correct grub boot stanza to boot Windows and Windows looks like it has the correct file structure. 

BootInfo does not show internal Windows issues and cannot run chkdsk on the NTFS partiiton, your need you XP disk to run that. Not sure if you Lenovo recovery offers that or not. Or is that really the Windows recovery with Lenovo's title? If repairs NOT restore is an option run that. Restore may erase system, so do not try that unless you have all your data well backed up.

Not sure why or how you get to a Lenovo recovery.

Windows does have to run chkdsk aftrer a resize to the NTFS partition. If you have not booted Windows since resize then that is what it wants to do.

---

### Post by nmallam on 2013-02-20
Thanks for taking a look at the boot_info.
I had a look at the output, but couldn't make a lot of sense of it.  I was expecting to see the hidden partition where the Lenovo recovery program is booted from, but there didn't appear to be any sign of it, yet this is what gets loaded when I select the WinXP boot option, so it must be there.
I'd like to return the system to the pre-Ubuntu state, is there an uninstall option that can do this for me (including resetting the master boot record)?

Thanks again,
Neil and Zoe

---

### Post by tgalati4 on 2013-02-20
I have a dual-boot T43p with WinXP and Jaunty, sometimes Windows changes the boot flag on the partition.  Check the boot flags on your partitions with gparted and make sure the boot flag is set to the correct partition.  That would be the partition that has grub installed.  You could have grub installed on multiple partitions, but only one partition can hold the boot flag at a time--on a single hard disk.

I find it easiest to boot with a Live DVD and run gparted to change the flag, then reboot.

---

### Post by oldfred on 2013-02-20
BootInfo shows boot flag on sda1, which is correct.

Windows has to have a boot flag on the boot partition. If multiple installs of Windows only one is bootable. 
Grub does not use boot flag and will chainload to a Windows install even if boot flag is not correct as long as Windows has its boot files.
But a few BIOS have to see a boot flag on a primary partition or they do not let you start to boot. Seems to assume Windows. So we suggest a boot flag on a primary partition even if you do not have Windows.

You can easily restore the Windows boot loader to the MBR. If you delete the Linux partitions first you will not boot as grub in the MBR needs more info from the Linux partitions.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

    
But OS-Uninstaller will not remove the partitions. You will need to do that from a liveCD to make sure all partitions are unmounted and may still have to click on swap and right click swap-off as liveCDs like to use swap to speed up processes.

---

### Post by nmallam on 2013-02-20
Thanks for the suggestion, [[COLOR=#000000]tgalati4[/COLOR]]("http://ubuntuforums.org/member.php?u=241895"), but I can see from the boot_info listing that the boot flag is set on the windows ntfs partition.  As I said above, what puzzles me is that there is no sign of the recovery partition in the listing -- could this be because it is 'hidden' (does that have any meaning for partitions?)?
The recovery program has options to do a factory restore or restore from backup, but I don't know how it will cope with a disk that has been partitioned.  There are no XP recovery disks, recovery is achieved via the recovery partition/program (which is not Windows, but I don't know what it's based on -- maybe linux :-) ?
Normally the recovery program is activated by pressing the 'thinkvantage' button during boot -- I can't imagine that WinXP boot would detect this, so it has to be something in the bios -- does the linux install mess with bios?
I'm confused.

---

### Post by oldfred on 2013-02-20
Linux does not change BIOS as that is on Motherboard. BIOS writes data onto drive for any operating system to use to know about hardware.

If system was new enough to be Vista, but downgraded to XP, you might have had a recovery partition. Normal XP installs still gave a Install disk, but with Vista they stopped providing CDs and only had recovery partitions. Many early Vista systems were reconfigured for XP as users still wanted XP, but they usually showed a Vista recovery (really XP) partition.

Since you have no recovery, it either was XP originally or during install the recovery partition was overwritten. Key to activate it may still be there. Not sure if XP partition has some of the software, but full recovery partition is 10 or 20GB and gparted always shows it. Window does not show it and never assigns a "drive" letter as it is not to be used except for recovery.

---

### Post by nmallam on 2013-02-20
Thanks OldFred, I'll try the os_uninstaller (in the morning when I'm not tired (I'm in the UK)).  I'm hoping that this will restore the original windows MBR (was this backed up somewhere during the linux install?)
I wasn't quite sure about removing the partitions.  Presumably I need to recombine the partitions, and I'm guessing that I can use 'gparted' to do this ... is that correct?

Cheers,
(Old)Neil and (Young)Zoe :-)

---

### Post by oldfred on 2013-02-20
Boot-Repair installs a Windows work alike boot loader, not Windows version. It may be copy-write issues. But all MBR does is look for boot flag and jump to PBR for more Windows boot code.

With XP you can use gparted. Any of the newer Windows you should use Windows Disk tools to resize a Windows NTFS partition. Any change to the Windows NTFS partition will require chkdsk, so reboot immediately if you change it and run chkdsk.

You can just change Linux formatted partition to NTFS. Reformatting will erase everything but a second NTFS partition will become the D: "drive" in Windows.

---

### Post by nmallam on 2013-02-20
Thanks for the clarification.  I will try to recover to a working winXP system with a fresh mind in the morning.  I have to say, though, that I'm very nervous about what I'm about to try mainly because I don't have a clear understanding of what went wrong and therefore what I need to do to correct it.  I have found various items on the web suggesting that achieving dual boot on a system that has a recovery partition is not straight forward eg
[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)

I also don't know what happened to the recovery partition? If it has been overwritten, then why do I see the recovery program when I try to boot into windows?  I can envisage removing linux and still having the boot problem of not reaching windows!
I'll let you know how I get on.

Cheers,
Neil and Zoe

---

### Post by nmallam on 2013-02-21
Well it's bad news I'm afraid.  All my worst fears have been realised :-(
I uninstalled linux ok.  I couldn't work out how to merge all the partitions back into one, so just left them.
When I reboot, as I expected, I end up in the Recovery program.  The only option from here was to restore from a backup, so I did this hoping that the restore would fix the mbr, but alas not.  So now I have a laptop that runs the Lenovo recovery program.  Very frustrating!  Windows is there somewhere, but I just can't access it.  
I need a tool that will restore the correct mbr ... any advice?  I'm not really interested in just running linux, I would like my winxp back and working.

Cheers,
N&Z

---

### Post by oldfred on 2013-02-21
Boot-Repair will add a Windows (syslinux) boot loader to the MBR. Use liveCD and install Boot-Repair to that.

Or a XP install disk.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
Or using liveCD you can install the lilo boot loader. Lilo and syslinux are also on most Linux repairCDs.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by nmallam on 2013-03-10
Finally got the laptop back to a working winXP.
I borrowed an xp install disk and did a complete fresh install.  Unfortunately, there must be some missing drivers for the thinkpad in the basic xp install and following installation, I would get a bsod during boot.  Fortunately the fresh install had corrected the mbr (or maybe the boot sector?).  Anyway, I was now able to use the Lenovo R&R program (booted from a cd) to recover the backup that I had taken before installing linux.

So, a happy ending, but I'm disappointed that Ubuntu/linux doesn't provide an uninstall mechanism that puts everything back as it was before installing.
Cheers,
Neil and Zoe.

---

