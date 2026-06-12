---
title: "No standard floppy drive was found"
date: 2022-01-16
forum: Installation &amp; Upgrades
---

### Post by ^*#gop* on 2022-01-16
Hello,

Following the thread regarding installing Ubuntu 5.04 from USB and installing via VM, my frustration with high latency mouse movement reminded me why I hated using VMs at work! So, after shouting at the screen numerous times, I decided to search through 30 boxes for CDs. Found one and used K3B to burn 32 bit Ubuntu 5.04 to CD. Amazingly, workstation booted from CD without interaction. Good sign! BUT, a screen appeared as alluded within attachment. "Select your floppy device:". WHAT? 5.04 was released in 2005 not 1985! So, why on earth does the installation require a floppy device? Also, the title of the screen mentions CD which is mounted! None of the options work!

Thank you.

---

### Post by MAFoElffen on 2022-01-16
What were is your hardware that all this is going on, "on"?

If you could run the UbuntuForums 'system-info' script in my signature line, that would give us a clearer picture of what we are trying to recommend solutions "for." 

I had said if you had any further questions on your VM, you could ask those in the Virtualization Section... If you had posted there, and described your VM config, we could have recommended tuning changes that might have helped with your latency concerns...

Note to others, he has a requirement to use this to develop for an Embedded ARM32 board. Long story, but that is the summary.

---

### Post by ^*#gop* on 2022-01-16
I have no intention of using VM so, will persist with attempting to install from CD. The attachments include hardware specification for installation and extract from TITAN Technical Manual stating Intel processor rather than ARM; albeit ARM compliant.

---

### Post by MAFoElffen on 2022-01-17
Yes, albeit made by Intel, it is functionally ARM arch that you are developing for... I read that manual, plus the manual that Titan released for their Development Kit for that board, which came with an early version of CentOS... Yes, It said supports Linux Kernel Version 2.6.x. My memory is pretty good.

What I said in Post#2, was said to try to "get you help", and for you to be welcomed by others (instead of what happened last time...) Not all here may have seen your other thread, and how it started with people shutting the door on you automatically, just because Ubuntu 5.04 (Hoary) is a very long out-of-support version. Remember, that I was one person that understood and did try to help you in whatever you wanted, because (me) as a Developer, I can see what you wanted, and needed to do. Remember that I am one of the few left around here that have supported it... And even reinstalled myself it to refresh my memory, and to supply you with screen shots, to help you through installing it...I don't thin I said anything that was off-track or offensive...

I'm tired, just coming off a closing shift of a very long week. Seeing your reply, and with the intent to see what kind of help you want...

Now I ask myself why help you(?) I feel a bit offended. Maybe you are just in a bad mood or do not need help? IDK. It matters no more to me. I can make myself useful helping people that actually need and want help.

Here you go:
[Ubuntu Installation Guide 5.05 Hoary]("http://old-releases.ubuntu.com/ubuntu/dists/hoary/main/installer-ia64/current/doc/manual/en/index.html")

Good Luck with your journey. Well wishes to you.

---

### Post by ^*#gop* on 2022-01-17
How is stating no intention of using VM offensive? I am suffering an inordinate amount stress without needing more! So, delete my profile.

---

### Post by MAFoElffen on 2022-01-17
Not using a VM is not offensive. Trying to support aversion of Ubuntu that has been unsupported for over 15 years, to run on modern hardware, that it didn't have drivers for, because the idea of current hardware was not even thought of yet... Is a bit of a challenge. Using a VM was a way to simulate that older hardware, without you having to get any real additional hardware. (Which you said was a challenge for you.) 

In the original thread, you didn't have an optical drive, and the Install CD  ISO was hard coded to check for a CD Drive. When that ISO was written, USB Booting was not around back then as any option in BIOS. Lots of hardware from back then, to include Network cards, versions of USB, WiFi Cards, etc... Are going to be challenge to include in that interim unsupported version...  

Sorry... I was a bit touchy by the time I got off work last night...

IDK. Let's see where this goes now, and if it is even possible.

On the Floppy Drive message... I seem to remember that message. But I even I didn't have floppy drives on all my machines by then. They were not much space and unreliable. Funny to say that now, when I can remember getting a newly released "20MB" IDE HDD and thought I would never run out of space. I don't get that message now, on that ISO, from a VM without a FD device configured... I just rechecked my config.No Floppy configured, and never asked me about it. 

Hmmm. I don't know. Let me test something different and see...

---

### Post by ^*#gop* on 2022-01-17
I was very nervous about viewing this thread but feel more relaxed after reading your latest post. Firstly, I apologise if I was offensive which was not my intention. I appreciate your assistance in addition to other members in this forum. I have never been a fan of VMs. Anyway, thank you again for your assistance.

---

### Post by MAFoElffen on 2022-01-17
I think I found the bad and good news for you, by drilling down through some specific things...

I didn't find this on the 5.04 ISO, but rather on the 4.10 ISO (one interim version earlier) Being this was 16-17 years ago, it was the early release of the debian-installer... I mounted the 4.10 ISO to read through the files, scripts, and documentation that is within the ISO itself. In /doc/install/ there is a file called  "INSTALLATION-HOWTO"... I posted this file for you, as for some reason, even with adding a .txt. extension, it wouldn't upload as an attachment.... Reading through it explains some things to me... It might be useful for you with some work-arounds...

```

How to install sarge with the new debian-installer
--------------------------------------------------

This document describes how to perform an installation with the new
debian-installer, which will be released together with the upcoming
Debian release, codename: sarge.

For the most current version of this document or more information on
the debian-installer project: http://www.debian.org/devel/debian-installer

Last update: $Date: 2004-07-28 21:40:07 +0000 (Wed, 28 Jul 2004) $


1. Preliminaries

The debian-installer is still in a beta state. If you encounter
bugs during your install, please refer to section 5 on how to report
them. If you have questions which cannot be answered by this document,
please direct them to the debian-boot mailing list
(debian-boot@lists.debian.org) or ask on irc (#debian-boot on the
freenode network).

Recently the debian-installer has switched to ask only the important
questions and configure the rest automatically. This also means that you
won't get to see the main menu anymore, except when something goes wrong.
If you want to restore the old configuration with more questions asked,
type "expert" at the boot prompt. If you do so, refer to section
3.1. for installing rather than section 3.

This HOWTO is mainly targeted at users of the i386 architecture, although
the instructions are similar for all architectures. For more detailed
information, see the Debian Sarge Installation Manual:
http://d-i.alioth.debian.org/manual/


2. Getting images

The debian-cd team provides builds of CD images for debian-installer here:
http://cdimage.debian.org/pub/cdimage-testing/daily/

The other kinds of images, including floppy images are in the Debian
archive, in the main/installer-<arch> directories. For example:
ftp://ftp.debian.org/debian/dists/unstable/main/installer-i386/current/images/

Daily builds of all non-ISO debian-installer images, including floppy images 
and initrd's are available, for a complete list with links, see
http://www.debian.org/devel/debian-installer/ports-status

The subsections below will give the details about which images you should
get for each possible means of installation.


2.1 CDROM

There are two different netinst images at the location above which can be
used to install sarge with the debian-installer. These images are intended
to boot from CD and install additional packages over a network, hence the
name 'netinst'. The difference between the two images is, that on the full
netinst image the base packages are included, whereas you have to download
these from the web if you are using the business card image.

Download whichever type you prefer and burn it to a CD.

2.1.1 SCSI CD drives

If you have a SCSI CD drive and a relatively uncommon SCSI controller, then
you may also need one driver floppy to let the installer see your CD drive.
However, this is only the case with CD images that use syslinux as their
bootloader, rather than the normal ones, which use isolinux.

See section 2.2 for information about floppys, and download the cd-drivers
floppy image and write it to disk. You will be given an opportunity to load
drivers from the floppy if the installer fails to see your SCSI CD drive,
and after loading the floppy, the installer will see your CD ROM.

2.2 The dreaded floppies

If you can't boot from CD, you can download floppy images to install
Debian. You need the floppy/boot.img, the floppy/root.img and possibly
one of the driver disks.

- floppy/net-drivers.img
  To do an install over the network with a few common ethernet cards,
  you do not need this driver floppy. If you have a less common ethernet
  card, or pcmcia, you will need it.
- floppy/cd-drivers.img
  If you have a cdrom, but cannot boot from it, you can boot from floppies,
  and use this driver disk to complete the install using the cdrom.

Floppy disks are one of the least reliable media around, so be prepared for
lots of bad disks. Each .img file you downloaded goes on a single floppy;
you can use the dd command to write it to /dev/fd0 or some other means.
It's a good idea to them use cmp to compare what ended up on the unreliable
floppy disk with the image. If it fails throw that floppy away and try
again. Since you'll have more than one floppy, it's a good idea to label
them.

The boot floppy is the one with boot.img on it. This floppy, when
booted, will prompt you to insert a second floppy -- use the one with
root.img on it. 

2.3 USB memory stick

It's also possible to install from removable USB storage devices. For
example a USB keychain can make a handy Debian install media that you
can take with you anywhere.

The easiest way to prepare your USB memory stick is to download
hd-media/boot.img.gz, and use gunzip to extract the 128 MB image from that
file. Write this image directly to your memory stick, which must be at
least 128 mb in size. Of course this will destroy anything already on the
memory stick. Then mount the memory stick, which will now have a FAT
filesystem on it. Next, download a Debian netinst CD image, and copy that
file to the memory stick; any filename is ok as long as it ends in ".iso".

Alternatively, if you're using linux and familiar with loopback mounting,
it can be quicker to loop mount the disk image, copy the iso into it, and
only then write the complete image to the memory stick.

There are other, more flexible ways to set up a memory stick to use the
debian-installer, and it's possible to get it to work with smaller memory
sticks. This web page has more complete directions for using
debian-installer and a bootable USB stick: http://d-i.pascal.at/

2.3.1 Booting directly from USB storage

Some BIOSes can boot USB storage directly, and some cannot. You may need to
configure your BIOS to boot from a "removable drive" or even a "USB-ZIP" to
get it to boot from the USB device. The web site above has more information
and some helpful hints about booting.

2.3.2 Using USB storage and a boot floppy

The debian-installer can be booted off a single floppy, which will be able
to access your USB memory stick. To boot the installer this way, you will
need to put the floppy/boot.img on a floppy (see section 2.2).

Now boot from the floppy. It should detect your USB device and proceed
with booting from it.

2.4 Booting from network

It's also possible to boot debian-installer completely from the net. The 
various methods to netboot depend on your architecture and netboot setup. 
The files in netboot/ can be used to netboot debian-installer.

On i386, the easiest thing to set up is probably PXE netbooting. Untar the
file netboot/pxeboot.tar.gz into /var/lib/tftpboot or wherever is
appropriate for your tftp server. Set up your DHCP server to pass filename
"/pxelinux.0" to clients, and it with luck everything will just work. For
more details, see this web page:
http://wiki.debian.net/index.cgi?DebianInstallerNetbootPXE

2.5 Booting from hard disk

It's possible to boot the installer using no removable media, but just an
existing hard disk, which can have a different OS on it. These instructions
are for i386 systems, such as those running windows. Download 
hd-media/initrd.gz, hd-media/vmlinuz, and a Debian CD image to the top-level
directory of the hard disk. Make sure that the CD image has a filename
ending in ".iso". Now it's just a matter of booting linux with the initrd.

If you have grub installed, boot grub, and do the following:

grub>kernel (hd0,0)/vmlinuz root=/dev/ram ramdisk_size=10000 devfs=mount,dall
grub>initrd (hd0,0)/initrd.gz
grub>boot

Note that the ramdisk_size parameter may need to be increased, depending on
the image you are booting.

After the installer boots, it should find the ISO you placed on the hard
disk, and continue with the install. You will not be able to reformat the
partition the installer was booted from if you use this technique.

2.6 Booting from CDROM

The most common choice, is booting directly from a CD drive.

For i386 systems, you should set this up in your BIOS directly
in the boot sequence.

For powerpc systems, you must press the "c" key while booting. The "c"
key, which represents "cdrom", will tell your machine to use that medium
as the boot method.

3. Installation

From here on, I assume you have downloaded and burnt the 'netinst'
CD. Put it into your CD-drive and make your system boot from CD.

You will be greeted by a welcome screen. Hit ENTER to boot. (If you want a
2.6 kernel, type "linux26" instead.) 

After a while you will be asked to select your language. This will affect
translation of debian-installer (if already available for your language) as
well as the choice of country and keyboard layout. Select your language and
press ENTER to continue.

Sit back while debian-installer detects some of your hardware, and
loads additional installer modules from the cd.

Next the installer will try to detect your network hardware and set up
networking by DHCP. If you are not on a network or do not have DHCP, you
will see an error message. You do not need a network to continue the
install, so this can be easily worked around. Select continue and watch the
main menu which will appear everytime if something went wrong, so you have
more control over the situation. Proceed to "Partition disks".

Now it is time to partition your disks. First you will be given the
opportunity to automatically partition either an entire drive, or free
space on a drive. If you do not want to autopartition, choose manual from
the menu.

On the next screen you will see your partition table, how the partitions
will be formatted, and where they will be mounted. Select a partition to
modify or delete it. If you did automatic partitioning, you should just be
able to choose "Finished partitioning" from the menu to use what it set up.
Remember to assign at least one partition for swap space and to mount a
partition on "/".

Now debian-installer starts to install the base system which can take a
while. That is followed by installing a kernel.

The last step is to install a boot loader. If the installer detects
other operating systems on your computer, it will add them to the boot menu
and let you know. By default GRUB will be installed to the boot
record of the first harddrive, which is generally a good choice. You'll be
given the opportiunity to override that choice and install it elsewhere.

Debian-installer will now tell you that the installation has
finished. Remove the cdrom from your drive and hit ENTER to reboot
your machine. Make sure it boots from harddisk, cross your fingers and
wait until base-config is started.

Stepping through base-config is not within the scope of this document
as it is not part of debian-installer.


3.1. Expert mode installation

From here on, I assume you have downloaded and burnt the 'netinst'
CD. Put it into your CD-drive and make your system boot from CD.

You will be greeted by a welcome screen. Type "expert" and hit ENTER to
boot. If you want to install with the 2.6 linux kernel, type "expert26"
instead. After a while you will be presented with the main-menu of the
debian-installer.  Some general remarks:

The main-menu is not static. New entries are added when new installer
modules are loaded. However main-menu tries to resolve the next best
choice and presents that as default selection. If that selection does
not suit your needs just select another entry. If you select an entry
that requires the configuration of an entry you did not yet choose,
the main-menu will try to resolve these dependencies automatically.
This can be used to automate the install process, by selecting always
the last visible step. 

When main-menu first is shown, the default will be "Choose language". Hit
return and choose your language from the list that now is presented. You
will be taken back to main-menu and the next item will be the default,
which is "Choose country". Select that entry and observe that the installer
tries to set a reasonable default based upon your language selection.
Select your country and continue.

The next step is "Detect a keyboard and select layout". Again the installer
will attempt to pick a reasonable default. Select your preferred keymap and
continue.

The next step is "Detect CDROM devices and mount the CD". As part of this
step, the installer will probe the system for hardware, and load kernel
modules for detect hardware. You will be given a chance to veto the loading
of kernel modules (in case they cause problems), and to specify parameters
to pass to the kernel when the modules are loaded. After the hardware is
detected, the CD should be found automatically in most cases.

Now we are able to load the rest of the installer. Select the corresponding
entry "Load installer components". Since the modules we want to access are
on the CD, select "cdrom-retriever". The floppy-retriever can be used to
load additional modules from a floppy, e.g. if you have exotic hardware.
See section 2.1.1 if you have a SCSI CDROM.

You are presented a long list with optional components to install. We
only want to install the standard components, which are selected
automatically, so just hit "Continue". Wait and watch until all
components have been loaded.

Main-menu appears again, but with the additional modules there are new
entries. The next default step would be to configure a network. We are
breaking out of the default route, because we do not need networking
since the base debs are on the CD.

Select "Detect hardware". This will repeat the hardware detection process,
but now the installer has more kernel modules available to it.

Now it is time to partition your disk, so choose "Partition disks" from the
menu. You will be presented with a display showing the partitions on your
system. Select partitons from the list to modify or delete them. If you
have free space it will also show up under a drive, and you can select it
to create new partitions. When modifying a partition you will have the
opportunity to choose the file system to use, and where to mount it. The
partitioning menu also has a choice at the bottom that can be used to
automatically partition a drive or existing free space on a drive, if you'd
rather go that route. Be sure to create at least two partitions, one for
swap and one for the root filesystem.

After finishing partitioning, select "Finished partitioning" from the menu,
and confirm that the filesystems should be created as requested.

Now we are ready to install the base system. Select the corresponding entry
("Install the base system") and lean back. The packages are retrieved from
the CD and installed in the /target area. During this step, you will be
presented with a list of all available kernel images on the CD. Select the
most suitable for your system and wait until the installation has finished.

Now we are almost done. Select "Install GRUB on a hard disk" or
"Install LILO on a hard disk" to make your harddisk bootable. You will
be asked where GRUB/LILO shall install the bootblock. A good idea is
the first hard drive in your system which should be in fact the
default selection.

If that last step has completed successfully select "Finish the
installation and reboot", eject your CD and wait until your computer
restarts. Make sure it boots from harddisk, cross your fingers and
wait until base-config is started.

Stepping through base-config is not within the scope of this document
as it is not part of debian-installer.


4. Installation Report

If you successfully managed an installation with debian-installer,
please take time to provide us with a report. There is a template
named "install-report.template" in the /root directory of a freshly
installed system. Please fill it out and file it as a bug against the
package "installation-reports". See section 5 on how to file bugs.


5. Reporting bugs

If you did not reach base-config or ran into other trouble, you
probably found a bug in debian-installer. To improve the installer it
is necessary that we know about them, so please take your time and
report them.

First, look here to see if your bug has already been reported:
http://bugs.qa.debian.org/cgi-bin/debian-installer.cgi?full=yes

The page is sorted by packages which represent the individual
subsystems of debian-installer. File your bug against the respective
subsystem or, if you do not know which it is, against the package
"install". Look here for an explanation of how to file bugs:
http://www.debian.org/Bugs/Reporting


6. Get involved

The Debian-Installer Team always welcomes people who would like to
work on the installer. We have plenty of work to do: fixing bugs,
improve usability, create new modules and of course extensive
testing. If you are interested to help, check out this page:
http://www.debian.org/devel/debian-installer/

```
Then I dug through old bug reports... Which prompted me t dig through the history of SATA and SATA Optical drives...

*** Summary, Ubuntu 5.04 does not have a driver for your SATA Optical disk drive... SATA HDD's didn't come out until 2003... But SATA DVD drives didn't come out until after 2005, which they early ones were PATA, with a SATA crossover bridge... True SATA DVD Mulitdrives didn't arrive until 2007-2008...

So during the Probe to find the CD drive, it didn't find one on an IDE controller, so it thought and failed back to searching for an older type SCSI Optical drive (note the scsi devices shown), which weren't able to boot logically, so probed to floppy drive... As noted in the instructions above...

So no... Can't install it that way on newer hardware. The reason it could boot and install on VM, is that KVM default machine for that version of Ubuntu uses an IDE controller, which that ISO does have drivers ofr that kind of controller, to be able to see the virtualized CD drive.

I'm not sure there was a backport for kernel modules for SATA DVD drives for that series kernel.

But those instructions did have other ideas...

---

### Post by ^*#gop* on 2022-01-17
Thank you. I will action after Technical Assessment Interview on Wednesday as I need to practice C/C++ interview questions.

---

### Post by MAFoElffen on 2022-01-17
> **puremathematics said:**
> Thank you. I will action after Technical Assessment Interview on Wednesday as I need to practice C/C++ interview questions.
Understood that making a living is a priority. Always a good thing.

The good news to keep in the back of your mind, for after that... That Doc says it will install from disk (file), from a loop device... which means it will also install as a Grub2 menu Item, booting the ISO file as a loop device. Talk to you about that later.

Good luck with your interview!

---

### Post by ^*#gop* on 2022-01-23
Thank you. Failed technical interview for C/C++. For example, no understanding of Template Specialisation. Researched since and discovered this is easy! Anyway, regarding your post, I awaited another post as per your statement "Talk to you about that later". In the meantime, I attempted to download SuSe Linux 9.2 for DVD but 3.1 G would take 10 hours! Even though, I have FTTP at 78 mbps! Should only take about 6 minutes. So, I will persist with Ubuntu 5.04.

---

### Post by ^*#gop* on 2022-01-24
Another reason why I hate VMs is that a shared folder is required to copy files between host and VM. I have spent 12 hours trying to get this to work. Just do not have the intelligence to solve this problem!

---

### Post by tea for one on 2022-01-24
> **puremathematics said:**
> Another reason why I hate VMs is that a shared folder is required to copy files between host and VM. I have spent 12 hours trying to get this to work. Just do not have the intelligence to solve this problem!

Have you considered [COLOR="#0000FF"]gnome-boxes[/COLOR]?
Gnome-boxes is a simpler virtualisation program with fewer settings than Virtualbox or KVM/Qemu.
It has automatic "drag and drop" file sharing from Ubuntu host to Ubuntu guest (or possibly Linux host to Linux guest?)
You drag the file to the guest desktop and it is automagically sent to the Downloads folder in the guest OS.

Just tested with Ubuntu 21.10 host and Lubuntu 21.10 guest.

Whether it will work with Ubuntu 5.04 as a guest, I really do not know.

Worth a try?

---

### Post by MAFoElffen on 2022-01-24
@Tea For One...

LMAO! You know that "Gnome Boxes" is a Front-end tool for QEMU/KVM right? KVM is the host for it, with Gnome Boxes being the virt viewer for... But what that does allow is simple ways to connect and share between. I use a few ways to share between. Network File Shares, shared directories, raw drives marked as shared, USB drives, etc.

@puremathematics...

Dang. I was hoping for you. 

Your Linux Host boots via a Grub Menu right?I think I remember you saying your host in Ubuntu, so I know it does. I create entries in my '40_custom file, some of mine are ISO files, to use as to rescue or reinstall. Look at this:
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

Those are instructions to boot an ISO file as a loop device...

---

### Post by ^*#gop* on 2022-01-24
tea for one - I will investigate gnome-boxes.
MAFoElffen - Yes, Ubuntu 16.04 and 14.04 hosts boot from grub menu. I will read the instructions.

Thank you.

---

### Post by tea for one on 2022-01-24
> **MAFoElffen said:**
> @Tea For One...

LMAO! You know that "Gnome Boxes" is a Front-end tool for QEMU/KVM right? KVM is the host for it, with Gnome Boxes being the virt viewer for... But what that does allow is simple ways to connect and share between. I use a few ways to share between. Network File Shares, shared directories, raw drives marked as shared, USB drives, etc.

Yes, I did know this.

I was trying to help the OP overcome the Shared Folder dilemma.

Gnome-boxes is easy to install and pretty easy to run if other Virtualisation software offers too many settings/choices.

---

### Post by MAFoElffen on 2022-01-24
@Tea For One

There are a few threads in the Virtualization section on sharing folders between the host and VM Guests. In fact there is a good current thread open now for discussion there now.

The challenge that would limit him is he is Ubuntu 14 or 16 on his host, which both are out-of-support. Next is his VM Guest is Ubuntu 5.04... which anything installed to that would have to support running on a Linux kernel 2..6.x. So that limits things down to SMB/SAMBA and NFS fileshares. Most of the Guest virtio Services, he might have problems with, as they are written for modern Linux Kernels.

Virt Viewers are an option for him, if they support hooks into such an old Guest... I can test that for him. It might help if he ran the UbuntuForums 'system-info' script so we know what hardware, system, and system settings, so we can make a recommendation on any configuration tuning... 

I say that... Because- Ubuntu 5.04 is a 'very lightweight' VM Guest. I spun up an instance of it to help him on my old laptop. It is so lightweight, that I do not have any the lag in mouse, keyboard, etc... like he described. It does have it's limitations on Graphics as a Vm Guest (only VGA).

The only reason I said that, was we do not want to confuse him, into thinking that KVM would not be required if he was using Gnome Boxes. I apologize if my wording came out wrong. Not intended that  way at all. I actually think that might be easier and simpler connection for him to try to connect to his existing VM Guest. I just think we might also have some tuning recommendations for him to tune his guest.

---

### Post by ^*#gop* on 2022-01-24
Ran system-info script which created system-info.txt. Edited to replace my name with [REMOVED] as this appeared numerous times. But, Manage Attachments refuses to upload. No error message.

---

### Post by ^*#gop* on 2022-01-25
After much procrastination, I have decided to remove myself from the internet. My unemployment is causing me an inordinate amount of stress. Requested for my account to be deleted but can only be deactivated. Please accept my gratitude for all your assistance!

---

### Post by MAFoElffen on 2022-01-26
To post the report, you could have copy/pasted into post, within Code Tags... Or used the Upload routine, to upload it to a pastebin, and posted the link where it got uploaded. The "[REMOVED]" placeholders in that report, where put there to protect the privacy, and safe-guard sensitive information of users. What was 'removed' from the User's version of the onscreen report, to make it safe to be posted publicly was decide by my project team.

If you have any question on that, I am the Author, Project Leader, and the Admin for it's DEV/TEST Repo, and the UbuntuForum's 'system-info' Stable Repo's.

I can empathize with unemployment. Things are rough out here also. Though, being active doing 'something', to keep your skills sharp... Is better than going stale. At least for me. I try to keep busy, and am always striving to learn new things.

Tip-- I use my volunteer time spent 'here' helping people, on my Resume. I have also translated some opensource applications from Spanish-to-English and vice-versa. It doesn't pay any bills, but I thought of it as an investment in time.

Sorry to see you leave, but I do understand.

---

