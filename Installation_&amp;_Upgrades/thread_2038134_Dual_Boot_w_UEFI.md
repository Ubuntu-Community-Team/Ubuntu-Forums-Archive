---
title: "Dual Boot w/ UEFI"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by javajeff1 on 2012-08-06
I am considering a new mobo/ram/ AMD cpu, and I would like to dual boot Windows 7 and Ubuntu with two hard drives.  I find it very easy on my current mbr based system.  I plan to do fresh installs but would love to hear from others how easy this will be.  Thanks.

---

### Post by mastablasta on 2012-08-06
if you buy windows 8 certified hardware you can disable uefi and use BIOS instead.
 
otherwise see this: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by drmrgd on 2012-08-06
It's a little trickier to do, but not too bad once you figure it all out.  I just set up a new dual boot UEFI system with two hard drives myself, and it's working great.  If you partition your drives correctly and be sure that you install each OS in UEFI mode, then it should be easy from there.  In order to help (since you really have an advantage having two drives IMHO!), I recommend having only the drive you're installing each to connected at a time in order to be sure you get each installed in UEFI mode and they boot without an issue.  Once you get there, it's a simple matter of making Grub2 be the default loader and making an entry to your Windows 7 bootmgfw.efi file.  

Here's my post with the method I used to get it working:

[http://ubuntuforums.org/showpost.php?p=12134650&postcount=14](http://ubuntuforums.org/showpost.php?p=12134650&postcount=14)

---

### Post by javajeff1 on 2012-08-06
> **drmrgd said:**
> 

Here's my post with the method I used to get it working:

[http://ubuntuforums.org/showpost.php?p=12134650&postcount=14](http://ubuntuforums.org/showpost.php?p=12134650&postcount=14)

Thank you so much for the post.  I MAY try that.  It looks like you are still chain loading from grub2, and still in jeopardy of a kernel update that can break your system.  Furthermore, future distro are planning to ditch grub 2.

Does anyone know if the Asus AM3 boards have a legacy/mbr mode?  I have only played around with the Insyde H2O boards.  Thanks!

---

### Post by drmrgd on 2012-08-06
I set up this system just before the news was announced that Grub2 might be phased out.  Since I couldn't figure out how to edit the Windows .efi files to add Kubuntu to the list (actually the biggest problem for me was I couldn't figure out how to get any of the UEFI editing tools to work), I decided that I would just stick with Grub 2 instead.  So, far I've gone through one Kernel upgrade, and nothing's broken yet (I've held the latest one and haven't upgraded that as I am in the middle of a project and don't have time for any system problems at the moment).  I'm really not expecting too many problems, though.  Do you have any information to the contrary?  I definitely wouldn't mind learning about some potential pitfalls!

I'm thinking that it'll be very easy to swap things over to an EFI bootloader once Ubuntu finished development on something and gets it rolled out.  For now, though I'm thinking Grub will be fine.  I'm definitely not planning to upgrade to Windows 8, and so Secure Boot UEFI won't be an issue I'll have to deal with.

I had a quick look at the AM3 boards, and it looks very similar to my X79 board.  In fact, I think it may (basically) be the AMD version of the board I have.  If that's the case, I couldn't find a way to disable the UEFI mode per se.  But, I think you can just boot the installation disc as MBR instead of UEFI (you'll see a both options when you're in the BIOS menu) and install from there.  That *should* go around UEFI in general, which I skipped since I had already installed Windows 7 as UEFI, and I wanted to see how UEFI worked since that seems to be the way things are going.

---

### Post by oldfred on 2012-08-06
Windows Secure Boot only applies if you buy hardware with Windows 8 pre-installed as that is the Windows requirement for vendors to sell with Windows 8. 
Both Windows 8 & Linux will install to any older computer without Microsoft Secure Boot as older computers do not have the switch in UEFI turned on. Not sure if on new computer turning off secure boot may cause issues with Windows or not. The issue is more that trying to tell the average user that turning off something that says secure boot is a good thing, especially with the MS marketing department promoting Microsoft Secure Boot as the solution to all the security issues Windows has had. Hopefully Microsoft is also improving other security issues it has with it fundamental design.

---

### Post by javajeff1 on 2012-08-06
I have been holding off upgrading due to bios concerns.  I only have 4GB of ram, and DDR2 ram is more expensive than buying a new board, CPU, and RAM.

---

### Post by drmrgd on 2012-08-06
> **oldfred said:**
> Windows Secure Boot only applies if you buy hardware with Windows 8 pre-installed as that is the Windows requirement for vendors to sell with Windows 8. 
Both Windows 8 & Linux will install to any older computer without Microsoft Secure Boot as older computers do not have the switch in UEFI turned on. Not sure if on new computer turning off secure boot may cause issues with Windows or not. The issue is more that trying to tell the average user that turning off something that says secure boot is a good thing, especially with the MS marketing department promoting Microsoft Secure Boot as the solution to all the security issues Windows has had. Hopefully Microsoft is also improving other security issues it has with it fundamental design.

Thanks for the clarification Fred!  I wasn't aware of the distinction, and now knowing that, if Windows 8 is better and I do have a few extra bucks lying around, I won't be so worried about upgrading, as I only build my own computers these days.

---

### Post by nehaljwani on 2012-10-08
You don't necessarily need to dual boot Windows and Linux on UEFI. Follow the guide [http://www.youtube.com/watch?v=PEou2dIcMSE](http://www.youtube.com/watch?v=PEou2dIcMSE) to convert your UEFI to MBR-BIOS without loss of data. Or read about it here: [http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html](http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html)

---

