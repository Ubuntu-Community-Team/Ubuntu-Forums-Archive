---
title: "Error in installer of Ubuntu 22.04.3"
date: 2024-02-01
forum: Installation &amp; Upgrades
---

### Post by greatashkan on 2024-02-01
Hi, 
I am installing Ubuntu 22.04.3 on a Dell r750 server. I mounted the iso via console and during the installation, in the section of checking for installer update it gives me the error which does not let me to move forward. 
I used UEFI with raid and I tried many combination but no luck. 
The error is in the attachment. Also the. error report is in the atachment. It raised some errors for split_lock which I could not found useful workaround for that.
Thanks,
Ashkan

---

### Post by MAFoElffen on 2024-02-04
> **greatashkan said:**
> Hi, 
I am installing Ubuntu 22.04.3 on a Dell r750 server. I mounted the iso via console and during the installation, in the section of checking for installer update it gives me the error which does not let me to move forward. 
I used UEFI with raid and I tried many combination but no luck. 
The error is in the attachment. Also the. error report is in the attachment. It raised some errors for split_lock which I could not found useful workaround for that.
Thanks,
Ashkan
Welcome to the Forum.

I used to be a Certified Dell, HP and Lenovo Onsite Warranty Tech, with extensive experience with Dell PowerEdge servers, and and have over 20,000 Linux Installs under my belt. I have also been on the Ubuntu Server Team since 2012.

The error seems to be a kernel boot error... But I know that these servers do boot Linux (well). First we need to ensure that the installer Live Image boots for you.

Tell me which ISO image you are trying to boot, how you verified that the downloaded image was good, and exactly how you are trying to boot it. How did you prepare the ISO to be booted? You said you mounted the ISO from console... Please explain that. Did you mean from the hardware's IDRAC management console? Does it get to the initial Grub2 boot Menu?

---

### Post by MAFoElffen on 2024-02-04
I don't usually do this. I usually just tell people to prepare removable USB media and create an Ubuntu Installer LiveUSB to boot from... 

But I since this is a recent DELL EMC PE, and you are trying to install from it's BMC iDRAC, I will share that with you. From my notes:
```

Log into iDRAC management softare, connect to the DellEMC Life Cycle (controller) screen of the server.

At that screen, use the "Get the latest firmware" option to update all the firmware of the server. Update all the firmware of the found hardware from the Dell site.

Afterwards: In the boot option, reboot the server.

DellEMC Life Cylce Screen > "Configure Raid and deploy OS" option. 

If RAID is alreay configured, confirm it says "Linux RAID" flavor instead of "Windows", select next. If not configured, select RAID level > drives, options, etc... Next > OK > Next > Next > OK.


OS Deplyment: OS Deploy

Connect Virtual Media:
Use that wizard to mount the ISO image from where it is located from using the Map CD/DVD option.

Select an Operating System:
 Select boot type = UEFI or BIOS.
 Secure Boot mode = Disabled 
 Secure Boot Policy = grayed out
 Secure Boot mode = blank
 From Operating System, the options of available does have RedHat... But not Debian, Ubuntu or VMware vSphere. Use the "Any other Operating System" option. Next.

Installation Mode = Manual

 Select OS Media = UEFI Boot (VirtualCD)
 
Reboot the System screen:
Review the selected options. Finish. 

Will reboot into the ISO Image of the installer...

```
Those are the options I use for Dell Servers with an updated, correctly configured iDRAC. That way I can install remotely, from an iDRAC Tools remote management console screen. If you are using an Ubuntu Desktop as a Management Console, then you are probably using this: [https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=xftc6](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=xftc6)

My previous home worksation was SuperMicro with an IMPI BMC. The process is similar for those, using IPMIView and SMCIPMITool.

The one related caution related to your error, ensure you verify the the ISO image is good.

---

### Post by MAFoElffen on 2024-02-04
The one thing I would recommend before you start... Is to think about what you are doing, and your set boundaries and requirements. This is hard set if this is commercial and a production environment, by others above you in the decision process, and your pay grade. Things you just have to live with and conform to.

If this is for personal use, you have so many other options that I would recommend that would give you so many other possibilities open to you with the hardware you have.

Think about that. If this is for personal use, tell me that, and what the job of this machine is planned for, and I will tell you what is a better path to follow.

---

