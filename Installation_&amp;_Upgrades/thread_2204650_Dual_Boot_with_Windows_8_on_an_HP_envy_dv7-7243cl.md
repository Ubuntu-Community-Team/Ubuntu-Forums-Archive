---
title: "Dual Boot with Windows 8 on an HP envy dv7-7243cl"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by Don_Phillips on 2014-02-09
Hi all,

I'm beginning to doubt my sanity.  I probably know far too much to be more that just a little dangerous.  I'd been hoping that seridipty would solve the issuses without my having to get more under the hood.

I have an HP envy dv7-7243cl with 16GB of ram, dual 1TB HDs configured as RAID1 via Intel's onboard chip, Insydeh20 bios, with Windows 8 that came factory installed, but has had it's partitions changed and then imaged.  Windows 8 is functional before I try to install Ubuntu.  I also have 15 years of experience usin openSuSE, but decided to give Ubuntu a spin.  My servers are currently running an old version of OpenSuse, but I want to consider migrating them to Ubuntu.

I've been through many cycles of restore the Windows 8 image, try to install Ubuntu 13.10 from DVD, get the message from UEFI saying that I have to first install an operating system, use boot-repair from CD, and be stuck with no bootable OS.

Just for more fun, the RAID has to be set up in order to load the Windows 8 image that I made (in which the drives were configured as RAID1).

I've got a partition configured with cryptsetup so that the entire partition is/should be encrypted.  That partition is configured with LVM so that I have a lvm-root(ext4) of 50G, lvm-swap(swap) of 32G and a lvm-home(ext4) of 742G.  I have a separate ext4 boot partition that mounts at /boot.

The long story short is that I've tried all of the methods that I've been able to find.  I'm now beginning research to try and find out precisely what the EFI boot sequence is attempting so that I can try and repair it.

Is anybody up for kibitzing on the experience with me?  I'll add screenshots and other data if there's interest.

Regards,
Don

---

### Post by oldfred on 2014-02-09
Is the efi partition outside the RAID?
And is Ubuntu /boot outside the encrypted LVM?

Standard desktop install has not supported RAID, only server version. 

 EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

      
 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

All this is before UEFI/gpt.

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

12.10 posted this. When they did away with the Alternative installer they said they would add RAID to the desktop, but now it is not even mentioned in the newer release notes.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer)

> 
[LIST]
[*]There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 

[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 
[/LIST]
[/LIST]




---

### Post by Don_Phillips on 2014-02-09
Hi oldfred,

I neglected to mention:  I also have an HP Pavillion DV6 that is successfully dual booting Windows 7 and Ubuntu 13.10.  So I wasn't totally insane to be trying this new configuration.  ;)

First, thank you for your interest and questions.

> **oldfred said:**
> Is the efi partition outside the RAID?

No.  The RAID, as configured by the factory, is RAID1 on the entire device.  

The LIVECD 13.10 install disk sets up each partition as it's own RAID.  The RAID configuration will successfully boot WIndows 8.

> **oldfred said:**
>  And is Ubuntu /boot outside the encrypted LVM?

Ubuntu boot is on it's own RAID partition and is neither in the LVM nor is it encrypted.

> **oldfred said:**
>  Standard desktop install has not supported RAID, only server version. 

Yep.  I read that somewhere.  I tried using the server version of 13.10 and ended up with a system that had no network interfaces.  I suspect that I ended up with the wrong kernel.

I also read [http://ubuntuforums.org/showthread.php?t=1782296](http://ubuntuforums.org/showthread.php?t=1782296) that gave me the (possibly bad) idea of how to set up LVM.  I read another article on how to use cryptsetup.

I could be misremembering, but I believe that when "something else" was selected during the installation process, I was offered the option to encrypt a partition.

I'm willing to believe that it's not working.  I'll plead being mislead by the tools.

> **oldfred said:**
> EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

      
 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)

RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

All this is before UEFI/gpt.

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

12.10 posted this. When they did away with the Alternative installer they said they would add RAID to the desktop, but now it is not even mentioned in the newer release notes.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer)

Fantastic!  Thank you for the links.  I'll read some more and go from there.

I'll post what my next steps turn out to be.

Regards,
Don

---

