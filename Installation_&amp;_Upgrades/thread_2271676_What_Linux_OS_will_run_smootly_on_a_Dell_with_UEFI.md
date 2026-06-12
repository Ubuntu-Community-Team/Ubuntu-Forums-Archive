---
title: "What Linux OS will run smootly on a Dell with UEFI?"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by Rick_Smith on 2015-03-31
Have a new Dell Inspiron 3646 with that ridiculous UEFI system, that I previously knew nothing about, and cannot get Ubuntu 14.04 to run without bugs. Win8 has been deleted. Installed from the Live CD and for about 2 weeks everything was fine. Then the bugs showed up. Biggest is about every 4 or 5 days things start malfunctioning, programs don't run right and other things too varied and numerous to mention, so I restart and it stalls in the middle of the process. I have to turn the computer off, literally push the button, and that's the only way it will restart. From what I've been reading Ubuntu is just not going to run on a computer with UEFI. I hate to give up on Ubuntu, really like it but, I need something that will run properly.

---

### Post by kurt18947 on 2015-03-31
I would recommend doing a search for user "Old Fred" and read his various posts. He's the resident wizard when it comes to UEFI. He also has some useful links in his sig.

---

### Post by Rick_Smith on 2015-03-31
Thanks, I'll do that.

---

### Post by grahammechanical on 2015-03-31
> [COLOR=#000000]From what I've been reading Ubuntu is just not going to run on a computer with UEFI.[/COLOR]

Where have you read that? I do not accept that statement as true. Ubuntu is Linux and Linux works well with GPT, secure boot and UEFI. Installation is tricky because the manufacturers work hard to make sure Windows is installed and working properly but care little if Linux has trouble installing. You said it yourself:

> [COLOR=#000000]for about 2 weeks everything was fine. [/COLOR]

If the problem was UEFI then the issues would be there from the start. Check the threads on this forum. People often say the installation went fine and then they restarted and that is when they hit trouble.

What were you doing during those two weeks? What did you install? What modifications did you make. We cannot help you unless you are specific about the problems. And I do not think that the problems are an incompatibility between Linux and UEFI.

---

### Post by Bucky Ball on 2015-03-31
Ubuntu will run fine with UEFI, but I'm wondering why you're using it if it is causing headaches. You have no Win installed, so why not just use legacy mode and install problem free?

Wipe the drive to unallocated space, reboot, go into the BIOS and set the machine to boot in legacy rather than UEFI. That is a Windows thang. ;)

As everything was running fine for a fortnight prior to these problems rolling up, are you sure you issues are related to UEFI and not something else?

---

### Post by oldfred on 2015-04-01
Dell's have in the past worked better than many others. 
They go to an extra effort with the top of the line model designed to run only Linux.
And they in the past released sputnik to add extra drivers to 12.04 to make it work with older Dells. All those extra drivers were in 14.04 as I understand.

Some of the very new Broadwell systems may have issues.
 Dell M3800 with 14.04 Some issues
[http://arstechnica.com/gadgets/2015/03/review-dell-m3800-developer-edition-is-a-great-linux-pc-with-a-few-rough-edges/2/](http://arstechnica.com/gadgets/2015/03/review-dell-m3800-developer-edition-is-a-great-linux-pc-with-a-few-rough-edges/2/)
Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

      Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Sometimes setting in UEFI that do not seem like they are related are vital. They say this may apply to all Intel systems. See details even though for M3800.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

What are specs on your system?
Which processor chip, video card/chip

Some with major issues have used Legacy/BIOS/CSM mode. But Windows wanted vendors to not back port any drivers to BIOS or Windows 7 for those systems with Windows 8. But vendors had too many customers (often business) that use older versions as standard and have to keep that older version but may want newer computer.
You should be able to use CSM mode but newer hardware added in later may not have BIOS drivers.

---

### Post by mattharris4 on 2015-04-02
I haven't tried any Canonical OSes on a recent Dell but I do know they sell computers with Linux pre-installed.  With that in mind I would expect that if installed properly on a recent Dell computer it should work (unless as Old Fred said you have a very new Broadwell chipped computer but that would probably be the case with any brand of computer equipped with that chip, Canonical programmers will probably correct that within the next month or two).  I also have to agree that if the computer worked fine for two weeks UEFI is not likely the issue.  I would go back and try to remember what you have installed in the past week or so, if all of your programs came from a Canonical repository maybe an update didn't take (Canonical OSes update almost daily).  I haven't run into that issue (I have been using Edubuntu for almost a year now) so I am not familiar with reversing updates on Linux -- but that does not mean you didn't have a corrupted update.  I know in Windows the computer will install a restore point before updating just in case something like this happens but I have not run across anything like that for any Linux OS.  If no one knows a way to reverse updates (and you haven't installed any non-repository programs lately that could cause the issue), since you have wiped the drive of other OSes anyway I would try to back up documents and wipe/reinstall Ubuntu, disabling UEFI (since you don't have a Windows install you don't need it), Fast Boot, Secure Boot (shouldn't be necessary but since it is useless for Linux installations anyway why not eliminate the possibility) and whatever else is instructed.  Here is a link to Canonical's documentation although it is more for a dual-boot with UEFI:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

For the record I have installed Lubuntu (a lighter version of Ubuntu with a different interface) on a 2014 model Toshiba laptop dual booted with Win 8.1 and haven't had any major issues with it (it actually works better than Windows on it -- it has a crappy power saver CPU and Lubuntu is less CPU intensive than Win 8.1).  The install went smoothly (really smoothly IMO) after disabling Fast Boot and a couple of other things the Ubuntu instructions say to disable.  I did wait about seven months before doing the Lubuntu install giving Canonical time to create drivers for the AMD processor.  I do know that if the computer had a recent version of Windows on it (the version Office Max sells does) I would not have wiped the drive before a Ubuntu install but that is my hang-up, not yours.

Good luck and I hope you get your computer working smoothly.  It is possible that you have a hardware problem but I would do the wipe/reinstall first before calling the computer repairman.  Since the computer is a desktop (Google is my friend here) you may even be able to repair it yourself if it comes to it.  You may have borked your warranty here messing with the Windows install but if a wipe/reinstall does not take care of the issue it could be as simple as a bad RAM stick or hard drive -- both easy fixes (or as complicated as a bad processor which is not reasonably repairable).  You have a Celeron J1800 processor which has been out for a few months now so drivers for it should be baked into Ubuntu -- ruling out one of Old Fred's concerns.

---

### Post by gordintoronto on 2015-04-02
This really looks like a hardware problem, most likely memory or hard drive. When you run Disks (Disk? Disk Utility? Sorry, I'm not running Ubuntu 14.04.) does it say the hard drive is healthy?

---

