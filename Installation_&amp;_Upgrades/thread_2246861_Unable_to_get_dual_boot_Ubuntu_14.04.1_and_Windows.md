---
title: "Unable to get dual boot Ubuntu 14.04.1 and Windows 7 working"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by Adam_Yost on 2014-10-03
So I have scoured forums doing everything suggested(correctly as far as I know...maybe making errors) and I cannot get these two OS's to dual boot. I am running a desktop that previously had Windows 7 on it, and I am attempting to install Ubuntu alongside it on my external hard drive. 

I went through the installation and got to the "error:no such partition. Entering rescue mode... grub rescue>" screen. I read to use boot-repair on the system for it to re-install grub. 
I've tried boot-repair multiple times with it not changing anything for me. It does always say to make sure and "Please do not forget to make your BIOS boot on the removable disk!", and I'm not entirely sure what that means.


Here are my boot options:

[IMG]https://drive.google.com/file/d/0B4o_nxesphymTXg5N2Q3ME80V1U/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/0B4o_nxesphymTXg5N2Q3ME80V1U/view?usp=sharing](https://drive.google.com/file/d/0B4o_nxesphymTXg5N2Q3ME80V1U/view?usp=sharing)

And my boot order

[IMG]https://drive.google.com/file/d/0B4o_nxesphymRTJCM2dXZ1lQM00/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/0B4o_nxesphymRTJCM2dXZ1lQM00/view?usp=sharing](https://drive.google.com/file/d/0B4o_nxesphymRTJCM2dXZ1lQM00/view?usp=sharing)


When I installed, the only option to put my install on was my external hard drive. I'm really not sure where to go from here. I would always use the default boot-repair settings when using it as well. 

Here is my Boot Summary info from boot-repair: [http://paste.ubuntu.com/8489502/](http://paste.ubuntu.com/8489502/)

Any and all help will be appreciated! I hope I've included enough information.

---

### Post by Bucky Ball on 2014-10-03
In your BIOS, do you have the boot order set to boot from sdc, the external drive (I presume)?

---

### Post by Adam_Yost on 2014-10-03
Working in the BIOS is where I get a little out of my element. The WD MyBook is the external, and it is set as the primary hard drive to boot from. In the boot order, HD is listed first. I'm assuming this means it should be the first thing to boot...I also have booted straight from the external hard drive using the boot menu, and it gives me the same error.

---

### Post by oldfred on 2014-10-04
You are showing two installs of Ubuntu 13.10 in sdc6 and 14.04 in sdc7. And it looks like grub is installed to boot sdc6, you can use Boot-Repair's advanced mode to tell it to install grub for sdc7 into MBR of sdc.

Reinstall the GRUB of sdc6 into the MBR of sdc

Your 13.10 had expired so no updates are available.
If the reinstall of grub2's boot loader for 14.04 does not work you may need to run the advanced uninstall and reinstall of grub2 for 14.04.

---

### Post by Adam_Yost on 2014-10-04
I am still getting the same error. [http://paste.ubuntu.com/8493567/](http://paste.ubuntu.com/8493567/)

I do not want the 13.10 install, I would like that deleted. 

I did try to do the advanced install of the grub2, and it finished but said there was an error so I ran boot-repair again. Really stuck on what to do. Wouldn't mind starting from scratch, but I'm not sure how to do that.

---

### Post by oldfred on 2014-10-04
Boot-Repair picks up some minor error somewhere and reports that in its summmary.

Error code 0 is no errors, so grub did reinstall for sdc7. Are you booting from BIOS with sdc?

 Reinstall the GRUB of sdc7 into the MBR of sdc
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdc: exit code of grub-install /dev/sdc:0

---

### Post by Adam_Yost on 2014-10-06
I have my Hard Drive Group set to be the first boot device, and within the hard drive group I have my external hard drive set to boot first. Is there something I am missing there?

---

### Post by Adam_Yost on 2014-10-06
Now windows won't even load...I deleted the 13.10 and 14.04 operating systems using the OS-Uninstaller in Linux using the live cd, and then re-installed 14.04 and that still didn't work and I would get the same exact error as before.

Now without making more changes, I cannot get Windows 7 to load, which would work before if I choose it on the boot menu.

[http://paste.ubuntu.com/8511744/](http://paste.ubuntu.com/8511744/)

---

### Post by oldfred on 2014-10-06
Installs both Windows & Ubuntu look normal.

Grub really only boots working Windows, but you have a boot partition sda1 & main install sda2. Boot-Repair usually copies the bootmgr & BCD from boot partition to main install as a backup. Many users do not know boot partition is essential and delete it. Your boot flag is on the main partition not the boot partition but looks like it still should boot.  Grub only really boots working Windows. I might move boot flag back to sda1 and see if f8 gets you to a repair console when you directly boot sda the internal drive. You should be able to use the one time boot key if your system has one. It is often f12, f10 or f8 depending on vendor. See manual.

Is BIOS set for AHCI not IDE? 
There are some newer BIOS with an old BIOS type issue. May be BIOS setting and has shown on external drives booting thru USB. Those BIOS only boot from partitions fully inside the first 137GB of the drive. But you have a very large NTFS at beginning of sdc drive so that will be difficult to test. Check BIOS settings first.

---

### Post by Adam_Yost on 2014-10-07
I reset the boot portion of the BIOS and windows still will not boot past the initial windows loading screen, and my ubuntu will not work either. 

The place that I saw ACHI and IDE was actually set to RAID. I tried switching that to IDE and I got all the same results. Really confused as to why Windows won't even work anymore. I've tried running the windows boot-repair that shows up when it doesn't load properly, and it says that it cannot automatically fix the problem.

---

### Post by oldfred on 2014-10-07
If RAID, you may get RAID meta data on the drive which then causes issues.
IDE is for compatibility with the very old systems. Best to use AHCI, but if you did not install that driver in Windows 7 you may need to install it. Newer installs of Windows 7 include it automatically, but it is just another driver.

Often have to run Windows repairs 3 times to fix everything, what was error message in Windows.

But this forum knows Windows 7 better.
[http://www.sevenforums.com/](http://www.sevenforums.com/)
       f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

            [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by Adam_Yost on 2014-10-07
It seems as though my hard drive is "failing". I am getting the BIOHD-8 error code. I am doubting that it is mechanical, but I am struggling to figure out how to fix this issue now. I didn't want to lose my windows install, but I'm starting to think I'll have to just install ubuntu and wipe away windows all-together.

---

