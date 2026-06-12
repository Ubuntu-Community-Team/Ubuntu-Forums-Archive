---
title: "Think I messed up somewhere dual booting Windows 10 and Ubuntu"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by Ridwan_Sameer on 2015-10-20
So Here's the backrgound

  Wanted to dual boot, already had Windows 10. I put 14.04 LTS ona  thumb drive and ran the live CD, installed it, making an EFI, root, home  and swap partition as told.
  I then realised it boots straight to Ubuntu. I ran boot repair for  the first time, it installed successfully and gave me this log
  [http://paste2.org/PGYfx0DY](http://paste2.org/PGYfx0DY)

  And then when rebooting it gave me GRUB, but with no Windows option,  Only ubuntu and advanced settings. I then checked the net and was told  to completely purge grub and re install and update, I did, still no  windows. I was then told to add Windows manually by editting the  /etc/grub.d/40_custom file, which I did, However it says EFI file path  invalid.
  I tried running boot repair again and got this log

  [http://paste2.org/GwffN7gG](http://paste2.org/GwffN7gG)
  And it still didn't work

  Now There's another problem, See I have two 500GB hard drives. The  First hard drive is divided into two partitions, One is C for my  windows, and D for data. The second 500GB hard drive was divided into  150GB for data, and the rest was used to install ubuntu (Seperate with  root, home, swap etc.). However now, I can't open Either the C, the D or  the 150GB data on the other hard disk, it gives me the following error
  > "Error mounting /dev/sda4 at /media/ridwan/DATA: Command-line `mount  -t "ntfs" -o  "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"  "/dev/sda4" "/media/ridwan/DATA"' exited with non-zero exit status 14:  The disk contains an unclean file system (0, 0). Metadata kept in  Windows cache, refused to mount. Failed to mount '/dev/sda4': Operation  not permitted The NTFS partition is in an unsafe state. Please resume  and shutdown Windows fully (no hibernation or fast restarting), or mount  the volume read-only with the 'ro' mount option."



  What do I do? I was able to boot into windows in the beginning, but  now I can't because the Hard drive which contains windows does not come  up in the bios. I just want to dual boot, I have a lot of data I need :(
  Thanks for any help!
  P.S I also tried OS-prober, after running the install command I got 


> Reading package lists... Done Building dependency tree
Reading state information... Done os-prober is already the newest version. The following packages were automatically installed and are no longer required:   secureboot-db shim Use 'apt-get autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 535 not upgraded.



  I then ran os-prober via sudo os-prober, and it didn't say anything,  just went to the next command line (albeit it took around 5 seconds like  it was running something)
  Another small thing, All the partitions shown in the file explorer  I'm unable to open as it gives me the error in the OP about mounting.  However for some reasons my 500mb EFI partition is showing and i can  open it 
  And I also tried refind, but refind works but shows only two ubuntu icons.

---

### Post by ubfan1 on 2015-10-20
Your Windows 10 is a legacy install, you probably don't have a UEFI machine, so the EFI partition is not used in this case.  It's good to have it, for any future use on an UEFI machine, but is not part of your current problem, it is totally ignored.  The problem seems to be Windows was not shutdown completely.  Try the line 1095 mount suggestion in your last boot-repair report, to remove the hiberfile, mount Windows, run chkdsk a few times, and make sure the power option in Windows uses shutdown.

---

### Post by oldfred on 2015-10-22
I would use Boot-Repair or your Windows repair flash drive to restore a Windows boot loader to sda.
And keep grub installed to sdb. Set BIOS to default boot sdb drive.

But then you can directly boot Windows from sda with one time boot key often f10 or f12 or from BIOS. And then in Windows turn off fast start up or its always on hibernation. It hibernates all NTFS partitions and does not not have a way to unmount a data partition. You can set the Linux NTFS driver to read only mode, and should for the Windows system partition. But need to have hibernation off for Linux NTFS driver to read/write NTFS.

With hibernation off then grub2's os-prober should find Window and let you boot it. But if Windows updates turn the hibernation back on you have to boot from sda directly.

sudo update-grub

       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

