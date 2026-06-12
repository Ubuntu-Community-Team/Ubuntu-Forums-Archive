---
title: "Ubuntu 10.10 booting from external HDD leading to some problems"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by ymesch on 2011-02-04
Hi,

I've already searches the forum a few times, but no one seems te have encountered the same problem.

Now for the problem: I wanted to try out Ubuntu without having to format any harddrive partitions on my laptop itself, so i decided to install Ubuntu on an external HDD which seems to work out quite well. The only problem I encounter is the folowing: 
   
When I boot my computer with the HDD connected and External harddisk booting enabled in my boot settings there are no problems at all; I get a GRUB menu with the choices to boot ubuntu 10.10 and various alternatives en as last option Windows 7. Just as it should be I suppose. 
   But when I want to boot directly to Windows 7 without having the external HDD connected the system boots with the Vaio logo (wich it also does with the HDD connected) but then I get a message saying that a certain drive doesn't exist followed by the message 'GRUB rescue>' (if needed I can write down the code, but I suppose it refers to a partition or harddisk)
   This seems rather strange to me since Ubuntu was completely installed on my external HDD and therefor there shouldn't be such a problem (in my logic.. but I'm absolutely not an expert so I am quite shure this is wrong).

Is there anyone having a clue about what is causing this problem and how I possibly could solve this problem so that I have 2 completely independant operating systems; one on my internal HDD and one on my external HDD without affecting eachother?

Kind greetings,
Ymesch

---

### Post by ajgreeny on 2011-02-04
The problem is that ubuntu put the grub bootloader onto the MBR of the laptop's hard disk, and you should have asked for it to be installed on the external disk.  This is a much less well documented option in the install, unfortunately, and many people wanting to do what you wanted end up in the same situation.

If you have a win7 install disk you can restore the windows MBR to the internal disk using that; I will leave you to search out the details as I no longer have enough information on windows to help.  If you don't have a windows CD, you may have to search further.  I think neosmart may have something to help, but win7 is beyond me so will leave you to look at [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) yourself.

See also [http://ubuntuforums.org/showthread.php?t=1534521](http://ubuntuforums.org/showthread.php?t=1534521)

---

### Post by oldfred on 2011-02-04
Boot into Ubuntu and install grub2 to the external drive's MBR (probably sdb). Then install a windows boot loader to the internal drive. If you do not have a windows repair CD you should have one anyway. If you set external to boot first in BIOS then you will get grub. If external is not plugged in then BIOS will default to the internal.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Install lilo which works just like the windows boot loader in the MBR. But we do not install the full lilo boot code as you are using windows.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

The windows way:
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub

---

### Post by ymesch on 2011-02-04
Many thanks for the fast replies and the help!

I solved the problem with a bit of searching and messing with the aid of ajgreeny.. I only saw your (oldfred) post when I already found a workaround.

What I did was first of all installing Ubuntu 10.10 to my external harddrive with the option that sounded lik 'completely use a partition or hardrive' or something like that. After having completed the installation i rebooted my computer keeping the external harddrive plugged in and went back into Windows through the grub menu. 

Once in Windows I downloaded Neosmart's EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)) and with that one I changed a few settings and set it this way that the the bootable stuff needed for windows was put on my C: drive. I made no other bootables and it seems to work.. The only thing I still need to change in my BIOS is the priority given to the my external harddrive so that I don't have to press escape every time I want to run in Ubuntu. 
The only difference that I remark is the fact that I have to be a little bit more patient when starting up Ubuntu, but besides that I now have 2 completely functional OS'es.

I'll mind posting some screenshots for those who might be in the same situation for the EasyBCD part if needed.

greets :)

---

