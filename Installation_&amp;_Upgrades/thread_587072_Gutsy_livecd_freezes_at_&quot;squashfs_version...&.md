---
title: "Gutsy livecd freezes at &quot;squashfs: version...&quot;"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by closet geek on 2007-10-22
Hi,

I have downloaded the Gutsy LiveCD but I can't get it to boot. When I boot in safe graphics mode with nosplash I see that the install stops at the line:

"squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher"

the cursor just blinks and it sits there. I've verified the CD and there are no issues according to Ubuntu. What can I do to get past this step or stop it from freezing?

cg

---

### Post by Pumalite on 2007-10-22
Post your specs.

---

### Post by closet geek on 2007-10-22
> **Pumalite said:**
> Post your specs.

AMD processor
1.5GB RAM
ATI x1300 card
NForce based motherboard

I've never had problems with previous versions of Ubuntu.

cg

---

### Post by Pumalite on 2007-10-22
With an ATI card, go for the Alternate CD. You'll have to fix your xserver at the end anyway. Come back then.
Check this:
[http://ubuntuforums.org/showthread.php?t=581562](http://ubuntuforums.org/showthread.php?t=581562)

Re: Feisty and Gutsy not working with ATI X1400
This is a solution from [http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/](http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/)
and I listed it on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.04 should now boot into GDM/KDM.

---

### Post by closet geek on 2007-10-22
Hi,

When I left it long enough it finally booted into a desktop (20 minutes+), I had to reconfigure X first of all. I then had to kill the user switching applet which was using 100% of the CPU. Then I ran the install and it froze at 53% of copying files. Very poor indeed.

cg

---

### Post by Pumalite on 2007-10-22
Forgot to tell you: you have to install with the Alternate CD.

---

### Post by closet geek on 2007-10-22
> **Pumalite said:**
> Forgot to tell you: you have to install with the Alternate CD.

You did tell me this, but I don't see *why* that should be the case. I like any normal curious user simply went to ubuntu.com, downloaded the CD image and suffered a very poor experience because of this. There shouldn't be different CD's, there should be one CD that works for all. It's not like previous live CD's haven't worked for me.

I'm just very disappointed, my hardware is a few years old and certainly not cutting edge or exotic by any stretch of the imagination.

cg

---

### Post by Pumalite on 2007-10-22
Not everyone has the same hardware; that why the Alternate CD exists. To solve problems like yours.

---

### Post by closet geek on 2007-10-22
> **Pumalite said:**
> Not everyone has the same hardware; that why the Alternate CD exists. To solve problems like yours.

I have incredibly normal, non-exotic and bog-standard hardware which every single other version of Ubuntu has had no problems with at all. Seriously now.

---

### Post by jbencic on 2007-10-31
Maybe unrelated 

I too have the same problem only the original LiveCD works fine for me , no freeze 

for every Ubuntu version i need to have installed LVM2 support so every version i unpack the squashfs from the livecd install lvm2 and re mksquashfs, mkisofs. This has worked flawlessly until now, i have AMD proc, Nvidia graphics...

this is the only version that i have had this problem with

something is not quite right here 

anyhow eventually it boots and all works fine, i do a dmesg and it looks fine from what i can see (no errors)

to get it to boot i have to press  a random number of keys + ctrl  then hit return and it continues past the message 

> "squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher"

does anyone have any ideas on how to better debug this problem rather than using the Alternative CD?

:confused:

---

### Post by Pumalite on 2007-10-31
You guys are funny; they give you a solution and refuse to download an iso. (LOL)

---

### Post by Data Doctor on 2008-01-11
After booting from the Gutsy Live CD, I selected F6 for boot option, and added **acpi=force pci=noacpi** to the boot line, but my Gutsy install still hung at squashfs, until I added more RAM. I realized I only had 64 MB of RAM installed, added 128 MB, and it no longer hangs at squashfs. It's still pretty slow to install though, so I'll probably try more RAM!

---

### Post by DavidTangye on 2008-02-14
I have the same problem still with a new Gigabyte GA M61SME-S2 mb, which has nvidia GeForce 6100, Nforce 405 chipsets, and an AMD CPU. I wonder if the squashfs software does not like that combination.

---

### Post by leeping on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126964) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi there,

I ran into the same problem with the Ubuntu Live CD - but this time, I was trying to get it to boot off the network.  My goal was to get twelve compute nodes in a Beowulf cluster to boot off a master server which hosts the Ubuntu CD over NFS - I would then clone the OS across these compute nodes using "netcat".

I added modules for my network hardware to the initrd.gz ramdisk, and I also modified the startup scripts in initrd.gz to boot up properly using NFS (the startup script is currently faulty.)  The system hangs at:

"squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher"

I was finally able to get past this hang by hitting a random combination of keys (it involved CTRL, Enter, ALT, and basically mashing my hand on the keyboard), but I have no idea why this works.  Then I found this forum thread and found that someone else had done the same thing :)

I tried the special boot parameters specified above, to see if it would solve my problem; it did not work.

I would use the alternative desktop CD, but the alternative desktop CD wouldn't allow me to use a network bootable live OS; this is essential for me, because I have twelve computers without CD-ROM drives.  I am aware of LTSP, but for various reasons, netbooting a live CD is the best option for me.

I would use an older Ubuntu CD if that option were available; alas, older live CD's do not support my motherboards' SATA controller, so I wouldn't be able to access the hard drives.  It seems like the Ubuntu Gutsy live CD is the only solution I have, and I hope that this bug gets fixed somehow.

Specs: 12 x the following:

ASUS P5E-VM HDMI LGA 775 Intel G35 HDMI Micro ATX Intel Motherboard
Western Digital Caviar SE16 WD2500AAKS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive
Intel Core 2 Quad Q6600 Kentsfield 2.4GHz LGA 775 Quad-Core Processor
pqi TURBO 8GB(4 x 2GB) 240-Pin DDR2 SDRAM DDR2 533 (PC2 4200) Dual Channel Kit
Antec earthwatts EA430 ATX12V v2.0 430W Power Supply

As you can see, very standard setup.  Furthermore, I booted into my LiveCD server with a virtual machine and it also hung at squashfs.

---

### Post by leeping on 2008-02-16
The magical key combination is ALT + ENTER, if that helps at all.  I wonder what purpose ALT + ENTER usually serves?

---

### Post by DavidTangye on 2008-02-17
Great advice, thanks. I tried it and it works for me too. I am going through the logs to see what is happening. My guess it that Alt-Enter frees up an X configuration process, that relates to some hardware, eg nVidia based graphics? being a problem with some new (post-Feisty, anyway) ubuntu software.

---

### Post by Pumalite on 2008-02-17
Here is the answer of a creative guy to a somewhat similar problem:

' Re: [Errno 5] Input/Output Error - SQUASHFS ??
Pumalite, there is nothing wrong with the iso / cdrom / cd drive
got it working without getting a new iso

I think my hard disk was the problem.
Not sure though what exactly the problem was.

Here is what I did:

   1. booted live installation
   2. partition manager (geparted) setup 1 partition ext3 and 1 swap partition
   3. ran a check disk, fix errors option in gparted
   4. right clicked on "install" icon on the desktop copied the command to install ubuntu 7.10 desktop
   5. opened a shell and run the command without any parameters. it will start the installation process in gui mode
   6. step 3(?) partitioner, selected 3rd option (no wizards) and edited mount point on first partition
      from '/dev/sda1' to '/' (root)
   7. in one of the next screens is an 'advanced' button, clicked that button and deselected option install grub loader'



'

---

### Post by Ev1L on 2008-06-30
> **DavidTangye said:**
> Great advice, thanks. I tried it and it works for me too. I am going through the logs to see what is happening. My guess it that Alt-Enter frees up an X configuration process, that relates to some hardware, eg nVidia based graphics? being a problem with some new (post-Feisty, anyway) ubuntu software.
I got the same problem trying to install Ubuntu Ultimate on VirtualBox, and I solved increasing RAM from 256 to 512MB.

Give it a shot if you can :)

---

### Post by DavidTangye on 2008-07-04
FYI:
I have just set up a bootp tftp server to boot the live Hardy CD image via pxe netboot as per my old notes at [help.ubuntu.com/community/Installation/LocalNet]("http://help.ubuntu.com/community/Installation/LocalNet") . The same issue appears on two of my PCs, a laptop and one running nVidia. Alt-Enter is still required to get past the freeze at the squashfs line. The Hardy live desktop then appears after the rest of the bootup has completed.

---

