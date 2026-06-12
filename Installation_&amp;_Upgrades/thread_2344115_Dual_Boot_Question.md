---
title: "Dual Boot Question"
date: 2016-11-22
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2016-11-22
Hello friends,

I have a PC with 2 separate hard drives. One is 1 T and it has Ubuntu 16.04 installed in it. The other is 160 GB and has windows 7 installed in it. When I turn on my PC, grub sees both ubuntu and windows (on /dev/sdb2) and lets me choose which system I want to boot first.

(so it is not a classic dual boot in the sense that you have two OS on the same hard drive - I have one OS on each hard drive in separate).

When I originally installed, I did first Windows and then Ubuntu, to make sure GRUB would be ok.

The problem now is that my win 7 is "broken" and I have to re-install it. The question is how to do it without harming ubuntu and GRUB. 

If I do a simple re-install with the win 7 disk and choose the correct 160GB drive, will GRUB continue to recognize the windows? 

Any other precautions, preparations I should do or worry about?

Thanks in advance,

linux.girl

---

### Post by RobGoss on 2016-11-22
Hello and welcome, reinstalling Windows after Ubuntu has been installed may cause your machine to not boot in to your Ubuntu OS

You will have to also update the grub boot loader after reinstalling Windows 7 it will over ride the grub boot loader

I believe the grub installs to the MBR Windows partition therefore it will be overridden by the reinstallation of Windows 7

I'm sure there will others with a better explanation to how this works

---

### Post by howefield on 2016-11-22
> **linux.girl said:**
> If I do a simple re-install with the win 7 disk and choose the correct 160GB drive, will GRUB continue to recognize the windows? 

If grub is installed on the Ubuntu disk the worst you should have to do is update grub if it doesn't see the Windows installation.

Repairing your Windows install is out of the question then ?

---

### Post by RobGoss on 2016-11-22
>  
The problem now is that my win 7 is "broken" and I have to re-install it. The question is how to do it without harming ubuntu and GRUB. 

    

I would try fixing your Windows before attempting to reinstall Ubuntu it might make things a lot easier if it can be fixed

---

### Post by linux.girl on 2016-11-22
Hi,

Yes, GRUB is installed on the Ubuntu disk. Repairing windows did not work, I really have to re-install. But if you say the max that will happen is to update grub (so it sees the windows) then I guess it is not that bad.

Thank you so much!

I will do the re-install and report back on how it goes.

EDIT: I will not re-install ubuntu, it is on a different disk (two disks on the same pc, one with ubuntu and one with windows)

---

### Post by Mark Phelps on 2016-11-22
If Ubuntu is on a different disk, then all you have to do is the following:
1) Remove the Ubuntu disk from the PC
2) Reinstall Windows
3) Reconnect the Ubuntu disk to the PC
4) Set your PC to boot from the Ubuntu disk
5) Once in Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB configuration files and when you then reboot, you will see a GRUB menu with entries for Ubuntu and Windows.

Good Luck

---

### Post by yancek on 2016-11-22
> Yes, GRUB is installed on the Ubuntu disk. 

But is Grub code in the MBR of the Ubuntu disk or the windows disk (if this is an MBR install).  Which drive is set to first boot priority?  You could install Grub on Ubuntu and still have Grub code in the MBR of the windows disk if it is set to first boot priority.  If you are sure Grub is installed to the MBR of the Ubuntu disk, then the suggestion above by Mark Phelps would definitely be the safest method.

---

### Post by oldfred on 2016-11-22
If you reinstall Windows is is vital you have Windows drive as default in BIOS if BIOS install.
Windows will create a 100MB boot partition on the BIOS default drive. Since it does not see Linux partitions, it just uses the first 100MB of Boot drive potentially overwriting part of your Ubuntu install and destroying it.

Best to disconnect Ubuntu drive. Then in Ubuntu run a new sudo update-grub to find the new Windows install and add it to grub menu. 
Also best to keep Windows boot loader on Windows drive and grub boot loader on Ubuntu drive.

And if Windows only install it will be first drive, best then to keep it as first drive on SATA0 port.

---

### Post by linux.girl on 2016-11-22
Thank you all so much for the helpful tips - disconnecting the ubuntu drive seems to be definetly the safest way to go. GRUB is installed on the ubuntu drive only. The first priority is the Ubuntu drive. As of now, grub comes up after I turn on the PC and shows me the GRUB menu with the options of either continue loading ubuntu or load the windows. I guess if I disconnect Ubuntu, re-install windows and then do update grub as Michael Phelps suggested (aslways keeping the ubuntu as first priority) then it should be OK.

I will try it this week and let you all know how it went.

Thanks again for all the help!

---

### Post by Mark Phelps on 2016-11-22
It's "Mark" not "Michael" -- the SECOND one is the Olympic Gold Medalist. :)

---

### Post by linux.girl on 2016-11-23
Ooooooops!!!!! Super sorry!!! :-) :-) :-)

---

### Post by linux.girl on 2016-11-28
Hi Guys,

Suggestion by Mark Phelps worked. I disconnected the HD where ubuntu is installed, re-installed windows on the other HD, reconnected the ubuntu HD, updated grub and all is working fine.

Thanks everyone for all the help, marking this thread as solved.

Cheers!

---

### Post by RobGoss on 2016-11-28
Glad you were able to get things running

---

