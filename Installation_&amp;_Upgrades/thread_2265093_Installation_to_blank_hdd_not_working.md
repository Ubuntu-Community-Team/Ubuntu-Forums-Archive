---
title: "Installation to blank hdd not working"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by mars2 on 2015-02-12
I am in the IT field (fairly newly) working for a group that helps people with general questions, problems, etc.  I had an individual approach me regarding an installation of Ubuntu.  My organisation views Ubuntu as "third party" and so I'm handling this freelance. 
The client had already erased windows off his internal hard drive. He was using Trust Tahr off a USB drive and when we selected "install Ubuntu" it took us through the install process. Everything seemed to be running smoothly. When we got to the end we went through the restart of the computer and it had not installed to the hard drive. Upon powering on the computer gave the generic "insert boot media and press a key" message. We weren't given an option to choose an install location during the installation. Should we have seen such an option? Is this potentially an improperly burned ISO? Basically, does anyone have a thought on why this occurred? We could run Ubuntu from the USB without issue so I doubt that the ISO was corrupted.

---

### Post by oldfred on 2015-02-12
What brand/model computer?
 Many vendors are modifying UEFI to only allow by description and only entry that says "Windows". That is not per UEFI standard. 
But we have a variety of work arounds.

If not using Windows we can change the grub or shim entry to read Windows in UEFI but actally load grub. Or we can change the hard drive boot entry to be grub or shim and system can be booted with hard drive entry.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Same instructions
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Often best to review details of install to make sure installed correctly.
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


     Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by yancek on 2015-02-12
You don't indicate how new/old the computer hardware is.  You might take a look at the links below and compare them to what you saw.  The first link is the simplest installation while the second is much more informative and detailed.

 [http://howtoubuntu.org/how-to-install-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/how-to-install-ubuntu-14-04-trusty-tahr)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

