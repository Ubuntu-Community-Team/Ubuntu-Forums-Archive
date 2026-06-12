---
title: "Ubuntu installation not seeing hard drives"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by kwilliams0 on 2006-06-22
Hello,

During my installation, the process hung when trying starting partman to partition the hard drive.  Looking into this it was because it couldn't find the hard drive.  I have an Adaptec 7890 storage controller, and a American Megatrends Perc2/SC raid controller.  I configured this as a raid 5 logical drive.  After the system hangs, I looked in the /dev directory, and there were no /sd* entries, which I would expect.  I ran lsmod and saw that aix7xxx was listed.  However megaraid (mod_scsi) was not.  I ran modprove -a megaraid, but there is still no /dev/sda listing.  I'm not sure how to troubleshoot this, or what to do.

On a side note, I noticed that the installation failed to load the ide_core, ide_mod, ide_probe_mod, and one other ide module.  Is this potentially part of the problem?  

I had gentoo installed on this box originally so I know linux CAN see the system--just not ubuntu:(

Any pointers or recommendations for how I can further troubleshoot this, or even better resolve this, would be greatly appreciated!   I already posted this on the chat room, but no one could help me.

---

### Post by prismatic7 on 2006-06-30
having a similar problem with a PowerEdge 2450 and PERC3/SC controller. The installer flakes when the partman component is launched - it can't identify any volumes on the system. I've tried modprobe -a aacraid (the driver Dell specify) and modprobe -a megaraid (as above) and nothing works. This is a critical issue for me because I have to ressurect this server for a very demanding client! Help!

---

### Post by kwilliams0 on 2006-06-30
Well, I found the root problem, and the solution.  Apparently the Linux 2.6 kernel (specifically the megaraid module) dropped support for the PERC2/SC controller.  I found out I had two ways to solve this--1.  Buy a newer raid controller, 2.  download the 2.4 kernel, recompile the megaraid module, copy the new megaraid module WITH PERC2/SC support on an Ubuntu boot disk, and overwrite the current one with the newly created one.

Given that I my skills with linux do not delve into compiling kernels and modules, I did option 3.  Decided this was a test server, and I didn't really need RAID anyway.

I'm not sure if the new kernel supports the PERC3/SC controller, but it sounds like you have the same problem, so it wouldn't surprise me.  I just don't understand why the REMOVED support for hardware...people always brag about how linux runs well on old hardware, well this issue proved that statement wrong.  OK, enough ranting...  Prismatic7, I hope this information helps you.

---

### Post by prismatic7 on 2006-07-02
[QUOTE=kwilliams0]Well, I found the root problem, and the solution.  Apparently the Linux 2.6 kernel (specifically the megaraid module) dropped support for the PERC2/SC controller.  I found out I had two ways to solve this--1.  Buy a newer raid controller, 2.  download the 2.4 kernel, recompile the megaraid module, copy the new megaraid module WITH PERC2/SC support on an Ubuntu boot disk, and overwrite the current one with the newly created one.
[/QUOTE]

Gah. Yeah, looks like that's the answer. Or, like you: 3. F*** it all off and run it up some other way. Which'll be Netware. and totally unsuited for the purpose.

Why can't I have the IBM x346 they promised me?

---

### Post by zagadka on 2006-07-23
Damn, What can I say. Kinda goes against the whole Linux idea eh... Removing support...

I'm in the same boat. It's giving me the shits.

I got it running on 5.04 with some of the lower version kernels. See the other thread for details on my setup.

[http://ubuntuforums.org/showthread.php?t=109509](http://ubuntuforums.org/showthread.php?t=109509)

I have hoary running on it with the following kernels:
2.6.10-10-5-386
2.6.11-1-686-smp
2.6.10-6-686-smp

EDIT:
exerpt from thread at:
[https://www.redhat.com/archives/nahant-list/2005-February/msg00077.html](https://www.redhat.com/archives/nahant-list/2005-February/msg00077.html)

DELL Release notes:
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/release-notes/as-x86/](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/release-notes/as-x86/)

[QUOTE="DELL RHEL4 Release Notes"]
# The kernel shipped with Red Hat Enterprise Linux 4 includes the new 
megaraid_mbox driver from LSI Logic, which replaces the megaraid driver. 
The megaraid_mbox driver has an improved design, is compatible with the 
2.6 kernel, and includes support for the latest hardware. However, 
megaraid_mbox does not support some of the older hardware that was 
supported by the megaraid driver.

Adapters with the following PCI vendor ID and device ID pairs are not 
supported by the megaraid_mbox driver:

vendor, device

0x101E, 0x9010
0x101E, 0x9060
0x8086, 0x1960

The lspci -n command can be used to display the IDs for adapters 
installed in a particular machine. Products with these IDs are known by 
(but not limited to) the following model names:

     * Dell PERC (dual-channel fast/wide SCSI) RAID controller
     * Dell PERC2/SC (single-channel Ultra SCSI) RAID controller
     * Dell PERC2/DC (dual-channel Ultra SCSI) RAID controller
     * Dell CERC (four-channel ATA/100) RAID controller
     * MegaRAID 428
     * MegaRAID 466
     * MegaRAID Express 500
     * HP NetRAID 3Si and 1M

Both Dell and LSI Logic have indicated that they no longer support these 
models in the 2.6 kernel. As a result, these adapters are not supported 
in Red Hat Enterprise Linux 4.[/QUOTE]

I know it pertains to RHEL but it's Dell and AMI (now LSI) who care for the driver, meaning unless someone picks it up, we're screwed right?

EDIT2: I just stuck a SUSE 10 install disc in to see if it would pick it up, it did. Although, it did not start in normal mode, it had to be run using the safe option.

I would prefer Dapper if I can make it work =(

EDIT3: FC5 doesn't work with default settings, however, after some research, I found that booting the installer with "linux noprobe" and manually selecting LSI MegaRAID (megaraid) and NOT the megaraid_mbox as well it works. The test is going to be wether it boots or not =) [It boots, 2.6.15-1.2054_FC5smp]

I need some Dapper images now!

---

### Post by llbbl on 2006-07-28
We have a Dell Poweredge 4400 dual 600mhz machine with PERC 2.5  RAID controller. I have been having problems getting Linux installed on the machine. I was able to get FreeBSD 6.1 installed, but I really wanted a distro with a package manager. I tried:

Fedore Core 3
Ubuntu 6.06
SUSE 10.1

With SUSE I tried installing it under the safe option and it didn't work. With FC3 I tried the linux noprobe but the megaraid driver wasn't listed. It probably would work if I had tried FC5. 

I was able to get it working with Hoary 5.04 Ubuntu, than I upgraded to Breezy 5.10 Ubuntu. Not sure what kernel I am running now. 

I have a question. If I upgrade to Dapper will it break it? I really would like to be able to install php5 but I can't get it working with Breezy. I have minimal server install so there is no window managers. Please don't address my php5 problems, that is best left for another thread. :)

---

### Post by aeble on 2006-07-31
I tried installing to an HP NetServer LH 3 with an Integrated NetRAID Adapter (based on LSI). Neither 5.04 nor 6.06 (server) recognize the adapter (not even when it is set to Mass Storage mode - the I2O mode doesn't work at all), to no avail.

I'm sure it is a driver problem - both FreeBSD 6.0 and SuSE 10.1 recognize the adapter and work well. SuSE 10.1 uses a 2.6.16 kernel with the megaraid driver.

If I had more time I might want to troubleshoot and see if I can get somewhere with the alternative installation image or maybe with explicitly loading the megaraid driver on boot. However, I'm not that deep in Ubuntu at the moment.

Any help or hints are welcome (I'd really prefer to have Ubuntu on that system).

---

### Post by aeble on 2006-07-31
> **llbbl said:**
> Not sure what kernel I am running now.

Run uname -r (or uname -a) to see what kernel you're running.

---

### Post by llbbl on 2006-08-01
Ok thanks. I discovered after upgrading to breezy it didn't work. 2.6.10 is Hoary and 2.6.12 is breezy. 2.6.11 works also.

I downloaded FC5 and am going to use that instead. Thanks for all the help/info.

---

### Post by gpeters on 2006-08-03
Sounds pretty jerky to have a fresh new release that actually drops hardware support.  How is FC5... I may try this as well- though I remember bad times with FC3 though...ungh...  I really want this to work. sigh

---

### Post by RX7Godfather on 2007-02-27
OK, I may have found an answer, at least it is working for my NetRAID 1Si SCSI controller.

You need to enter the bios of your scsi card, usually Ctrl+M while booting, locate somewhere in your scsi config utility the emulation section, you may have to dig for it, I know I did....

Change your SCSI emulation from I20 to MASS STORAGE, erase your array (you will lose everything on your drives) and rebuild and initialize it. This way Ubuntu will not see multiple installations and will erase the entire disks.

After doing that, try to install it again, so far it is working with my NetRAID 1Si controller.

Hope this helps...

---

