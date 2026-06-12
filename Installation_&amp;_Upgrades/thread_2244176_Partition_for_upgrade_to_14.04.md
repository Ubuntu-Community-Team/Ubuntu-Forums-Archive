---
title: "Partition for upgrade to 14.04"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by Photobug on 2014-09-14
I have been running Ubuntu successfully with XBMC on my HTPC with 12.04 for about a year.&nbsp; Initially I had envisioned doing a dual boot with windows and possibly other partitions for other Linux OSs.&nbsp; In order to do this I made an overly complicated partition scheme on my SSD to accommodate these needs.&nbsp; Now I realize that Ubuntu is all I need.&nbsp; I am having issues with my setup now with 12.04 or the XBMC portion of it.&nbsp; I figured it is a good time to try to migrate towards the new LTS in 14.04.&nbsp; Initially I was having troubles to the partitioning and placement of the 14.04 but in the process of posting a question here I figured out how to go about it.<br><br>My computer is configured with an SSD for the OS and two HDDs for storage.&nbsp; On startup it gives me a number of options to boot and will boot to an early version of 12.04 if I do not choose an option.&nbsp; I like the configuration of the OS I have on sdc2 so use that instead.&nbsp; I was hoping to be able to choose the the new 14.04 build I installed on sdc5 (with a Unetbootin) using this same method on startup, however sdc5 does not come up as a boot option.<br><br>Attached is a GParted snapshot of my sdc SSD.&nbsp; I am guessing either I did not install it correctly or need to change a configuration to get the 14.04 build running. How do I proceed?[ATTACH=CONFIG]256444[/ATTACH]

---

### Post by grahammechanical on 2014-09-14
I do not understand your situation. Giving us your history has confused me. Please explain what OS you have on what disks and which disk is sda, which is sdb and which is sdc. 

Another thing. The Ubuntu installer will by default install the Grub boot loader into sda. If sda does not have boot priority then you will not see the Grub boot menu that was configured at the time that Ubuntu 14.04 was installed. You are most likely seeing the boot menu for 12.04 and that is unaware of the existence of 14.04.

Load 12.04 and run

```
sudo update-grub
```

Now can you load into 14.10? Or change the boot priority to sda. Or make sure that 14.04 is on sdc and load into 14.04 and run

```
sudo update-grub
sudo grub-install /dev/sdc
```

and make sure that sdc has the boot priority. Then 14.04 will be at the top of the menu and load after 10 seconds.


Regards.

---

### Post by Photobug on 2014-09-14
> **grahammechanical said:**
> I do not understand your situation. Giving us your history has confused me. Please explain what OS you have on what disks and which disk is sda, which is sdb and which is sdc. 

Regards.

Sorry for the confusion.  I believe I started the computer using sda as my HDD and it can possibly have an OS or Grub on it.  I really had no clue what I was doing then but just experimenting with an Ubuntu configurations, trying to get it running on this computer.  [ATTACH=CONFIG]256445[/ATTACH]
The sdc is my SSD and is intended for my OS use only.  sda and sdb are HDDs intended to be used only for storage.  The main problem I am having with my 12.04 build which is on partition sdc2 is I have forgotten the password so am unable to use sudo commands.  I think I remember the words I used for my password but not which combination of capitalised letters I used.  I was hoping to be able to create a new 14.04 partition and do it right this time, by writing down my password this time and configuring it how i want.

I have tried before to run through the various options of my password when I realized I had forgotten it and will try again later today to rediscover the missing password. Is there a way I can create a partition with an install on sda with 14.04 on it to bypass this sudo command on sdc?

---

### Post by oldfred on 2014-09-14
You can install Ubuntu on every hard drive. Actually I suggest with the new very large drives to have a smaller / partition only for emergency boot on large data drives.
I like to keep password relatively simple for my home desktop system. 

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

With multiple drives you can have different boot loaders in the MBR of each drive. And they can boot different drives. And grub should let you boot any install on any drive. Or with multiple installs and multiple drives it can get complicated on what is where. I then suggest Boot-Repair's report or bootinfoscript (which is part of the report) just to know what is where.

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Photobug on 2014-09-14
> **oldfred said:**
> You can install Ubuntu on every hard drive. Actually I suggest with the new very large drives to have a smaller / partition only for emergency boot on large data drives.
I like to keep password relatively simple for my home desktop system. 

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

With multiple drives you can have different boot loaders in the MBR of each drive. And they can boot different drives. And grub should let you boot any install on any drive. Or with multiple installs and multiple drives it can get complicated on what is where. I then suggest Boot-Repair's report or bootinfoscript (which is part of the report) just to know what is where.

      [/]("http://bootinfoscript.sourceforge.net/")

The password I am missing is the one for the computer itself.  I have user password.  I tried to follow the instructions for lost password when I tried to "mount -o remount, rw /"  I got a "line 10 error"  So I tried without remounting and was able to change the password on my user.  When I try to change the password for the computer using :passwd "computername" I get an error "authentication token manipulation error".

After exiting the root mode or recovery I tried the grub repair in the recovery mode.  When I enter "YES" in the grub repair nothing happens.  When I enter ctrl alt delete it runs through a series of code then shows two OSs 12.04 at sda1 and 14.04 at sdc5.

Is there a way to reset the password on the whole computer not just individual user?  Is there a way to repair the grub in the recovery mode?

---

### Post by oldfred on 2014-09-14
If a desktop your computer manual may have detailed instructions on which two pins to manually jumper on Motherboard to reset a BIOS password. Some laptops have a pinhole for a paper clip to reset. See your user manual.

You should be able to use Boot-Repair, or you can manually reinstall grub by mounting which every partition has your full Ubuntu install and reinstalling grub. Or you can do a full chroot and totally reinstall grub if totally corrupted. 
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Photobug on 2014-09-14
> **oldfred said:**
> If a desktop your computer manual may have detailed instructions on which two pins to manually jumper on Motherboard to reset a BIOS password. Some laptops have a pinhole for a paper clip to reset. See your user manual.

You should be able to use Boot-Repair, or you can manually reinstall grub by mounting which every partition has your full Ubuntu install and reinstalling grub. Or you can do a full chroot and totally reinstall grub if totally corrupted. 
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

It is not the computer itselfs code I am missing but the root level code for the computer.  I have some hard drives that do not automatically mount when I open my sdc2 version of 12.02.  When I click on it it asks for a password.  I put in my personal password and the drives become mounted.  However when I try to use a sudo command and plug this password in it does not work.  I am assuming there was a different password for my "cathousetheater" which is the name I gave the computer on the OS.  I had assumed there was another code I am missing for root level access.

Any way it is kind of a moot point as I have solved the original issue I came here for.  When I ran some of the other diagnostics I found an OS on sda1.  It was my orignal working OS and I don't use it but figured it might solve this issue.  I booted into its recovery mode reset the password, booted into it and did a "sudo update-grub".  I am now happily posting this from my new Trusty Tahr.

I am going to mark this as solved. Althought it has opened up a new slew of quetions.

Like how to get root access on the sdc2 OS?
Should I move the SSD to the position of sda so the OSs will boot directly from the SSD and not rely on the current sda which is an HDD?

Thanks oldfred and grahammechanical for your help;

---

### Post by oldfred on 2014-09-14
With Linux the drive order is not critical, Windows often seems to work better if it just is the first drive.
But you do have to control in BIOS which drive you boot from.

I do prefer to have grub in the MBR of the same drive as your Ubuntu install and in BIOS boot from that.

Are the drives that do not mount then encrypted as those do require you to have password to mount them. And if you lose that password your only way to get data is from your backups.

---

### Post by Photobug on 2014-09-17
> **oldfred said:**
> With Linux the drive order is not critical, Windows often seems to work better if it just is the first drive.
But you do have to control in BIOS which drive you boot from.

I do prefer to have grub in the MBR of the same drive as your Ubuntu install and in BIOS boot from that.


I am able to change the boot order in the BIOS, but since the Grub is installed on the sda HDD, and my preferred boot location is the sdc5 partition, will making the sdc drive the primary screw things up for the grub?

Can I put a grub on sdc and or make the sdc5 the first partition that gets booted?  Right now the computer will boot to the sda1 partition which is not my best working one.  Although of the Ubuntu builds work well it is the XBMC configurations that I prefer on some builds over others.

---

### Post by oldfred on 2014-09-17
If from the install booting from sda lets you boot into the install in sdc5, you can directly install grub to the MBR of sdc. Then reboot and set sdc as default.
This assumes all drives are MBR with standard (old) BIOS boot. If drive is gpt with BIOS boot you also need a bios_grub partition on the gpt drive for grub to install correctly to the gpt drive's protective MBR to boot in BIOS mode.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdc but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck /dev/sdc
sudo update-grub

Grub also remembers where you originally installed it. It will have a hard drive entry for that:
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc

      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Photobug on 2014-09-18
I was complaining that I broke my link to the sdc5 in the process or running these steps.  But that was only because I did not recognize the new configuration.  In 14.04 or the new grub I am not sure which is responsible the boot screen came up with an option for Ubuntu, Ubuntu advanced, sda1, sda1 advanced, sdc2, sdc2 advanced and nothing else.  I figured I had broken my link to the sd5 build, and after going back and forth between the two working (sda1 and sdc2) OS's I tried just letting it boot automatically to just the first Ubuntu and my 14.04 setup on sdc5 booted up just like i wanted.

Thanks OF.

---

### Post by oldfred on 2014-09-18
It still is showing a broken RAID.

If drive used to be RAID and is not:
             
 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

