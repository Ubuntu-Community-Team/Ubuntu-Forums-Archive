---
title: "Installing Ubuntu 16.04 alongside ubuntu 14.04, partition just hangs"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by jafoti on 2017-09-10
So I've had a bit of an experience this weekend, and a lack of focus coupled with distractions got the best of me.  Luckily I did have the foresight to backup password keychains and other vital files before all this started.

First, I inadvertently did an upgrade on 14.04 that resulted in a kernel panic upon reboot.  No matter what kernel I tried to boot from (.26, .63, .65), I got a kernel panic.  Same when trying each one in recovery mode.  Ugh.  I decided it's finally time to finally upgrade to 16.04, but I don't want to compound the problem.  I had a USB boot ready to go with 16.04, popped that in, and selected "Try Ubuntu" first.  Booted up, everything's OK.  My thought was to try and back up what I could then install 16.04.  Oops, no perms!  OK, So I choose "Install 16.04.3 alongside 14.04.3"  thinking I'll boot from 16.04, back up and import what I can, no harm, no foul.

I went with the default partition sizes -  the existing 14.04.3 installation partition would be 581GB, and then 16.04 would be 411GB on a Western Digital 1 TB HDD.

 It's been at least ~30 minutes now and we haven't moved past the partition screen.  I could hear the HDD chatter away a bit when it started, but all is silent now from what I can tell.

Is this normal in the partitioning process, or do I have some real problems now?

---

### Post by jafoti on 2017-09-10
And we have moved along!  Now installing 16.04!  

After what I've been through it's been a bit of a hear

---

### Post by jafoti on 2017-09-10
Yes, I'm feeling a bit overwhelmed and not thinking straight, so please bear with me.  This has all been thrust upon me without my expecting any of this.

OK, I survived the HDD partition hang, now I have another problem.  The problem I have with Linux is I know just enough to be dangerous, which has probably led to what happened here.

The 16.04 install alongside 14.04 looked successful, but upon reboot, I got a the original kernel panic that led me to got down the side-by-side install.

When I reboot using the live USB  I did the 16.04 install from, I can see the 16.04 partition, and I can navigate through it, but I just can't seem to boot from it!!!  The live USB boot was a UEFI boot.

Upon reboot I got into the BIOS thinking I just need to set the 16.04 volume as the main partition, but the HDD shows up as a 1TB volume, not the different volumes.

Any help you can give this overwhelmed, frustrated user will be greatly appreciated!!!  Time for a few deep breaths...

---

### Post by ajgreeny on 2017-09-11
Threads merged as they are the same problem.

Solved tag removed.

---

### Post by oldfred on 2017-09-12
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jafoti on 2018-03-24
oldfred,

I'm finally getting back to this issue as I've been fine without 14.04, and finally have some time to mess with this.

Just to be clear, you suggested running Boot-Info, NOT Boot-Repair from a live installer, correct?

---

### Post by oldfred on 2018-03-24
Just the report for now.

Very occasionally Boot-Repair does something automatically that we do not want. Usually it does work or does no harm.
With BIOS/MBR and Multiple drives it does install grub to all drives, so no matter what drive is default in BIOS, it will  boot. But usually we want different installs to have its boot loader in another drive.

---

### Post by jafoti on 2018-03-24
oldfred,

OK, hopefully this is what you want!

[http://paste.ubuntu.com/p/9xVzdZbmQq/](http://paste.ubuntu.com/p/9xVzdZbmQq/)

BTW, thanks for the help and interest in solving my issue.

---

### Post by oldfred on 2018-03-24
It looks like MBR is still set to boot 14.04 install.
BIOS only boots from MBR.

And you installed the grub for 16.04 into the PBR - partition boot sector for sda1, you 14.04 install. But there is no way to use that.

Boot-Repair's auto fix wants to reinstall grub of first found install or your 14.04.
You should use Advanced mode and choose the 16.04 install and MBR of sda to reinstall grub and see if then you can directly boot 16.04 install.

---

### Post by jafoti on 2018-03-24
Thanks.  I'll do some reading up on Advanced Mode first instead of just leaping blindly into running it.

It also seems to explain why I have to boot from command line to get into the 16.04 partition.

---

### Post by jafoti on 2018-03-24
> You should use Advanced mode and choose the 16.04 install and MBR of sda  to reinstall grub and see if then you can directly boot 16.04 install.

"Main Options" tab "Reinstall GRUB" is checked but "Restore MBR" **is** **not**.  Do I want to check this box?
"GRUB Location" tab I can select 16.04 as "OS to boot by default."
"GRUB Options" nothing is checked.  Is there anything I should check in this box.
**"MBR Options" tab is** **disabled**.  

This has me a bit concerned as you state 
> MBR of sda to reinstall grub
but I am unclear on what you mean by this.

---

### Post by oldfred on 2018-03-24
If you only have sda, there is only one MBR, so it may not show options.
I have not used it and always have had several MBRs.

If manually doing it and not using Boot-Repair you have to specify the drive.
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda 

When you specify a drive like sda, the boot loader is installed to the MBR of that drive. 
Almost never specify a partition like sda6.

---

### Post by jafoti on 2018-04-07
Well, I ran Boot Repair and can now boot into the 16.04 partition.  Thanks for the help!

Now to work on accessing the 14.04 partition.  I still get a kernel panic when trying to boot into 14.04 even after running Boot Repair.

I also cannot access it via the desktop from 16.04.  But, I believe this is probably an issue for a new thread!

"The link &#8220;Access-Your-Private-Data.desktop&#8221; is broken. 

This link cannot be used because its target &#8220;/usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop&#8221; doesn't exist."
[URL="http://http://paste.ubuntu.com/p/zBc7XmHrty/"]
http://paste.ubuntu.com/p/zBc7XmHrty/[/URL]

---

### Post by oldfred on 2018-04-08
You show an encrypted swap in fstab on sda1, so you encrypted /home in your 14.04 install.
So you have to unencrypt it to be able to see it with your passphrase.

[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) 
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

