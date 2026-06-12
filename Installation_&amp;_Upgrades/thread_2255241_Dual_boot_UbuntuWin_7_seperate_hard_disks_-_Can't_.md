---
title: "Dual boot Ubuntu/Win 7 seperate hard disks - Can't boot in Windows 7"
date: 2014-12-03
forum: Installation &amp; Upgrades
---

### Post by hellstorm68 on 2014-12-03
I have had Ubuntu 14.04 running on a 320GB hd along side my 2TB hd Windows 7 hard disk for some time now.  Recently my ubuntu had some errors that it could not recover from, so I re-installed using a CD I burned with the Ubuntu 14.04 ISO.  I used to boot into the Grub, which would ask if I want to boot in Ubuntu or Windows 7.  Now, there is no option to boot into windows, I just boot automatically into Ubuntu.  I tried hitting the Esc key to bring the grub up during boot, but there is no option for Windows 7.  I think back to the installation, and I believe I have chosen the option to "Install along side Windows" in the past, but chose this time the "Replace my Ubuntu Installation" option, which may have removed some files windows needs to boot.  I tried using my Windows 7 pro install CD to repair my windows installation, but the installer tells me that there are no problems booting, and that the last boot of Windows (11-21-14) went just fine, so there are no errors to fix.

I tried disabling my Ubuntu hard disk in my BIOS so I'm forced to boot off my Windows HD only, but Grub comes up anyway and errors out, putting me into some sort of restore mode or something similar.

I'm not an avid Ubuntu user, I love the OS and would like to get more knowladge, but I still need Windows for my gaming (I'm a geek, I know :) ).  I know I could do a fresh install of Windows and Ubuntu and be fine, but I do want to keep my configuration, and not spend the next few weeks getting my computer back to where it was.  Can anyone help me out?  I'm at work right now, but will be home later and ready to try some new options based on suggestions from the Ubuntu community. 

Any help would be greatly appreciated!  I'll be checking back on the forums from time to time until i go home, but won't be able to try anything until about 10 hours from now.

Thanks again!

---

### Post by oldfred on 2014-12-03
With mulitple drives or mulitple installs, we now have no idea what an auto install may do. Generally safer to use Something Else or manual install, as then you have total control over partitions, locations, sizes, formats. But then you do have to specify all that.

We need to see where everything is at. DO NOT run auto fix. That installs grub to every MBR, and you do want Windows boot loader on Windows drive, and grub on Ubuntu drive. That is in advanced options only.
Post link to summary report, so we can suggest best alternatives.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hellstorm68 on 2014-12-03
I did read some forum entries after researching my problem a few days ago on Google, and saw some terminal commands for updating Grub, so I tried those.  However, I didn't have any success.  Grub still sees only the Ubuntu booting possibility, not the Windows.  I'm thinking Grub has been installed on my Windows HD because when I disabled the SATA port in my BIOS to only boot from the 2tb drive, Grub still came up with an error.  I've browsed my windows HD, and can see all my files there.  I've tried to use terminal commands to browse around my 2TB Windows drive while in the Grub recovery mode (Again, I don't remember if that's what it was called, but it's the mode that came up when I disabled the Ubuntu SATA port in my BIOS and booted from the Windows HD).  When I tried to browse the drive, I received an error saying it could not recognize the file system.

I also saw references to terminal commands to install boot-repair, however the package could not be found when the command was entered.

As far as "Post link to summary report, so we can suggest best alternatives", I'm not sure what you mean by that.  As I've said, I'm fairly new to Ubuntu and have used it for little more than learning basic Python programming, playing games, watching movies, and trying to learn Linux in general.  I obviously know just enough about the OS to get me into trouble :D.

Thanks for the reply, I really hope I can get my desktop up and running again.

---

### Post by oldfred on 2014-12-03
Boot-Repair did not have current versions in its ppa until a week or two ago. Now it has current versions.
Instructions in web page were updated to remove the name change back to an old Saucy version when using trusty. Now you do not run the name change.
 Precise, Trusty, Vivid, & Utopic all should work now

If you look at Boot-Repair site one of the main buttons is the summary report. Click on that button and it will upload the summary report to pastebin and give you a link. Post link so we can review the report. It is rather large.

---

### Post by hellstorm68 on 2014-12-03
Great, this is the most headway I've made on my problem in a week of researching, thank you!  I will be sure to try that out when I get home tonight and reply to let you know if it worked or not.  Thanks a lot, I'll give it a shot.

---

### Post by hellstorm68 on 2014-12-03
Ok, so I entered the commands for boot-repair installation, and sucessfully installed Boot Repair.  I ran the recommended fix, and I received this error:

 
 GPT detected.  Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bois, grub flag).
This can be performed via tools such as Gparted.  Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

I opted to get the summary URL.  Here's the URL:

[http://paste.ubuntu.com/9358239/](http://paste.ubuntu.com/9358239/)

I was hoping to have the auto-repair fix it, but it seems I messed things up even more than I orignally thought :(

Any thoughts?

---

### Post by yancek on 2014-12-03
You have Ubuntu installed in EFI mode with its efi files on sdb1 but you also have Grub installed to the master boot record of sda, your windows hard drive.  That's not a good combination.  I don't use EFI myself so don't have any suggestions but, hopefully oldfred will post back as I have seen a number of posts where he made suggestions successfully resolving similar issues.

---

### Post by oldfred on 2014-12-03
I think autofix was trying to convert your UEFI install on sdb to BIOS install.
Your Windows is booting in BIOS mode from a MBR partitioned drive in sda.
Your Ubuntu is booting in UEFI mode from a gpt partitionded drive in sdb.

You can boot that way if you really want. You may be able to use one time boot key like f12 or f10 but that key varies a lot by vendor. Some require you to go into UEFI/BIOS and turn on/BIOS UEFI mode or BIOS/CSM mode to boot a system installed in that mode.

Usually better to have both systems installed in the same boot mode. When not in same mode you cannot use grub menu to dual boot, only from UEFI. The two boot modes are not compatible.

Boot-Repair can convert a UEFI install to BIOS boot if you add a tiny 1 or 2MB partition with the bios_grub flag. You can use gparted from live installed to add that partition anywhere on drive. Shrink sdb2 and create the new bios_grub partition. Then rerun boot-Repair.

Use advanced mode in Boot-Repair to also install just the Windows boot loader to the drive that is sda. Then if grub does not work you should be able to choose to boot Windows.

Make sure UEFI/BIOS is set to BIOS/CSM/Legacy but not UEFI.

How you install whether UEFI or BIOS is determined by how you boot installer for both Windows & Linux. And new hardware that has both modes, will offer to boot flash drive in either mode.

---

### Post by hellstorm68 on 2014-12-05
Ok, so sorry for the delay with my post. Haven't been able to work on this until now. Here's where I'm at:

-Booted from Ubuntu 14.04 install Cd into "try ubuntu"  option 

-ran gparted by typing "sudo gparted" into terminal

-shrunk sba2 by 2 MB

-created 2MB grub_bios partition

-rebooted into Ubuntu from 320gb hd

-ran boot-repair

-got the same error as before

-went into boot-repair advanced options and checked the box that said "repair Windows mbr" or something similar

-grub still didn't recognize Windows 

-rebooted into motherboard bios menu

-went into booting menu

-saw a bunch of options for "boot override" listing my dvd rom drive and hard disks

-clicked on the dvd rom drive 

-Windows immediately booted

Not sure why, but when I start the computer seems like I have to do this every time I want to boot into Windows.  Otherwise I boot into Ubuntu by default, and the grub still has no Windows option. 

I have to be missing something. I don't really know how the partitions work and all that, I'm pretty ignorant to this. I appreciate your patience, oldfred. Am I missing a step?

---

### Post by oldfred on 2014-12-05
The bios_grub partition has to be on the gpt partitioned drive or the 320GB drive.

You can boot Windows in BIOS mode or Ubuntu in UEFI mode.
You may be able to go into UEFI and in effect reboot into BIOS mode to boot Windows.
The two boot modes UEFI & BIOS are not compatible and you have to reboot to change from one mode to the other.

Make sure bios_grub is on the Ubuntu drive, run Boot-Repair to convert Ubuntu from UEFI to BIOS. It actually uninstalls grub-efi-amd64(UEFI) and installs grub-pc(BIOS).
Then if you can boot into Ubuntu with UEFI mode off or CSM/Legacy mode in UEFI/BIOS on run this:
sudo update-grub

Keep Windows boot loader on 1TB drive so from BIOS you could boot Windows, And set BIOS to boot Ubuntu drive first. Then you should be able to dual boot from grub menu. Or if grub has issues switch BIOS to Windows drive and boot Windows or use one time boot key.

---

### Post by fantab on 2014-12-06
> ...... -ran gparted by typing "sudo gparted" into terminal

-shrunk sba2 by 2 MB

-created 2MB grub_bios partition


As oldfred points out, "the bios_grub partition has to be on the gpt partitioned drive or the 320GB drive", or on /dev/sdb or on the HDD where you have Ubuntu installed.
I would first remove the 'boot' flag from the /dev/sdb1 Fat32 partition. And shrink it by 2Mb.
Then create a 2Mb unformatted partition with 'bios_grub' flag... Now re-run Boot-Repair.

---

### Post by hellstorm68 on 2014-12-06
Ok, so I did what you said. I discovered after a few more failed attempts that I was simply labeling the 2mb partition bios_grub and not setting a flag. Glad I figured that one out. 

Looks like it's working now, I do have the grub menu and after I ran the terminal command sudo  update-grub Windows now appears as an option. Thanks for the help, my problem is solved.

---

### Post by fantab on 2014-12-06
That's great to know. Please mark the thread as 'Solved' using thread tools.

---

