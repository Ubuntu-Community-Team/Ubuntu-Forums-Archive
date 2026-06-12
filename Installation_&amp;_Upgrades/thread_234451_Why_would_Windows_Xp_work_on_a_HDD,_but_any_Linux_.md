---
title: "Why would Windows Xp work on a HDD, but any Linux systems do not on the same HDD???"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by joople on 2006-08-11
Hello, I hava this 20gig HDD which is an IBM Deskstar.  
My problem is I can install and run Windows Xp just fine on this hard drive, but for some reason I cannot do the same for any Linux system. I've tried Ubuntu, Mepis, and SUSE; Meaning I can install each system fine, but after install I can't boot into the system. It gives me a "DISK BOOT FAILURE..." everytime.

Please Help me out. I'm begging!! Please!!

Does it mean that windows is more compatible with HDD's then Linux?

---

### Post by 23meg on 2006-08-11
Are you 100% sure it's an issue with your HD? Is it recognized without problems at the install stage, and does everything go fine with no errors? Does the Ubuntu live CD work without problems? 
> Does it mean that windows is more compatible with HDD's then Linux?No. For years I've heard of all sorts of compatibility problems but nothing of this sort.

---

### Post by joople on 2006-08-11
No I am not 100% sure that it is a HD problem, but this is so bizarre that I have no clue as to what is going on. Yes absolutely no errors during installation using SUSE 10.1, Mepis, Ubuntu, and Alternate Ubuntu. Runs perfectly smooth. I can even access the files using Knoppix live cd. So I know it installed to the HD. 

Clean insatll of Windows works

Clean install of Linux doesn't

Conclusion.... WIERD!!

---

### Post by 23meg on 2006-08-12
Weird indeed. This is most likely an IDE HD, right? Boot with the live CD and see what your IDE controller device is listed as in Device Manager. Maybe there's a bug specific to this controller. 

Have you tried installing to a different HD with the same hardware configuration?

---

### Post by joople on 2006-08-13
> **23meg said:**
> Weird indeed. This is most likely an IDE HD, right? Boot with the live CD and see what your IDE controller device is listed as in Device Manager. Maybe there's a bug specific to this controller. 

Yes this is a IDE HD. It's a Deskstar (IBM-DPTA-372050). Why would there be a bug with this specific controller, that only is affected when a linux format is activated?

> **23meg said:**
> Have you tried installing to a different HD with the same hardware configuration?

No I have not tried that because I don't really want to mess with my other hard drive that has Windows on it. Too much of a hassle to back up everything.

It just doesn't make since?

---

### Post by 23meg on 2006-08-13
[QUOTE=joople]Why would there be a bug with this specific controller, that only is affected when a linux format is activated?[/QUOTE]What I mean is that there may be a Linux bug or compatibility issue that affects your specific controller, or you may have to issue a kernel boot option (unlikely) or recompile your kernel with a certain configuration (even more unlikely) for it to work. I've searched for specific issues with your HD and there seem to be none, but what I asked before was what your *IDE controller *is listed as, not your HD.

---

### Post by joople on 2006-08-13
> **23meg said:**
> I've searched for specific issues with your HD and there seem to be none, but what I asked before was what your *IDE controller *is listed as, not your HD.

Oh my mistake it is listed as "5513[IDE]" from Silicon Integrated Systems.

so SIS PCI IDE Controller.

---

### Post by randell6564 on 2006-08-13
> **joople said:**
> Hello, I hava this 20gig HDD which is an IBM Deskstar.  
My problem is I can install and run Windows Xp just fine on this hard drive, but for some reason I cannot do the same for any Linux system. I've tried Ubuntu, Mepis, and SUSE; Meaning I can install each system fine, but after install I can't boot into the system. It gives me a "DISK BOOT FAILURE..." everytime.

Please Help me out. I'm begging!! Please!!

Does it mean that windows is more compatible with HDD's then Linux?

Could it be that in your bios, your MBR is set to virus protection? If it is then linux has been unable to install the Grub boot loader. 

This is what it sounds like to me since you say that the entire installation goes well until you reboot.

---

### Post by joople on 2006-08-13
I've looked all in my BIOS (Award). And I can't see anywhere that says that it has virus protection enabled? I'll look again.

---

### Post by randell6564 on 2006-08-13
> **joople said:**
> I've looked all in my BIOS (Award). And I can't see anywhere that says that it has virus protection enabled? I'll look again.

I believe you.  I had some boxes that did'nt have that option either.

So.,the next question is.,are you sure that Linux installed grub to the MBR?

---

### Post by joople on 2006-08-13
> I believe you. I had some boxes that did'nt have that option either.

So.,the next question is.,are you sure that Linux installed grub to the MBR?


positive. I've checked it in Knoppix  And I also reinstalled many times in the live CD Terminal.

I even installed GRUB on a dual boot system; I put it into the MBR of windows and still wouldn't work. But don't worry I'm not even considering dual boot; right now I'm only dealing with Linux.

I even installed GRUB on to a floppy using the alternate cd and that didn't work.

---

### Post by confused57 on 2006-08-13
See you still haven't had any luck getting your Linux to boot...wonder if a separate boot partition would work, probably not.

You might want to check into the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

or 
GAG boot floppy:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

Good luck, again...

---

### Post by randell6564 on 2006-08-13
> **joople said:**
> positive. I've checked it in Knoppix  And I also reinstalled many times in the live CD Terminal.

I even installed GRUB on a dual boot system; I put it into the MBR of windows and still wouldn't work. But don't worry I'm not even considering dual boot; right now I'm only dealing with Linux.

I even installed GRUB on to a floppy using the alternate cd and that didn't work.

Wow!  Thats crazy!  So you are trying to install knoppix on a clean HDD? No windows, no nothing!

Thats strange!  If it's not working (cuz it's sounds like everything that you tried ie.,dual-boot was correct), I would get another iso or whatever and try again.

I have done many dual-boots and many single installations with ubuntu, xubuntu, kubuntu, Xp, and never had boot issues.

I would install and place grub in the MBR and everything worked.

Sorry man, I'm lost!

---

### Post by joople on 2006-08-14
yes Im doing a complete clean install.  Thanks for all the help guys, I think im concidering it a lost cause. Oh well I was planning on buying a brand new computer, or putting one together rather, this computer is getting old its 2002. peace:-({|=

---

### Post by Frogger on 2006-08-14
Check to make sure your BIOS is not set to PnP OS.
Unless I am mistaken the IDE controler uses PnP unless told otherwise, and while I realize much of linux's PnP issues are solved, in order for me to install to my SiS Computer, I has to disable PnP

---

### Post by jimmygoon on 2006-08-14
Make sure that you either install grub to the mbr or that the partition you assign ubuntu/grub to IS BOOTABLE! On my Dad's PC the crappy Windows Restore disc wiped the HD but didn't set it to active so I had to use a Gparted Live disc to make it "bootable"

---

### Post by joople on 2006-08-14
> Make sure that you either install grub to the mbr or that the partition you assign ubuntu/grub to IS BOOTABLE! On my Dad's PC the crappy Windows Restore disc wiped the HD but didn't set it to active so I had to use a Gparted Live disc to make it "bootable"

Thanks, yes I have checked that before and it was active.

> Check to make sure your BIOS is not set to PnP OS.
Unless I am mistaken the IDE controler uses PnP unless told otherwise, and while I realize much of linux's PnP issues are solved, in order for me to install to my SiS Computer, I has to disable PnP

Cool I will look at that. haven't heard of that, but I am able to have windows xp working on this hard drive so im not sure this is the problem.

---

### Post by joople on 2006-08-14
Ok so I put PnP to "NO". And still did not load.

Dang I really was hoping that would work. Had my toes and fingers crossed.:(

---

