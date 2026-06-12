---
title: "&quot;No Common CD-ROM drive was detected&quot; with 9.10 alternate installer"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by vodsonic on 2010-02-17
I'm trying to install Ubuntu 9.10 on my Thinkpad X60, using the alternate installer on a CD in a USB-connected PATA CD drive. Early on in the install process, the installer claims that it's can't find a CD-ROM drive, even though the installer is currently running from the CD-ROM drive. This has apparently been a [[COLOR="Red"]known bug for about two years now[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614), and affects a wide spectrum of hardware platforms. Various [[COLOR="Red"]workarounds[/COLOR]](http://ubuntuforums.org/showthread.php?t=964904) [[COLOR="Red"]suggested[/COLOR]](http://ubuntuforums.org/showthread.php?t=1180234) on these fora did not work for me.

I had been using ubuntu on my Thinkpad X40 since Ubuntu 7.04, using the alternate install CD both times I installed it. I also had the docking station/UltraBase, which contained a CD-ROM drive that I used during the installs on the X40. It worked without a hitch.

I don't have an ultrabase for my X60, so have been using an external USB CD-ROM drive. This is old technology - no rocket science involved here. The installer complains that it can't find a CD-ROM drive: "No Common CD-ROM drive was detected." It then asks me to specify the device or supply a driver. 

Alt-F2 to a second console, press enter to activate.
$ ls -l /dev | more

Nothing comes up in the list that looks like a CD drive.

$ modprobe ide-scsi

Claims it can't find the module.

I followed the instructions [[COLOR="Red"]here[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614/comments/8), found the drivers on a working system, and put them on a thumbdrive. However, when I mount it:

$ mkdir /tmp/drive
$ mount /dev/sdc1 /tmp/drive

Mount fails due to an "invalid argument," with two different USB drives that work just fine on other systems.

Unfortunately, I am not an uber-hacker, and can't fix a problem like this with both hands tied behind my back. If mount doesn't work, I'm really up a creek.

I then attached a SATA CD-ROM drive with a USB interface. This does start booting into the installer, but causes spontaneous reboots within the first 5 minutes of the process, and usually much sooner than that.

I used unetbootin to create a bootable USB flash drive based on the Ubuntu 9.10 alternate installer iso. I can boot to it, and get a long way through the install process, but grub fails to write to any device, and selecting "Finish install" also "fails." There's no way out at that point besides aborting the install.

After years of doing this, and getting the install down to a science on my X40, this seeming dead end is frustrating.

Where to go from here? Until I get this fixed, I've installed Xubuntu 9.10 on the X60 using the regular live CD, and not utilizing some of the options offered by the alternate install disc. I'm going to await the next major release of Ubuntu in April, since I had planned to do a clean install of that anyway. If the bug has been fixed in the new Ubuntu, I may not need to battle this issue any longer.

However, if it persists, what is the simplest way to skirt around this issue? Is there a different type of external USB CD-ROM drive that might not be so problematic, like a better SATA drive?

I don't know how else to put the alternate installer on a flash drive. The way I did it with unetbootin is not ideal, since although I used the alternate installer iso as a basis, it still goes and tries to download all the packages. Ideally I need something that will allow me to complete the install offline, which the unetbootin USB drive won't do - it aborts when it can't find a download mirror.

Any suggestions? On the one hand, I could wait for the LTS release of Ubuntu in April, and try a USB CD-ROM drive with a SATA interface. Or, I could start trying to figure out why modprobe and mount don't work with my existing setup. Which approach is more likely to get me where I need to go without me reinventing the wheel along the way?

---

