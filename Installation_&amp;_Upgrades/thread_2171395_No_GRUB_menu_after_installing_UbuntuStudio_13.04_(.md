---
title: "No GRUB menu after installing UbuntuStudio 13.04 (dual-boot with Windows 7)"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by peGGi on 2013-08-30
Hello,

I'm trying to install UbuntuStudio 13.04 (64bit) in a dual-boot setup with Windows 7 (already installed).

 

 I degfragmented several times.  I backed up the MBR and first track of hard-disk.
 

 I then shrunk my C: drive.  Booted back into Windows afterwards, several times, and also ran chkdsk.  Everything ok.   
 

 I then used GParted Live to format the partitions for the Linux install.  After I finished, this is what my partition scheme looked like:
 
[LIST]
[*]/dev/sda1        Primary           Windows     MBR                             NTFS              200Mb 
[*]/dev/sda2         Primary           C:     (Windows)                             NTFS              160Gb 
[*]/dev/sda3        Primary           partition for     /home                      ext4                382Gb 
[*]/dev/sda4 Extended
[LIST]
[*]/dev/sda5                    partition for     /                          ext4               45Gb 
[*]/dev/sda6                   partition for     swap                  swap           8.97Gb 
[/LIST]
   
[/LIST]
 [ATTACH=CONFIG]245846[/ATTACH]


 Again, after doing this I backed up the MBR and first track of hard-disk.  I also ran chkdsk again for Windows.  

 

 Since then, I have booted into UbuntuStudio Live session many times and installed the system.  Each time I do this, it all seems to go ok.  Installer runs without problems.  It tells me the installation is complete and to reboot the computer to finalize.   
 

 However, when I reboot, it goes straight into Windows.  Every time.  No sign of GRUB.   
 

 I have run the live session from my USB key (which I had wiped clean and formatted before putting the Ubuntu files on it), using both UnetBootIn and LiLo.   

 

 I tried to run the live session from a DVD-R and a DVD-RW, having used ImgBurn and InfraRecorder to burn the images.  However, when I try and boot in, using these discs, I get a blank screen with some gobbledy-gook white pixels in a row at the top of the screen, and that's as far as it will go.
 

 I have also tried installing *not* from within the live session, from running the installer without booting into the live session.  But the same thing happened.
 

 I have verified the MDA5 and sha hashes for the UbuntuStudio image.  
 

 At the point in the installation process where I choose which system folders will be installed on which partitions, it recognises UbuntuStudio 13.04 as being on the 'root' partition.  So I suspect that it's a problem installing GRUB and the correct bootloader files.   
 

 I chose to install the bootloader files to 'dev/sda WD6400BPVT-2' each time, except the very first time, when I chose 'dev/sda1 Windows 7 (loader)'.  Regardless, the same outcome happened/happens.   
 

 The machine is 2 years old.  It doesn't have secure boot or UEFI or anything like that.
 

 I can't see anything in the BIOS that would cause this problem.
 

 What is wrong?  I was so looking forward to having my first, fully-installed Linux distro up and running today.  I've been planning this particular install for weeks, and in fact on-and-off for two years!
 

 I've read about another bootloader (LiLo).   Or I could try and install vanilla Ubuntu and upgrade from there.  Or install an older version of UbuntuStudio and upgrade.  But before I throw myself into any more rabbit holes, I'd really appreciate some advice/suggestions/guidance first.   
 

 Oh, my machine's specs:
 
[LIST]
[*]Lenovo IdeaPad Z570 
[*]Windows 7 64bit 
[*]Intel Core i5 (second gen, 2.3Mhz) 
[*]640Gb Harddisk 
[*]6Gb RAM 
[*]Nvidia GeForce 520m Optimus     (although I've disabled Optimus in BIOS, running the Intel chip     only) 
[/LIST]

---

### Post by oldfred on 2013-08-30
Best to see details. If you installed grub to PBR - partition boot sector of a NTFS partition that usually prevents Windows from booting as it has to have its boot code in the PBR.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by peGGi on 2013-08-30
Hi Oldfred,

You actually helped me with partition stuff, a few years ago!  Hi again!  

Thanks for the quick response.

The boot-info report is here:  [http://paste.ubuntu.com/6045051/](http://paste.ubuntu.com/6045051/)

My external hard-drive was plugged in so please ignore that.  It's not part of the system, as such. 

I won't be online for the rest of the evening so please don't be miffed if I don't get back today.  Will definintely do so tomorrow (it's going to be all I'll think about all evening).  I'll be able to look more closely at the Boot-Repair program tomorrrow too.

Thanks again :)

---

### Post by oldfred on 2013-08-30
You have a BIOS/MBR install, so be sure to boot Boot-Repair in BIOS mode. It says your system is UEFI capable and you booted it in UEFI mode.

You do need to install grub2's boot loader to the MBR. Not sure why it did not work before. 
Some issues can be BIOS has locked MBR, so check BIOS for settings.

Also some hard drives that were gpt, or were RAID may have left over meta-data that grub sees and then does not know which way to install.

I do not see anything that looks like a problem. I would just let Boot-Repair run its reinstall of grub. It is suggesting a full uninstall and reinstall so make sure Internet is working as after uninstall you may not be able to boot until reinstall is complete. If it still does not work then post new BootInfo report and it may have an error message that will help.

---

### Post by peGGi on 2013-08-31
I ran boot-repair.  And it worked!  GRUB 2 menu showing up and I can boot into Ubuntu Studio and Windows.  I am thrilled.  Thank you for your help.  

After the updates installed in Ubuntu, my wireless stopped working, and hasn't come back on after several reboots.  That's for another round of searching and possibly another thread I suppose!  

Anyway I finally I have a dual-boot Ubuntu/Windows setup so thanks.

---

### Post by oldfred on 2013-08-31
Glad it is booting.

Usually updates fix things. But if you cannot quickly resolve it best to start a new thread with model of chip and issue in title and details in post.

My wireless just works on my laptop, so I do not know much. But those that do like this info:

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

Noticed it has HWaddr which is unique to you but can be spoofed so someone can pretend to be you. Just change address to xX.

---

### Post by peGGi on 2013-09-01
Wireless is working.  I disabled the Broadcomm driver (which seems to have been enabled during the update) and wireless came back.  Thanks for the suggestions though.

---

