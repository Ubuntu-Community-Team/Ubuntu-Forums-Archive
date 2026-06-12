---
title: "ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Dropping to a shell on an HP desk"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by Ivan_Beccaro on 2014-12-08
I installed ubuntu 14.04 LTS x64 Destop on my HP on the second internal drive /dev/sdb2, using /dev/sdb1 as swap space.
I worked till two days ago when i rebooted the first time afer the last update.

Now when booting, after selecting the boot partition from GRUB screen, it hangs for a while, and finally it drops to a shell, giving me the following messages

```
[FONT=Ubuntu Mono]ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Dropping to a shell! [/FONT]BusyBox v.1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)  [FONT=Ubuntu Mono]Enter 'help' for list of built-in commands [/FONT]
```

I tried a clean install from an usb stick on /dev/sda2 but booting it i got the same message. 

I booted from an usb stick and both /dev/sda2 and /dev/sdb2 are there with the file systems appearing to work perfectly (i even repaired them with gparted)

found two procedures to solve the issue on askubuntu at the following link
[http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell](http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell)

I tried both on both partitions but with no result, it keeps dropping to the shell and don't boot.

booting from /dev/sda3 (the original win7 recovery partition) worked fine (i never meant restore windows do not worry guys ;) )

any suggestion to solve this issue and restoring my original installation on /dev/sdb2 is welcomed, i need to restore it asap since i have ongoing work saved on it.
I have my SVN on my small server but preparing an alternative workstation i would take too much work and time, and this is the best performing machine i have available, so i would get back to use it with ubuntu 14.04 LTS

thanks in advance for the attention, waiting eagerly for your support

---

### Post by Ivan_Beccaro on 2014-12-08
[COLOR=#000000]I installed ubuntu 14.04 LTS x64 Destop on my HP on the second internal drive /dev/sdb2, using /dev/sdb1 as swap space.[/COLOR]
[COLOR=#000000]I worked till two days ago when i rebooted the first time afer the last update.[/COLOR]

[COLOR=#000000]Now when booting, after selecting the boot partition from GRUB screen, it hangs for a while, and finally it drops to a shell, giving me the following messages[/COLOR]

[COLOR=#000000]Code:
[FONT=Ubuntu Mono]ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Dropping to a shell! [/FONT]BusyBox v.1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)  [FONT=Ubuntu Mono]Enter 'help' for list of built-in commands [/FONT][/COLOR]
[COLOR=#000000]I tried a clean install from an usb stick on /dev/sda2 but booting it i got the same message. [/COLOR]

[COLOR=#000000]I booted from an usb stick and both /dev/sda2 and /dev/sdb2 are there with the file systems appearing to work perfectly (i even repaired them with gparted)[/COLOR]

[COLOR=#000000]found two procedures to solve the issue on askubuntu at the following link[/COLOR]
[http://askubuntu.com/questions/51621...ing-to-a-shell]("http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell")

[COLOR=#000000]I tried both on both partitions but with no result, it keeps dropping to the shell and don't boot.[/COLOR]

[COLOR=#000000]booting from /dev/sda3 (the original win7 recovery partition) worked fine (i never meant restore windows do not worry guys [/COLOR]:wink:[COLOR=#000000] )[/COLOR]

[COLOR=#000000]any suggestion to solve this issue and restoring my original installation on /dev/sdb2 is welcomed, i need to restore it asap since i have ongoing work saved on it.[/COLOR]
[COLOR=#000000]I have my SVN on my small server but preparing an alternative workstation i would take too much work and time, and this is the best performing machine i have available, so i would get back to use it with ubuntu 14.04 LTS[/COLOR]

[COLOR=#000000]thanks in advance for the attention, waiting eagerly for your support[/COLOR]

---

### Post by oldfred on 2014-12-08
Does waiting a few seconds and then pressing enter does it boot?

Some have suggested adding a boot delay parameter to grub. Or does drive in caddy not come up to speed as fast as main drive?

Is grub installed to MBR of same drive as install and are you booting from that?
Or is second drive a caddy that you cannot boot from? Some systems seem to restrict that.

What setting is hard drive(s) set for in BIOS. Usually AHCI is best, sometimes compatibility works. But not IDE nor RAID.

When you chrooted into system, did you do a full un-install/reinstall of grub and update kernel?

Someone post this which was from an upgrade, but if initramfs not updated correctly for some reason could be the same issue?
>  "If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."




Post link to summary report, but I do not expect to see anything unusual. Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nerdtron on 2014-12-08
what is the contents of your /etc/fstab? and what is the output of "sudo blkid". The UUID of the disks in the fstab should be the same on the output of blkid.

---

### Post by oldfred on 2014-12-08
Two threads merged, Please do not post two threads on same topic.
We all are volunteers and need to know what has already been suggested to avoid duplication or wasted effort.

---

### Post by Ivan_Beccaro on 2014-12-08
1) no it does not boot by pressing enter it still gives the (initramfs) prompt
2) boot intances of ubuntu on the main and on the secondary drive give the same issue
3) GRUB is installed on MBR of /dev/sda, and i have two separate ubuntu instances on /dev/sda2 and /dev/sdb2 the original installation i use to work with it was the one on /dev/sdb2, the one on /dev/sda2 is a clean installation without downloading updates during installation process performed from an usb stick yesterday. Tring booting from both of the partitions it drops to the shell with an alert (didn't check the uuid of the drive in both)
4) the controller was set to RAID, setting the controller to AHCI still does not work

trying to operate something with your suggestion hold on,

---

### Post by Ivan_Beccaro on 2014-12-08
a full reinstall of grub did the trick ty for the suggestion oldfred:p

and thanks to all who replied

---

### Post by chris348 on 2015-02-11
Hello,

I'm new to the forum and really need some help. I've been following the instructions in this thread and askubuntu.com to resolve a similar problem after performing a release upgrade.

I attempted to upgrade my server's OS from Ubuntu 12.04 LTS to 14.04 LTS by executing the following command *sudo do-release-upgrade*. After completing the update and restarting the server I'm getting the same error as the original author of this thread. I carefully followed the steps that resolved the problem, but I needed to modify them slightly since my /boot directory isn't mounted on the same partition as my / directory. The altered commands I performed were as follows:

sudo mount /dev/sda2 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub
rebootUnfortunately this didn't work.

I then used boot-repair but this didn't work for me either. The URL to the boot-repair output is provided below:
[http://paste.ubuntu.com/10147702/](http://paste.ubuntu.com/10147702/)

I would be very grateful for any assistance that could be provided since I don't want to format and re-install the OS.

Thank you

---

### Post by oldfred on 2015-02-11
@chris348
Does it boot with older kernel? Or with recovery mode and enter after error and wait?

I do not think Boot-Repair will work for you. It only optionally mounts /boot, but since you have just about every other system folder as a separate partition, you may have to mount some or all of them when you do updates.
I might try the same chroot, but include all your other system partitions in mount like you did with /boot. I do not know for sure which other ones are required when updating, probably not /backup and /home.

Some older BIOS required boot files to be at beginning of drive. That is why most installs make first partition /boot or have / (root) as a smaller partition 10 to 25GB at beginning of drive.

Not sure now if dpkg will list older kernels after upgrade. But you should regularly houseclean older kernels. I use synaptic, but now after upgrade old kernels may not be shown and require manual delete. Best to have housecleaned most before upgrade. Do you have any ppa's enabled, as sometimes they do not update and then cause entire update to stall.

 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by chris348 on 2015-02-11
@oldfred
Thanks for replying so quickly. Yes I have my file system quite carved up (probably unnecessarily) but my file system layout came from an old school methodology. :)  

> [COLOR=#000000]Does it boot with older kernel? Or with recovery mode and enter after error and wait?[/COLOR]

I tried booting using recovery mode and the last kernel prior to performing the upgrade and it didn't boot. I haven't tried using any of the older kernels, but I would do so and provide you with and update.

> [COLOR=#000000]I might try the same chroot, but include all your other system partitions in mount like you did with /boot. I do not know for sure which other ones are required when updating, probably not /backup and /home.[/COLOR]

I will try it again mounting the other system partitions as you suggested. I will also look at the suggested links to try to clean up some space before proceeding with the repair.

> [COLOR=#000000]Do you have any ppa's enabled, as sometimes they do not update and then cause entire update to stall[/COLOR]
I don't think any ppa's were installed prior to the upgrade. I did install a ppa source during troubleshooting to install boot-repair but this was in the live CD environment. I really can't say for sure if any ppa's were installed.

I read about uninstalling and re-installing GRUB. I didn't try this because I was afraid I would only complicate things further or make matters worse. Is this something you recommend I try?

---

### Post by oldfred on 2015-02-11
The full uninstall/reinstall usually works, but that is with Desktops or those that only have /boot as a separate partition. While chrooted with all system partitions mounted you should be able to run it. But not sure if that is the only issue.

---

### Post by chris348 on 2015-02-12
@oldfred

I followed your first recommendation to boot using one of the older kernels and I'm happy to report that the server booted with 3.5.0-51 kernel! After the server came up I ran aptitude to see if any updates were required and I got the following message:
> [1(1)/....] Suggest 5 removals

I typed 'e' to examine and I got the following message shown in the attached image. I'm not sure if I should remove the packages. What do recommend?

Even though the server is running I don't consider myself out of the woods as yet since ideally I would like the server to use the current kernel. Any advice how I should proceed?

Regards,
Christian

---

### Post by oldfred on 2015-02-12
Sounds like something with new kernel did not fully get updated. But at this point not sure what is best option to fully update.

The 3.5.xx kernel is 12.10 unless you have 12.04 with HWE Hardware Enablement Stack, but not the newest, so repository is closed and updates not really possible. There may be a way to reconfigure to legacy repository, but upgrade to one of the LTS is really required.

---

### Post by chris348 on 2015-02-12
@oldfred I'm very grateful for your advice to resolve the issue with my server. At least now I could perform a back up of my data and do a clean install. Thanks!! :p

Cheers,
Chris

---

### Post by oldfred on 2017-04-17
Some other threads with same issue. 
Does not seem to be one easy solution.

 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
Also check that drive is hd0 and grub in same drive.
ALERT! /dev/disk/by_uuid, then missing keyboard driver, chroot install new kernel
[http://ubuntuforums.org/showthread.php?t=2245053](http://ubuntuforums.org/showthread.php?t=2245053)
[http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell](http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell) 
    SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=2255888](http://ubuntuforums.org/showthread.php?t=2255888)
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the “apt-get upgrade” does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs –u -k command. Then run sudo dpkg –reconfigure. That should clear the upgrade flags and fix any broken packages."

---

