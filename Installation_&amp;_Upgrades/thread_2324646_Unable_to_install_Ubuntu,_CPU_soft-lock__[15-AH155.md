---
title: "Unable to install Ubuntu, CPU soft-lock  [15-AH155NR][FX-8800p]"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by bckwalton on 2016-05-15
[TABLE="class: table table-bordered table-steps"]
[TR]
[TD="align: left"]**_Backstory:_** I've had this laptop for a few days now and I told myself that I would stick with windows for as long as I can (usually I jump over to some flavor of Linux immediately) to see how the other side lives. Well, after finally getting annoyed with Windows 10's surprise updates, I noted that there was nothing I was doing on Windows that I couldn't do in Linux. So I decided to jump ship, I heard good things about Elementary OS so I thought I would try that. I downloaded the 64-bit ISO and flashed it to a Flash drive with RUFUS and restarted. I had my PC in Legacy Boot support so it loaded the flash drive immediately. I selected try and then the logo froze. I restarted and tried it again but pressed f1 so I could see the outputs. It quickly flashed super suspicious text and started stating "BUG: soft lockup - CPU#0 stuck for 25s!" I was spooked so I decided to see if it was the ISO. It passed a hash check so I figured it was the OS, and decided to try old faithful (Ubuntu), It ran into the same error. I tried Nomodeset to no avail.

**_Issue:_** I am unable to install any version of Linux do to a "BUG: soft lockup -CPU#(It varies) stuck for (also varies)!" or at least I believe that to be the issue. I've tried Ubuntu, ElementaryOS, and Mint. All failed in similar fashions. I'm at my wits end with this I've tested every ISO to verify their integrity, I've used Rufus, UNetbootin, UUI and they all created a bootable drive that inevitably failed.

***_Laptops Specs:_***
Processor: FX-8800p
Graphics: Radeon R7
Storage: 256GB Sandisk SSD
RAM: 6GB Hynix (4GB + 2GB)


_**A bit of Intel I've gathered on the matter:**_ Apparently the Carrizo APUs are in various stages of being supported by the Linux Kernel and not, but I heard this information from Forums that are almost a year old now. Has the situation changed? Is there a way to triage this issue? Do I have no idea what I'm talking about :confused:[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[/TABLE]

---

### Post by grahammechanical on 2016-05-15
What version of Ubuntu did you try? If it is 16.04 then you should see this from the release notes. Known Issues.

> [h=2]Graphics and Display[/h]  
[h=3]fglrx[/h] The  fglrx driver is now deprecated in 16.04, and we recommend its open  source alternatives (radeon and amdgpu). AMD put a lot of work into the  drivers, and we backported kernel code from Linux 4.5 to provide a  better experience. 


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 

More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

When installing do not tick the box "Install third party software." That will attempt to install a proprietary video driver as well as some audio & video codecs. It may not be the solution to this problem but it will simplify the situation as an AMD proprietary video driver does not exist in Ubuntu 16.04.

Regards.

---

### Post by bckwalton on 2016-05-15
Hello,

I tried version 16.04 . That sounds like it could be the problem, would that cause the CPU soft-lock issue? I'm unable to reach any form of a GUI, it fails shortly after the GRUB menu with try, install, oem install, etc. 

So should the problem be fixed by trying an earlier version? (I'm going to try that now)

---

### Post by bckwalton on 2016-05-15
Well... Things got weird quickly. So I put Ubuntu 15.10 on a flashdrive and tried to run the install, and it RAN! I was excited when it finished, but then it restarted and everything went black. I restarted and added nomodeset to the boot commands and it started sending soft-lock errors again. If i try it on recovery mode it acts like its going to start, but just doesn't, no error message or anything it gets up to dhcp.h then stalls and then I restarted it. :( So there was progress, but another roadblock has appeared

---

