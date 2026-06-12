---
title: "Install/boot problem"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by bouldie12 on 2013-03-18
Hi,

I think I've arrived at some kind of twilight zone :-)
I have a HP proliant MD350 G4 server with Windows 2003 installed. I wanted to create a dual boot with ubuntu.
The server has an ATI video card, which is not recognized by the live DVD. I managed to install ubuntu anyway (on a RAID1 drive), but now when I boot my server, I only get the message "Trying to boot from disc c:", and there it gets stuck.
I guess this is a problem with GRUB, so I started the boot repair disc. But because the harddisc is RAID1, the standard boot repair doesn't continue and indicates that I should use the linux secure remix version which is supposed to be able to handle RAID1 discs with a more advanced version.
When I start the linux secure remix DVD, it indicates that it doesn't recognize the video card, and that I should continue at low resolution. However, whatever I choose, I can't get past, the system gets stuck.

So... How can I proceed? Would it be possible to install the advanced boot repair version after starting up with the standard boot repair DVD? I have the feeling I'm at a non-standard combination of circumstances: unrecognized video card and ubuntu installed on a raid1 disc.

Any suggesions?

Best, Bo

---

### Post by oldfred on 2013-03-18
I do not know server nor AMD, but I have a couple of links.
What version of Ubuntu?

12.10 server may not have AMD drivers for old versions.
 This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for Ubuntu 12.10 Quantal Quetzal.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

The Desktop versions of 12.10 do not have RAID Drivers by default. But in live mode you can add them.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
> There are several options for installing using software RAID.  You can: 

[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 
[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 
[/LIST]


I thought Boot-Repair added the RAID drivers automatically?
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bouldie12 on 2013-03-19
Apparently there are 2 versions of Boot-repair, the standard one and the one that comes with linux secure mix. The standard one doesn't support RAID1 (nor LVM, I had ubuntu installed with LVM at first and reinstalled after a warning of boot-repair)
I'm still not sure what my problem is, it might be a problem with grub, or it might be that my raid is considered a fake raid (it's a hardware controller but it doesn't seem full fledged) and doesn't start up correctly.

So following you comments:
I've installed 12.10 desktop.
If I want to run the live DVD, how and at what point could I install the video drivers before I get the low resolution warning?
In what sense would it help me to install the RAID drivers using the live DVD? You mean regarding boot-repair?

---

### Post by oldfred on 2013-03-19
I guess it depends on version of Boot-Repair.
But you can install RAID or LVM anytime to a liveCD that does not have them.
       sudo apt-get install lvm2
sudo apt-get install mdadm

For Video, Ubuntu usually will offer in System Settings, Additional drivers, offer the correct driver. But with liveCD you cannot reboot and have it as everything you install to liveCD is gone. But with Video I think you log out out & log back in and then new driver should work.

---

### Post by bouldie12 on 2013-03-19
Hi,

as far as I can see now, I have 2 ways to go:
1. start the live DVD and somehow install the video drivers before it fails to proceed; this way I can start up the enhanced boot repair and try to repair GRUB; any idea how I can do this?
2. Start up the boot repair DVD (which has no problem with the video drivers), and somehow install the enhanced boot-repair. How Can I indicate I want the advanced boot-repair?

Either way has it's own problem I don't know how to resolve.

I tried to install the mdadm yesterday, but it doesn't recognize any RAID arrays

---

### Post by oldfred on 2013-03-19
You can usually use nomodeset or other boot parameters to get into a low quality video and then install video driver. If just repairing grub low quality video may be all you need?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by bouldie12 on 2013-03-19
Hi,

for the live DVD, when I choose the nomodeset option (F6 and then clic the predefined nomodeset option), it still tells me that I have low graphics, and asks me what I want to do: just this one time low graphics, etc. From there on I can't move on.
What I do notice is that I get a "I/O space for GPIO uninitialized" error before the system warns me about the low graphics; I don't know if this has something to do with it.

---

### Post by oldfred on 2013-03-20
There is this bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035698](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035698)
But on the Arch site they say the error is not critical, so I do not know.

But then you may need other kernal boot options. With quiet splash removed do you see any other error messages? It does go by quick and last entry is not usually the error.

---

