---
title: "Infinite loop with Gparted &quot;Can't have a partition outside the disk&quot; when upgrading"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by aninkling on 2014-07-02
System configuration:
Window 8.1 on C drive. (dev/sda)
Second hdd (dev/sdb)  This has two partitions:
sdb1:  ntfs 160Gig for general storage
sdb2:  ext4 was the current 12.04 version.  I had reformatted the disk, so 12.04 is wiped out.  I wiped out two partitions and then created one new one, reformatting to the ext4 format.  Following "easylinuxtips" methodology to upgrade to 14.04. At the point where I have the 138Gig partition.  But when I try to set the configuration as root to continue with installation, I get a "Can't have a partition outside the disk".  Note that I have Device for boot loader installation as the /dev/sda.  I suspect this is the problem.  However, the way I have this working now is the way I want to have it work in the future: When the computer boots, Windows 8 gives me a choice of 2 boots, one to windows, one to ubuntu.  If I pick ubuntu, then I get the normal grub loader selection list.  

The problem:  There is no way, short of turning off the computer, to stop this message.  I did go into sudo gparted to start a second instance. But the first instance had the partition mounted, so I'm stuck.  

So, do I change the device boot loader to the /dev/sdb?  

And how do I kill the Gparted process?  

I'm a casual user, so I will need some fairly specific directions.  Thank you so much.

---

### Post by grahammechanical on 2014-07-02
> [COLOR=#000000]I want to have it work in the future: When the computer boots, Windows 8 gives me a choice of 2 boots, one to windows, one to ubuntu. [/COLOR]

Surely that is the wrong way around. I was not aware that the Windows boot loader recognised Linux operating systems. When I installed Windows 8 pre-view it did not detect any of my Ubuntu Installs. But Grub certainly detected the Windows 8 boot loader.

If you install Grub to /dev/sdb and sdb has the boot priority then you can select either Ubuntu or Windows. If you then change boot priorty to sda - Windows will load. But if you install Grub to sda then you will still get a Grub boot menu.

How are you trying to install Ubuntu 14.04? Is it from a live session DVD disk or USB memory stick? Then you can cancel the installation and shut down the live session. Are you trying to format and partition and install 14.04 as a series of queued actions?

Why not do it one step at a time? Run the live session, open Gparted and then create the partitions. Then close the live session and re-load it and this time use the something else option to install Ubuuntu into the partition of your choice.

It is my view that when we make a mistake with Gparted it remembers the problem and it takes a shutdown and a re-load of the live session to break out of the loop.

Regards.

---

### Post by aninkling on 2014-07-02
yes, i just finished.  It is really true... Windows 8 can dual boot and shows the options at the beginning.  
I got Ubuntu 14.04 installed but ... the windows boot disappeared entirely.  I can't access Windows 8|  I suspect the Ubuntu boot entirely took its place.  Gparted would not let me change the location of the boot drive- it insisted on the drive that Windows was on.    

I tried the grub repair tool and it failed.  Im stuck with no access to Windows.  Windows is still there- nothing touched.  Just no option to boot into it.  i can't get to the boot utility new to Windows 8 either.  You have to boot into windows to get to the windows 8 utility.  Hows that for logic.  

I saved the Ubuntu/Linux boot utility output to [http://paste.ubuntu.com/7738847](http://paste.ubuntu.com/7738847).  Can you or someone else help me restore the dual boot?

---

### Post by yancek on 2014-07-02
You have the Ubuntu Grub bootloader installed in the master boot record of sda which is your windows disk.  If you look at the grub.cfg file, there is no entry for windows.
I also noticed "/bootmgr /Windows/System32/winload.exe /wubildr ", indicating that you have or had a wubi install or tried it.  I've never used it but my understanding is that it will not work at all with windows 8.  You have the same wubildr on sdb1.

Your Ubuntu on sdb2 seems to indicate an mbr boot.  I believe windows 8 needs uefi.  There are several other factors involved with windows 8 such as Secure Boot and FastBoot.  I am not familiar with this so best to wait for someone with more knowledge on the subject. 

The only way a windows bootloader will have an entry for a Linux system is when using wubi type installation, as a program inside windows.

---

### Post by hakuna_matata on 2014-07-03
IMHO **/dev/sdb2** is _not_ Wubi. If you also have parts of Wubi these links should help you:

[http://askubuntu.com/questions/45341...not-be-mounted]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-temp-could-not-be-mounted")
[URL="http://ubuntuforums.org/showthread.php?t=2217829"]http://ubuntuforums.org/showthread.php?t=2217829

[/URL]In your case Windows 8 should be no problem because you don't use UEFI.

---

### Post by yancek on 2014-07-03
With regard to wubi and windows 8:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

sdb2 is a Linux partition and where your Ubuntu is probably installed.  If you used wubi in the past, it would be installed on a windows/ntfs partition and not on its own partition.   You can install the Ubuntu Grub bootloader to the mbr of sdb with:  sudo grub-install /dev/sdb
That would need to be done from the Ubuntu on sdb2.  You would need to repair your windows bootloader on sda or you could run sudo update-grub after installing Grub to the sdb mbr and it should detect windows.  You would then have to set sdb to first boot from the BIOS to boot to windows.   That might lead to other complications so you might be better off booting sda with windows, sdb with Ubuntu Grub by selecting the drive on boot.  It also might be a problem with mixing legacy/uefi and gpt booting.

---

### Post by LostFarmer on 2014-07-03
as per your paste from Linux boot utility line 515.  Win 8 was installed in EFI mode but linux was installed in MBR mode.  Will have to let others instruct you on repair.

---

### Post by aninkling on 2014-08-18
The solution was rather easy.  Using the Grub editor, I found the Windows entry in the grub under "Advanced".  I dragged that entry to the top of the entire grub list.  Saved.  Powered off, restarted.  Get the Windows as the first option.  However, I'm going to start another thread on now this works and a problem that I noticed only recently:  when booting into ubuntu 14.04 and then later cold start rebooting into windows 8.1, the system time is changed to +4 hours, which makes the system time equal to GMT.  I have to manually reset.

---

