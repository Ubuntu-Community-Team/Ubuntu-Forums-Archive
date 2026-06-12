---
title: "Laptop Install - Dual boot vs Virtual Box"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2011-07-25
All,

Have a Dell Latitude C640 with 500GB HD and segmented it to 2 250 GB partitions.  I installed Ubuntu on the second partition, but can not get it to boot, nor can I get the dual boot screen.

Not sure what I'm missing in the instructions yet.

Also I want to bring the first Win partition up under my Virtual-Box session, so I have all my Win stuff and can basically, once it is working right, eliminate the dual boot screen and go direct to Ubuntu accessing the Win under that.

All help appreciated!

Thanks!

OMR

---

### Post by Mr. Shannon on 2011-07-25
I don't think windows can be migrated from a hard drive to virtualbox.

About not getting the boot screen, did you have Ubuntu install the grub boot loader to the first partition or the second?

---

### Post by westie457 on 2011-07-25
> **OldManRiver said:**
> All,

Have a Dell Latitude C640 with 500GB HD and segmented it to 2 250 GB partitions.  I installed Ubuntu on the second partition, but can not get it to boot, nor can I get the dual boot screen.

Not sure what I'm missing in the instructions yet.

Also I want to bring the first Win partition up under my Virtual-Box session, so I have all my Win stuff and can basically, once it is working right, eliminate the dual boot screen and go direct to Ubuntu accessing the Win under that.

All help appreciated!

Thanks!
Hi, We are going to sort the boot problems for you.
Firstly, boot up the pc using a LiveCD/USB and select try.

When the dust has settled download and run bootinfoscript.
The download and instructions are here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

They even explain how to post the results.

This will give us more information and ideas on how to proceed

OMR
 Am looking at the VM idea that you have.
No idea at all if it can be done. No harm in looking though.

                  =====================================================================

That is the first time I have seen (or put) a reply in with the OP's question. :lolflag:

---

### Post by Old_Grey_Wolf on 2011-07-25
OldManRiver,

What are the specs for the CPU and RAM. I Googled for Dell Latitude C640, and the results I got don't look like you could run VMs on it; however, your machine my have better specs than what I found from Googling. Please post the CPU specs for number of cores/threads, processor speed, and GB of RAM. VMs use Virtual Disc Images (VDIs) rather than partitions. 

Virtualization is intended to separate operating systems and applications that run on those operating systems form the physical hardware. You may be able to find someone that can help you create a VDI from the partition of Windows you already have installed. The applications I know of for migrating a physical system to a VM are extremely expensive. It is possible that the no-cost-solution would be to backup important files from the Windows install, create the VM, and install the backed up data on the VM.

---

### Post by Mr. Shannon on 2011-07-25
I think the problem with moving Windows, is that it does not take kindly to hardware changes and a VM is certainly different hardware.

---

### Post by OldManRiver on 2011-08-09
All,

Thanks for the inputs, looking at and considering them all.  One of the options I think I have on the VM is that samba can be used to see the old Win XP disk and then, if not able to use VBox to actual boot the current windows install, then after installing new XP, can pull all the files from the current win partition and overlay the new, so all apps, etc are intact and working in the new installation.  Yeah lot of work, but maybe an option.

Then I would have to used and intelligent partition manager, reformat old win partition and pull it into the Ubuntu partition.

What do you all think?

Thanks!

OMR

---

### Post by gpost3 on 2011-08-09
You mean booting into a copy of windows that is already installed on your physical disk in a dual-boot configuration and using that through vbox? Sure it can be done.

I am actually in the process of writing entire blog entry for this here:
[http://ubuntuhelpportal.blogspot.com/2011/08/creating-virtual-machine-for-physical.html](http://ubuntuhelpportal.blogspot.com/2011/08/creating-virtual-machine-for-physical.html)

Meanwhile I suggest you look into here:
[http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)

---

### Post by OldManRiver on 2011-08-14
> **Mr. Shannon said:**
> I don't think windows can be migrated from a hard drive to virtualbox.

About not getting the boot screen, did you have Ubuntu install the grub boot loader to the first partition or the second?

MS,

The grub boot loader is not working at all, the main part of the problem, for which I've not found a good howto, thus have not been able to effect a fix.

If you know one, please pass along.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-14
> **gpost3 said:**
> You mean booting into a copy of windows that is already installed on your physical disk in a dual-boot configuration and using that through vbox? Sure it can be done.

I am actually in the process of writing entire blog entry for this here:
[http://ubuntuhelpportal.blogspot.com/2011/08/creating-virtual-machine-for-physical.html](http://ubuntuhelpportal.blogspot.com/2011/08/creating-virtual-machine-for-physical.html)

Meanwhile I suggest you look into here:
[http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)

Thanks for the links, think you got my idea down.

First gotta get the grub working to get back into the Ubuntu side, so I can knock it out, but thanks!

Cheers!

OMR

---

### Post by OldManRiver on 2011-08-23
> **gpost3 said:**
> You mean booting into a copy of windows that is already installed on your physical disk in a dual-boot configuration and using that through vbox? Sure it can be done.

I am actually in the process of writing entire blog entry for this here:
[http://ubuntuhelpportal.blogspot.com/2011/08/creating-virtual-machine-for-physical.html](http://ubuntuhelpportal.blogspot.com/2011/08/creating-virtual-machine-for-physical.html)

Meanwhile I suggest you look into here:
[http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)

All,

Some clarification:

Forget that I even mentioned Windows, it could be any OS and I am and avid "Don't Do Windows" person.  That is why it is getting trashed.  It's friggin 20 years behind Linux and everyone knows all Windows apps are stolen from the Lunix, so do not get me started.

Anyway, because there are certain things that I used as field telephony tech that require apps that I only have on the Window partition, that is why I must use Virtual Box and not a straight VM.  Not that Linux does not have the same apps, but I do not know there names so don't have installs on the Linux side for them.  Also my ACT db and all my MS-Access apps will not run under the Linux side, because OpenOffice has not figured out howto yet, mostly due to licensing, since nothing is free on Windows.

Obviously the exception to the normal VBox install, is that I do not plan installing a CD copy of XP, since I already have the working XP copy on the other partition of the drive.

I just have to study the information on this, given in the responses and then proceed with the attempt.  Once I have that up I will never be ever booting any Windows again.

Thanks for all the inputs!

OMR

---

### Post by haqking on 2011-08-23
Use clonezilla to take an image of your partition that you want in your VM.

create a VM hard disk with settings.  Boot it to the Clonezilla live CD or .iso

Clone the image back to the VM

Job done

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #26 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by xdwilko on 2012-06-09
OMR,

Paragon Backup & Recovery 2010 Free Advanced Edition includes a feature called P2V (physical to virtual) migration. 

I have not used this feature before so I am not sure which VMs it works  with but a google search for "p2v migration" reveals there are also a  number of alternatives, but most notably VMware Converter which is also  free and creates VMs which are compatible with VMware ESX/ESXi, Server  and Workstation.

I am currently running VMware Player 4.0.3 on Ubuntu 12.04 64-bit. It  was quite easy to install and it works perfectly however I was actually  just in the process of finding instructions for installing Server 2.0.2  (before stumbling upon your thread) as I have found Player is missing a  number of useful features which I have grown accustomed to in Server. 

I have very little experience with VMs other than these two but then I  have had no reason to look elsewhere... In other words although you are a  Virtual Box user I would recommend you try using a VMware Converter +  Server/Player combo for guaranteed compatability. If you give either of  these a go please let me know what you did and how it worked out for  you.

Hope this helps

[http://http://download.cnet.com/Paragon-Backup-amp-Recovery-Free-Advanced-Edition/3000-2242_4-11559170.html](http://http://download.cnet.com/Paragon-Backup-amp-Recovery-Free-Advanced-Edition/3000-2242_4-11559170.html)

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

[http://www.vmware.com/go/downloadplayer](http://www.vmware.com/go/downloadplayer)

---

### Post by OldManRiver on 2012-11-25
All,

I gave up on this for 2 reasons:
[LIST=1]
[*]Bought a new laptop,
[*]All machines are now 100% Ubuntu Linux.
[/LIST]
So marking this solved!

Cheers!

OMR

---

