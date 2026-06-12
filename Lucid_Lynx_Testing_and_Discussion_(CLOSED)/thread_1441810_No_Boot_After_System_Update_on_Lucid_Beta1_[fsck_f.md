---
title: "No Boot After System Update on Lucid Beta1 [fsck from util-linux-ng 2.17.2]"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zeroseven0183 on 2010-03-29
Now this is a little bit frustrating for me because I really need to use my computer. I was able to access it earlier but after updating and a reboot, it's stuck in the bootsplash. When I try to go to Recovery Mode, the error message says:

> 
fsck from util-linux-ng 2.17.2
udevd[321]: can not read '/etc/udev/rules.d/z80_user.rules'

/dev/sda1: clean, 153777/2342912 files 4810291/9357824 blocksI'm using Lucid Beta1 but am running a LiveCD now. I checked the directory and found out that z80_user.rules does not contain anything.

If I can remember, the last thing I installed is VirtualBox and setup a Jolicloud-Pre Beta VM.

Another issue has been reported about this, a bug report, can be found at [https://bugs.launchpad.net/ubuntu/+bug/549751](https://bugs.launchpad.net/ubuntu/+bug/549751)

---

### Post by bwallum on 2010-03-29
I've lost Lucid on upgrade this morning to -18 kernel. Hangs indefinitely on OS splash.

EDIT
Fixed on further updates.

---

### Post by dino99 on 2010-03-29
if you have a dual boot, you can follow this thread:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

change karmic by lucid, then you view .xsession-errors & /var/log, update & upgrade ....

---

### Post by zeroseven0183 on 2010-03-29
Unfortunately, I don't dual boot. I only use Ubuntu.

---

### Post by sports fan Matt on 2010-03-29
I reinstalled .16 myself.  Seems like .18 has a bug.

---

### Post by ranch hand on 2010-03-29
> **zeroseven0183 said:**
> Unfortunately, I don't dual boot. I only use Ubuntu.
I do not only use Ubuntu anymore but my first dual boot setup was Hardy/Hardy.

If you have room on your drive I would install 9.10.  If you, as you should, are installed on 2 partitions, you can use the same /home partition (just make sure to use a different user name for each OS).

---

### Post by kansasnoob on 2010-03-29
> **this is a little bit frustrating for me because I really need to use my computer.**

That is exactly why the release notes say:

> **Note: This is a beta release. Do not install it on production machines. The final stable version will be released on April 29, 2010.**

[http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)

Even the top of this forum page:

> **Ubuntu Lucid Lynx is in development, use only for testing purposes!!!**

I always run testing releases in a multi-boot with at least one other "production" OS just because of expected breakage. Right now my stable OS of choice is Jaunty.

---

### Post by _h_ on 2010-03-29
> **bwallum said:**
> I've lost Lucid on upgrade this morning to -18 kernel. Hangs indefinitely on OS splash.

> **sox fan Matt said:**
> I reinstalled .16 myself.  Seems like .18 has a bug.


-18 kernel is working perfectly for me, no issues or problems whatsoever.

---

### Post by sdowney717 on 2010-03-29
sounds like a gamble to see if your system dies when upgrading to -18 kernel.
Cant you just boot the 17 kernel available from the grub menu?

> scott@scott-desktop:~$ uname -r
2.6.32-17-generic

currently running 17. If I wait long enough 19 will be out, then 20. etc...

---

### Post by sdowney717 on 2010-03-29
We should start a poll to see how many have boot problem with -18 kernel or a poll to see how many will not want to upgrade a kernel after reading someone had a problem using it. This would give some sense of insurance that it wont mess up your system to go ahead and do the upgrade or not.

How do you do a poll anyhow?

---

### Post by garok89 on 2010-03-29
i did have this problem....
runnin ```
e2fsck -p /dev/sdaX
``` from a liveUSB on each partition fixed it for me

---

### Post by ranch hand on 2010-03-29
I have no trouble with the -18 kernel.  If anything, it seems a little more stable.

---

### Post by Zed on 2010-03-29
Last night, I installed from the Beta1 CD and manually configured an ext2 /boot partition, and LVM over an encrypted partition with one logical volume for swap, and another for /. After installation, it rebooted fine. I did an update, upgrade, dist-upgrade, and rebooted. I don't even get the bootsplash, just a blank screen. Probably the same issue as this one.

---

### Post by sports fan Matt on 2010-03-29
I can confirm no issues with the .18 kernel, it just took me awhile to get around to checking it.

---

### Post by zeroseven0183 on 2010-03-29
I'm not sure if this is a conflict with Plymouth, the kernel and my installation of VirtualBox. Before that happens, I noticed that my external USB drive is not automatically detected.

---

### Post by solitaire on 2010-03-29
I've got the same error.
it's on both 17 and 18 kernels. (Both after running apt-get update / upgrade)

I'm currently running on Live CD...

---

### Post by solitaire on 2010-03-29
*update*
I managed to chroot into my install using a LiveCD and ran ```
sudo apt-get update && sudo apt-get upgrade
```

Rebooted and that fixed the problem.

---

### Post by Arla on 2010-03-29
> **solitaire said:**
> *update*
I managed to chroot into my install using a LiveCD and ran ```
sudo apt-get update && sudo apt-get upgrade
```

Rebooted and that fixed the problem.

Darn, tried that (after figuring out how to use chroot) and no dice, didn't update/upgrade anything.

---

### Post by zeroseven0183 on 2010-03-30
> **kansasnoob said:**
> That is exactly why the release notes say:

[http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)

Even the top of this forum page:

I always run testing releases in a multi-boot with at least one other "production" OS just because of expected breakage. Right now my stable OS of choice is Jaunty.

Yeah, my bad. So any suggested solutions?

---

### Post by solitaire on 2010-03-30
Only thing to do, at the moment, is to use chroot from a live CD to update your install of Lucid.
it should hopefully be corrected by now.

follow the steps in this post to chroot into your install using LiveCD:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
then run and update..

---

### Post by Arla on 2010-03-30
> **solitaire said:**
> Only thing to do, at the moment, is to use chroot from a live CD to update your install of Lucid.
it should hopefully be corrected by now.

follow the steps in this post to chroot into your install using LiveCD:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
then run and update..

Thanks for the link, very useful, unfortunately it doesn't solve my problem, in fact updating this morning just made it worse, now running in recovery mode I get to "Begin: Running /scripts/init-bottom..." then the Done message, and then that's it, no more messages about mountall, but I'm not sure if it even gets to that point (if I recall mountall came after the scripts) guess it's going to be time to reinstall soon.

---

### Post by Brandioch.Conner on 2010-03-30
> **Arla said:**
> ... now running in recovery mode I get to "Begin: Running /scripts/init-bottom..." then the Done message, and then that's it ...

This is exactly what is happening on my machine which I upgraded from 9.10. I haven't been able to find a bug report with those characteristics yet. Does anyone know if there is one?

---

### Post by mart1n on 2010-03-31
I have the same problem on a DELL D600. After updating to kernel .18 the boot process is halted after grub. I end up in initramfs with the remark, that the root partition is missing "ALERT! /dev/disk/by-uuid/afxxxxxx does not exist. Dropping to a shell!" is the message. the UUID is correct, but the disk is just not mounted. 
Selecting the .16 kernel allows the system to boot, although slow and with new error messages which I did not have before (may be some bad sectors, old LT).

---

### Post by konare on 2010-03-31
> **Arla said:**
> Thanks for the link, very useful, unfortunately it doesn't solve my problem, in fact updating this morning just made it worse, now running in recovery mode I get to "Begin: Running /scripts/init-bottom..." then the Done message, and then that's it, no more messages about mountall, but I'm not sure if it even gets to that point (if I recall mountall came after the scripts) guess it's going to be time to reinstall soon.

Same here after updating and the running of fsck.

---

### Post by konare on 2010-03-31
Also had the Begin: Running /scripts/init-bottom message. When I looked at /etc/init (when looking at the lucid files from my dual boot 9.10 installation) I noticed that there were lots of empty files. Among them all files with mount*.conf, and gdm.conf.

Recreated those files with sudo apt-get install --reinstall gdm mountall. Am able to boot again, though I probably have to reinstall some more as my panels are gone.

---

### Post by Brandioch.Conner on 2010-03-31
> **konare said:**
> Also had the Begin: Running /scripts/init-bottom message. When I looked at /etc/init (when looking at the lucid files from my dual boot 9.10 installation) I noticed that there were lots of empty files. Among them all files with mount*.conf, and gdm.conf.

Recreated those files with sudo apt-get install --reinstall gdm mountall. Am able to boot again, though I probably have to reinstall some more as my panels are gone.

Sounds great. I'll try that tonight.

I'll have to boot the live CD, though.
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by Yahoé on 2010-03-31
Bonjour,


 Updated my Lucid Beta @ 05:00 am UTC, over 100 updates, rebooted.


  Since GDM loops, and I cannot go into  recovery mode.


When trying to go  into recovery mode, I get fsck from util-linux-ng 2.1.7.2


 So I'm totally stuck


Regards


AO

---

### Post by WereVince on 2010-04-01
I had the same problem here on my dell m1330 64bit. I tried to chroot from the livecd, but couldn't find what to reinstall to fix the problem. I finally reinstalled lucid from the beta1 CD and didn't update since. I'll wait until this problem is fixed. Did anybody identify what needed to be reinstalled to repair?
V

---

### Post by Brandioch.Conner on 2010-04-01
> **Brandioch.Conner said:**
> Sounds great. I'll try that tonight.

No luck. It still gave me the exact same:

Begin: Running /scripts/init-bottom
Done

So I pulled that drive and did a clean install of 10.04 beta, set it to nomodeset in grub and that seems to be working. So I know it isn't the hardware that is at fault.

---

### Post by Arla on 2010-04-01
My update (just for refence) I figured I'd done something wrong with the failed updates, so just reinstalled from CD, worked fine, have updated still works fine, so not sure what caused my issue. chroot'ing into the machine seemed to not work (while I could chroot in, could update everything, I still couldn't boot) so clean install seemed the only way to go.

---

### Post by yvesg on 2010-04-01
After upgrade from hardy to lucid beta1, I can no longer boot:

1) with 2.6.32-18-generic stops after "Starting up ..."
2) with the same kernel in recovery mode, stops after
"Begin: Running /scripts/init-bottom
Done"
[4.308717] Adding 9277528k swap ...
[4.973971] EXT3 FS on sda2, internal journal"
3) with 2.6.32-17-generic, it also stops after "Starting up ..."
4) with the same kernel in recovery mode, this is similar to point 2).

I can boot with kernel 2.6.31-10-rt but only tty works, gdm allows me to connect but I get a dark grey screen and nothing more.

After booting with kernel 2.6.31-10-rt in recovery mode I am now able to open a normal gnome session, except that the screen resolution is only 640x480. I have nvidia but I cannot load proprietary pilots. Let me continue investigating.

---

### Post by schmolch on 2010-04-01
None of these "fixes" work for me.
I made a fresh install from the beta1 livecd.
After the update no boot, no grub menu.
I chrooted, updated (nothing to update) and edited grub conf to point to -16.
It still does not boot nor do i get the grub menu.

---

### Post by Irihapeti on 2010-04-01
Some of these are sounding like bug 499399. If any of you think they are, please add a comment to the bug report.

---

### Post by zeroseven0183 on 2010-04-05
> **Irihapeti said:**
> Some of these are sounding like bug 499399. If any of you think they are, please add a comment to the bug report.

and [bug #549751]("https://bugs.launchpad.net/ubuntu/+bug/549751")

---

### Post by Cillean on 2010-04-05
@ yvesg:

I had quite the same problem - booting with the generic kernel ended in the message you quoted, but there was no problem with the rt kernel (except that the proprietary nvidia kernel module was not included in that kernel so I had to reconfigure the X server). I've got no idea why the rt kernel is not affected by that problem - however, I could solve the issue by having a look at the /etc/fstab. There I spotted two problems:

[LIST=1]
[*]One line referenced /dev/sda4, which is an extended partition on my drive, and tried to mount it as ntfs. The uuid did not exist. I changed it to /dev/sda3 which is the partition I need. Not sure why that line was there, neither do I know whether it was like that with Karmic...
[*]There was this line at the end of the file: ```
none        /proc/bus/usb    usbfs    auto,devmode=0666    0    0
``` I remember adding that line in a previous version because there had been some problem with usb automount. I removed that line and now it's booting fine.
[/LIST]
 
So maybe you should just have a look at your fstab and see if there's anything strange in there ;)

---

### Post by soro2005 on 2010-04-09
> **Cillean said:**
> @ yvesg:

[*]There was this line at the end of the file: ```
none        /proc/bus/usb    usbfs    auto,devmode=0666    0    0
``` I remember adding that line in a previous version because there had been some problem with usb automount. I removed that line and now it's booting fine.


Who would've thought! Thanks a lot, was about to despair.

---

### Post by jac_tict on 2010-04-10
Thank you Cillean! Finally get my box working!

---

### Post by jac_tict on 2010-04-11
It's important to make a workaround in startup scripts or in lucid upgrading steps.
Anyone who have VirtualBox installed (and use USB attached devices on virtual machines) has that line in fstab.

---

### Post by whatever on 2010-04-12
> **jac_tict said:**
> It's important to make a workaround in startup scripts or in lucid upgrading steps.
Anyone who have VirtualBox installed (and use USB attached devices on virtual machines) has that line in fstab.

Yes, fstab should be automatically checked during the update process and any "usbfs"-lines should be commented out.

I updated from Karmic today and stumbled across the same problem. I chrooted into the System from the LiveCD and tried a LOT of things until i realised this small line caused the whole boot process to fail :(

---

### Post by neokod on 2010-04-24
I have the same problem here.
After removing the line, this boot fine, but how I can uses USB in VirtualBox now ?

Thanks for your help !

---

