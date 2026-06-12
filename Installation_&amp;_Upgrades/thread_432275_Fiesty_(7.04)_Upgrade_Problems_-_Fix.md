---
title: "Fiesty (7.04) Upgrade Problems - Fix"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by finalzero on 2007-05-03
Hi,

If like me you have experienced issues upgrading your existing 6.10 distribution or attempted to do a clean install using Feisty 7.04 distribution and experienced strange lock ups during the upgrade or a dead system after a clean install then I can probably help.

I had a working 6.10 distro running on my x86 system (Dual P4 Xeon), and like others I received a message advising me the 7.04 upgrade was available. 

So I thought why not, lets do it, I was pretty confident my system was running sweet (follow this guide for a complete run down of how to configure your system:  [http://ubuntuguide.org/wiki/Ubuntu:Edgy)](http://ubuntuguide.org/wiki/Ubuntu:Edgy)).

The upgrade process started off okay and began downloading the various update files so I carried on surfing the web.  Once the files were complete the upgrade process began and the various files I had downloaded were being installed.  Everything was looking good up until it went to install the kernel image, at which point it completely hung and locked up my system.

Now when I tried to reboot, I had a bricked system i.e. it would not boot into Linux, thankfully I have a dual boot so I fired up Windoze XP and downloaded 7.04, burning it to CD so I could do a clean install.

The clean install seemed to work fine but I have no idea what they have done to the partition manager, its a bloody nightmare to use now, the previous one was alot easier to use and partially guided you through the process of setting up and configuring any existing NTFS partitions and removable devices.  The new version is much more clumsy and I can see new users easily wiping their HDD clean if they have a dual boot system.

After much cursing I got my linux partitions configured as I wanted and I managed to proceed with the installation - all looked well and it seemed to complete without any hickups however when I went to reboot, I got nothing.

All I could see was the grub menu however selecting any option simply resulted in the message "no image found" or "no disk present" - bloody great. Even entering manual grub commands had no effect, it couldn't see my drives!

Solution:

Now here is how I got it working.  I installed a clean copy of Ubuntu 6.10, once installed I promptly rebooted and made sure everything was fine, yep grub had found my Windoze partition and was happy to boot into Ubuntu again.

To avoid any issues I ignored any update messages and waited for the upgrade option to appear (or as per the official upgrade method, in a shell window type  **gksu "update-manager -c"** ), lo and behold about 5 minutes later I was offered the option to upgrade to 7.04 which I accepted.  This time round it worked, the upgrade process completed and I was able to boot into Feisty 7.04.

Very annoying and a long haul process to get it installed but seemed to work fine for me and quite a few others so I thought I would share the insight with you.

I believe the original issue was with 6.10 i.e. the way it had been configured and the various apps that were installed, one or more of these must have caused an issue - hence a completely stock build of 6.10 worked fine.

Incidentally I had Beryl installed on 6.10 so this could have been a contributing factor.  However why the clean install from the Feisty 7.04 failed for me and others is a mystery. All I can think is that its something to do with the way the drives and partitions are now presented in 7.04.

Thankfully everything works now and I am very impressed with 7.04 overall, I had already seen most of its internals when I recently built a Debian 4.0 based system but the new Ubuntu just feels a bit more polished.  Beryl installed first time and worked like a treat (provided your using a nVidia card) and I have had no issues with Gnome now so thats a relief (I love the clean unobtrusive nature of Gnome over KDE's in your face look).

Now I just hope linux hardware support matures and we can start getting the basic hardware things working like WiFi !

*References: Once you have 7.04 installed I recommend following this guide to complete your setup: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Adios,

Fz

---

### Post by DavidTangye on 2007-05-03
Thanks for the info.
> All I can think is that its something to do with the way the drives and partitions are now presented in 7.04
Perhaps its the way the drives and partitions were presented in Edgy. On this standard vanilla Ubuntu machine /etc/fstab is as follows, and gparted has a warning icon next to the root partition saying it cant find its mountpoint, and the update-manager will not upgrade, complaining that the /boot partition if too small when in fact it does not exist.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=b7bce030-9b6a-43a4-9eb1-fbca1bdde76a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=e9abaaf0-de55-4552-a625-e5d05329b077 /home ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=081727d9-f4da-4060-b837-f7ec7dc17950 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=9877-489A /mnt/winfat vfat rw 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=1A6409D86409B811 /mnt/windows ntfs ro,users,umask=0000 0 0

---

### Post by finalzero on 2007-05-03
Yep I found that as well - all I can think is its bugged and needs some attention.  As people will have noticed fstab is different now as are other things so the old conventions have to be thrown out of the window.

Using the method I have outlined seems to work, I think its because your using the 6.10 partition manager to setup your drive and then doing the upgrade to 7.04 from that - seems to preserve the drive partitions and works fine.

What I have noticed is if you do any updates in 6.10 and then try the upgrade it fails at about 75% of the way through the upgrade.

---

### Post by finalzero on 2007-05-04
bump for those that are stuck with install/upgrade issues

---

### Post by DavidTangye on 2007-05-14
I dont suppose you would now know whether the /etc/fstab was in the changed format, similar to how I showed it in the previous message, by your initial install of Edgy?

I have never installed Beryl, so you can discount that as causing the problem.

Whatever the reason its not an acceptable solution to me to freshly reinstall Edgy then upgrade to Feisty just to get my current Edgy to Feisty.

---

