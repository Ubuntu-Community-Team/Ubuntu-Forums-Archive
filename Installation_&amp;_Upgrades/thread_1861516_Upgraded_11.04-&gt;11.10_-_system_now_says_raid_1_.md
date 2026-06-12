---
title: "Upgraded 11.04-&gt;11.10 - system now says raid 1 array degraded"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by billsmithem on 2011-10-15
Upgraded 11.04 amd64 to 11.10 amd64. No errors during upgrade.

After upgrade completed, the now system hangs just before login screen. Booting in recovery mode displays errors that the raid 1 array is having a problem and offers to allow it to be started in degraded mode. If it's started in degraded mode the system boots fine.

I cannot find anything wrong with the array. I can stop and restart the array with no errors whatsoever.

This was working perfectly before the upgrade. Anyone have a clue why it's failing at boot?

---

### Post by james@finnall.net on 2011-10-15
I have upgraded two machines so far to 11.10 from 11.04 with RAID-1 mirrored drives.  Without any problems.  Both were originally installed and configured with 10.04 LTS from the alternate install CD.  On-line upgrade is the only option I have found to upgrade that will work on RAID-1 mirrored systems.  

If your system has similar history then I would suspect a possible hard disk problem causing issues with the RAID.  Problem might not have been an issue before the upgrade until the GByte or so download was done and all the files started to be changed.  That causes a lot activity on the hard disk, way beyond normal operation.  The CLI interface tool is "mdadm" to process RAID devices.  You could try hot removing the second drive and then hot adding.  Monitor  /proc/mdstat for the reconstruction progress. 

Hope it helps to identify your problem.  Hardest part is always isolating the problem itself.  Fix is usually far simpler.

James

---

### Post by billsmithem on 2011-10-16
Similar upgrade history, except that raid array is data only. OS/swap/user partitions are all on another single device. The raid array was untouched by the upgrade, it just won't initialize correctly at boot since the upgrade.

According to /proc/mdstat there is nothing wrong with the array. The only issue is with bringing it up at boot.

---

### Post by james@finnall.net on 2011-10-16
You might want to look the file /etc/mdadm/mdadm.conf

The mdadm monitor process starts up very early in the boot process.  My system has a process ID of about 1200 in the process list.

---

### Post by gadnex on 2011-10-17
I have exactly the same problem as **billsmithem**.

I also have my operating system on a separate drive from the mdadm RAID5 array.

I will check /etc/mdadm/mdadm.conf this evening and see if that file may have been altered during the Ubuntu 11.10 upgrade process.

---

### Post by billsmithem on 2011-10-17
Yup, been through checking mdadm.conf, though I didn't expect there to be anything wrong there as the array works fine if I bring it up after the system is booted. 

Checked both drives smart data and nothing has changed. One has a single remapped bad sector that it lost 15 days after the drive was first brought online (2 years ago) and the other is perfect.

Finally gave up on it. I had enough extra storage space to copy all the data and I recreated the array from scratch. No problems recreating the array at all, but it still won't work, though the problem has changed slightly.

It used to be md0. I recreated md0. Now at boot the system starts up md127 and md0 dissapears. Yes, I've updated mdadm.conf for the new array. 

I have no idea where to go from here. I'm about ready to just do a complete re-install. Not such a big deal data-wise as everything but OS is on other drives, but a real PITA getting all the services set up again.

Anyone have any other options before I completely write off this upgrade?

---

### Post by james@finnall.net on 2011-10-17
You might want to check out the bug tracker and see if anything there applies to your problem.  If not, then post a new bug report.

I checked and saw a few new bugs but not close enough to the problem to determine if exact or not.  The package I was looking at was "dmraid" at the post below.

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bugs?field.status:list=NEW)

On the right side bar it offers more options to review even more bugs that have been reported.

On my systems, I have several RAID-1 mirrored partitions on two physical drives.  So far no problems with any of them.  They are all using SATA hard drives on the native SATA controller of the Intel motherboard.  I only mention this in case of driver support in the new 3.0.0 kernel for your hardware.

Good luck,
James

---

### Post by gadnex on 2011-10-17
I can confirm that I also checked the smart data of all my drives and all seems fine. I just used the graphical Disk Utility to check the RAID5 array and the individual drives.

When I power on my PC, it just freezes on a screen with the Ubuntu desktop background with absolutely no information or error messages at all. If I then press ctrl+atl+del on the keyboard, the machine restarts and this time I get the grub boot menu with the following options, although I do not have the exact text for the options:
[LIST]
[*]Restart normally
[*]Recovery Mode
[*]Boot previous Os version
[*]Memory test
[*]Another memory test
[/LIST]

I select the first option to restart normally and this time round I get a black screen which states that the RAID failed to start and asks if I want to start the RAID5 array in a degraded state. I say yes and Ubuntu then starts normally.

I then immediately check Disk utility, which states the RAID5 array is running normally and is not degraded.

I have 6 x 2Tb drives in single a RAID 5 array, so recreating the array is something I would like to avoid. 

I previously upgraded from Ubuntu 10.10 to 11.04 and that time everything went fine.

---

### Post by james@finnall.net on 2011-10-17
I found this remark in the comments on one of the dmraid bug reports to add

 "bootdegraded=true"  to the kernel boot options

Now I am not sure where you add this myself.   I am thinking maybe grub on the boot config of the kernel.  It is intended to get around an issue of incorrectly detecting RAID drive failures.  Maybe it could help here.

James

---

### Post by gadnex on 2011-10-17
I found the following article:
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

It states the following:
```
Boot from Degraded Disk
If the default HDD fails then RAID will ask you to boot from degraded disk. If your server is located in a remote area, the best practice may be to configure this to occur automatically. Since Ubuntu 8.10 there is a new feature to boot automatically if default RAID disk fail. Simply:

edit /etc/initramfs-tools/conf.d/mdadm
change "BOOT_DEGRADED=false" to "BOOT_DEGRADED=true"
NB:

Additionally, this can be specified on the kernel boot line with the bootdegraded=[true|false]
You also can use #dpkg-reconfigure mdadm rather than CLI!
```

This might solve the problem, but currently when I boot I do not get a message saying the array is degraded. It is just a blank screen with no indication of what is wrong. Only after second boot do I get the boot degraded array option.

Something must have changed between Ubuntu 11.04 and 11.10. I will try and see toningt if I can figure out what happens, but I am not an expert when it comes to Linux log files and fault finding.

---

### Post by gadnex on 2011-10-17
Sorry for the many replies to this thread, but I keep finding additional info that may be of value.

I found the following links, which may be related:
[http://ubuntuforums.org/showthread.php?t=1859856&page=2]("http://ubuntuforums.org/showthread.php?t=1859856&page=2")
[https://lists.ubuntu.com/archives/foundations-bugs/2011-August/016682.html]("https://lists.ubuntu.com/archives/foundations-bugs/2011-August/016682.html")

It seems that the hanging on the purple screen is not the caused by mdadm, but probably something else like a graphics driver issue.

This failure probably happens after the mdadm RAID array started successfully. When I then press ctrl+alt+del to reboot, the RAID array is then degraded by not shutting down the RAID array before the reboot. That is why the degraded RAID array is reported on the second boot attempt.

---

### Post by billsmithem on 2011-10-17
The "hanging on the purple" screen is itself a bug, as far as I'm concerned. What happens is the error comes up, something runs which give you the opportunity to boot the degraded array, which then times out and drops you into a recovery mode.

Of course, this behavior is totally useless unless you switch the system back out of the mode where it's hiding the boot sequence. It just looks like it's hung. The console is live. If you type "reboot" and hit enter it will restart.

Holding the left (might work with both) shift key down just as grub starts to run will give you the option of booting in recovery(??) mode and you can see the whole thing happening. I've looked at it so many times I'm able to judge where the system is in the boot sequence by looking at the HD activity light, and just hit "y" and return when it gets there before the timeout.

It would be nice to know where this new array (md127) that I didn't create is coming from. Looks like it's doing an mdadm --assemble by itself at boot and ignoring my definition in mdadm.conf.

As there is nothing at all wrong with the array, for now I've reconfigured the system to boot with the degraded array via the config file in initramfs-tools.

I'd still like to know what's going on here.

---

### Post by billsmithem on 2011-10-17
After configuring it to boot with degraded raid array, everything is working just fine. System come up, despite what the boot code says the raid array is functioning perfectly. I'm just going to run it like this.

I'm tired of messing with it. I have work to do.

I've not been terribly impressed with the last three Ubuntu releases. Each one has completely messed up at least one system when they were upgraded.

---

### Post by gadnex on 2011-10-18
I checked last night and my /etc/mdadm/mdadm.conf file was unchanged from the way I set it up with Ubuntu 11.04.

Weird thing is that last night the machine booted correctly and did not hang on the purple screen.

I hope my problem has been resolved, although I am not aware that I did anything that should make a difference.

---

### Post by Trebacz on 2011-10-18
Add my vote to similar people having the problem after upgrade. My setup uses two mirrored SATA data drives. Operating system is on another drive completely. I did have some upgrade issues (apparently nvidia-current driver related) from 11.04 to 11.10. My current drive situation is:
1) The system alerts me to the fact that my raid 1 array is borked. It asks me if I want to boot the array degraded. I don't answer, since I'm not sure of the ramifications. The system drops to a INITRAMFS prompt
2) If I CTRL-ALT-DEL from the INITRAMFS prompt the machine boots fine. The array seems to work fine.

---

### Post by annagel on 2011-10-21
I am having similar issues, I posted a separate [thread]("http://ubuntuforums.org/showthread.php?t=1866376") on the issue.  It looked like the boot degraded was going to fix it, but even that is failing sometimes saying it can't boot degraded.  Frankly I don't see why this has to stop my boot.  

Even if it was correctly detecting issues, if the system can't mount the arrays it is an issue but unless the system gets all the way up there is not a hell of a lot I can do about it.  I would just like a way to turn this option off all together and deal with a down array when it is real after boot.

---

### Post by gadnex on 2011-10-24
I read annagel's other thread and it says something about adding the following line that affect grub:

```
GRUB_GFXPAYLOAD_LINUX=text
```

I am not sure if this actually fixed the problem or not. I am not even sure what the setting does or in which file to add the line.

I got the idea that it changes the boot sequence to use a text based interface instead of a graphical user interface. I cannot think that this would solve the issue, but maybe it will help to identify exactly what the error is that cause the boot to get stuck on the purple screen.

---

### Post by dangriffin on 2011-10-24
I was having problems with my RAID 1 array which had previously worked fine on Natty/Lucid. There was nothing wrong with it, but on every boot either the dreaded 'purple screen of death' popped up or the busybox initramfs screen.

The /proc/mdstat that is dumped out on the 'degraded raid' screen appeared to show that one of my two drives had not been detected before the check on the raids health had been performed. It turns out that mdadm raid arrays are incrementally added to the system via udev rules that you can find in /lib/udev/rules.d/85-mdadm.rules. 

This is all well and good, as long as each of the udev rules for each of your drives in the array has fired before the check on the health of the array has occurred. If not all of the devices have come up in time then you'll get the degraded screen - a good old fashioned race condition. This occurs even if there is nothing wrong with any of your drives.

Checking through the initramfs scripts for ocelot/natty/lucid, I couldn't find anywhere where a 'sanity check' is taken to ensure that all members of the array have come up, other than the 'degraded array' screen. I can only assume in previous incarnations of ubuntu the structure of the scripts was such that the race condition didn't occur very much (I did have the odd bad boot where the array wouldn't come up).

I fixed this problem on my hardware by adding a 'udevadm settle' in the following file: 

/usr/share/initramfs-tools/scripts/mdadm-functions

In there, look for the following function:

```
degraded_arrays()
{
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}
```

and change it to:

```
degraded_arrays()
{
        udevadm settle
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}
```

then do a:

```
sudo update-initramfs -u
```

and reboot.

This line makes all current udev rules being processed complete before the health check is made on the array. By then the array should have had chance to correctly assemble.

Hope this helps.

---

### Post by gadnex on 2011-10-25
Thanks dangriffin for your assistance. Your explanation makes sense based on the experiences reported on this thread. 

I will definitely go and try you fix and report back here.

I do think however that this issue and solution should be reported to the Ubuntu team so that your fix may be fixed in a future patch or in Ubuntu 12.04. Does anyone know what the correct procedure is to do this? I would assume it has something to do with logging a bug.

---

### Post by annagel on 2011-10-25
This is great work, I rolled my system back to 11.04 for the time being so I am going to see if I can setup a vmware instance to reproduce the issue and test the solution.  I posted it to the bug which has been filed on this an another raid issue ([https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220)).  If it works this fix should fix the majority of the issues, the second part of the bug is the inability to boot if you have an array too far gone for assembly.  For example 1/3 of a raid 5 or even just an old raid 5 disk. both of which will make your system unbootable.

I am also thinking this check may never have even been run in 11.04, as neither the unbootable or missing drive problem appear there and it seems like the check code at least is unchanged.

---

### Post by gadnex on 2011-10-25
annagel, I think it is you that made the following comment on the bug report.

```
Like I said the effect would seem to be it is impossible to put a disc that has at some time in the past been a part of a RAID5 array into a system even if all you want to do is format it.
```

In the past I had a problem where 2 of my RAID 5 disks temporarily lost connection due to incorrect bios settings and the 2 disks were removed from the array. The following command helped me to add them back in the array.

```
mdadm --assemble --scan --force
```

The thing that makes the real difference is the --force parameter, but I am not sure if this is applicable to your issue.

---

### Post by annagel on 2011-10-25
That was me the issue is not assembling the raid latter though that works fine the problem is that the system won't boot period. Even doing something innocuous like trying to reuse an old disk that used o be part of a raid array will first trigger the check then if you tell it or have the option set it will try to boot degraded or if not drop to initramfs. The boot degraded fails because you only have one disc and the system drops into the initramfs shell.  Unless I am missing something there does not at the moment seem to be a way to boot 11.10 with a single raid5 disc attached to the system as a result.

---

### Post by Chadarius on 2011-10-26
I'm having this same exact problem. I'm install rolling back to 11.04 for the time being. 

What a pain in the rear! I hope this is something that gets put into the testing plan for future Ubuntu releases. RAID arrays are not to be messed with! :)

---

### Post by alpha-omega on 2011-10-27
Hello and sorry for my probably dumb question: How do you roll back Ubuntu 11.10 to 11.04?

I upgraded 11.04 to 11.10 with the result that I now have 1) a graphic problem and 2) a RAID problem, too.

@1)
After the upgrade and reboot I had no real graphics (i.e. not even the splash screen saying "Ubuntu" with the little blinking dots below), but instead black and white scrambled symbols. I removed my AMD/ ATI Radeon HD 4something und booted again with the Intel onboard GMA active. Thus, I got rid of the scramble and had a chance to read from the console what else was going on. Then I realized...

@2)
... that my system (or rather root [/]) was mounted read-only. Root (as well as swap and /home) is sitting in a logical volume (I use LVM on soft-RAID1). I then used the "rescue" function of the Ubuntu 11.10 system, but then did not exactly know how to proceed. I was asked whether I wanted to assemble my RAID1 array, I said "yes" and selected "automatically", and the 2 drives where correctly assembled. Then I was asked whether I wanted to work with a shell on the real root or rather with a (slacked down) shell run from RAM (do not exactly remember how this was phrased, but I hope you get the idea). The problem is that if I chose the shell on the real root, I cannot do much, because it is read-only. And of course fiddling with the RAID when working on it cannot really work, I understand. However, when I work with the slacked down shell, this shell does not even know commands like "fdisk". Where do I get this from, do I need it at all (besided "mdadm")?

Coming back to my initial question:
Should I try to roll back to 11.04? Is this possible at all without a backup (I have none, because I am still using my rather new Ubuntu 11.x for testing purposes), i.e. is there an in-built functionality to roll back? But still, I would need to correct the RAID issue, right? So what would be the purpose to just roll back?

So should I rather first try to fix the RAID problem (since updating the AMD/ ATI drivers will surely fix the graphics issue, this would be fine with me)? If "mdadm" is my friend to accompany me, how exactly do I fix the RAID problem? See above: Which other tools do I need? E.g. Ubuntu rescue remix, or would the Ubuntu "rescue" method from the CD/ stick work, too? But the shell did not have "fdisk" on board, remember?

I read a lot of stuff like "man mdadm", HowTos, FAQs etc., but I could not find some guidance how I repair the bad data on one of the drives (I hope that not both are affected - both Samsung Spinpoint F3 SATA drives, less than 6 months old).

Thanks for your kind help and hints!

PS:
I started Ubuntu once more, but now pressed SHIFT and then used the rescue mode and console, which seems to be completely different than the rescue mode of the Live CD. It was possible to check the RAID status with "mdadm". Interestingly, /dev/md0, md1 and md2 all appeared "clean", and there was nowehere a message that the RAID was degraded. Does "mdadm" display such a message if the RAID is degraded?
Then I entered "fdisk" which started to check the drives:```

...
EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
```Then the blinking cursor, so I believe that it is still checking (2x 1TB may take a while).

PS2:
After a night, still blinking cursor, so I did ctrl+x and rebooted. Now Ubuntu shows the splash screen again, then text (black/ white), with the last lines that the NX service was started, that's it, i.e. no Gnome. I can switch to another console (ctrl+alt+F1), but do not know how to proceed. Shall I put back my AMD/ ATI? Dmesg did not show any failures,  mdadm shows the RAID is clean, too.
When I nx (from a Macbook) into Ubuntu, I do get the Gnome graphics etc., so there is no problem in using it with the onboard Intel GMA after the RAID issue has been resolved. But the Ubuntu machine itself does not start into Gnome. I do not want to always nx or ssh into it, but would like to have back Gnome. What to do?

---

### Post by simeonzv on 2011-10-28
> **dangriffin said:**
> I was having problems with my RAID 1 array which had previously worked fine on Natty/Lucid. There was nothing wrong with it, but on every boot either the dreaded 'purple screen of death' popped up or the busybox initramfs screen.

The /proc/mdstat that is dumped out on the 'degraded raid' screen appeared to show that one of my two drives had not been detected before the check on the raids health had been performed. It turns out that mdadm raid arrays are incrementally added to the system via udev rules that you can find in /lib/udev/rules.d/85-mdadm.rules. 

This is all well and good, as long as each of the udev rules for each of your drives in the array has fired before the check on the health of the array has occurred. If not all of the devices have come up in time then you'll get the degraded screen - a good old fashioned race condition. This occurs even if there is nothing wrong with any of your drives.

Checking through the initramfs scripts for ocelot/natty/lucid, I couldn't find anywhere where a 'sanity check' is taken to ensure that all members of the array have come up, other than the 'degraded array' screen. I can only assume in previous incarnations of ubuntu the structure of the scripts was such that the race condition didn't occur very much (I did have the odd bad boot where the array wouldn't come up).

I fixed this problem on my hardware by adding a 'udevadm settle' in the following file: 

/usr/share/initramfs-tools/scripts/mdadm-functions

In there, look for the following function:

```
degraded_arrays()
{
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}
```

and change it to:

```
degraded_arrays()
{
        udevadm settle
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}
```

then do a:

```
sudo update-initramfs -u
```

and reboot.

This line makes all current udev rules being processed complete before the health check is made on the array. By then the array should have had chance to correctly assemble.

Hope this helps.

dangriffin: many thanks! this solution fixed the problem with incorrectly detected degraded RAID 0 for me.

---

### Post by gadnex on 2011-10-31
I also tried dangriffin's solution over the weekend and it seems to have resolved my issue as well.

Thanks very much for the help.

---

### Post by jf77 on 2011-11-09
Worked like a charm, many thanks :D

---

### Post by gadnex on 2011-11-09
Lets hope this fix makes it into Ubuntu 12.04 so that mdadm works correctly on a default install.

---

### Post by derjusti on 2012-01-01
Worked perfect, thanks!

---

### Post by Antoniya001 on 2012-01-01
THX for the solution Dangriffin
Same problem here (although Raid6 in my case)...
 
My systems still hangs on first boot but at least it will load the array correctly. Must be another problem that makes the system halt.
 
Arjan
 
Edit : It now works after also changing : 
 
pico /etc/initramfs-tools/conf.d/mdadm
change "BOOT_DEGRADED=false" to "BOOT_DEGRADED=true"
 
AND using following boot options :
pico /etc/fstab
/dev/md0 /mnt/Raid6 ext4 defaults,noatime,nobootwait 0 0
 
This is crazy though... Array is fine.
 
Edit: After reinstalling my VM host machine again, the everything the following happened :

Jan  4 00:05:05 IOSERV-HOST kernel: [ 1309.092530] md: kicking non-fresh sdh1 from array!
Jan  4 00:05:05 IOSERV-HOST kernel: [ 1309.092536] md: unbind<sdh1>
Jan  4 00:05:05 IOSERV-HOST kernel: [ 1309.108404] md: export_rdev(sdh1)
Jan  4 00:05:05 IOSERV-HOST kernel: [ 1309.108441] md: kicking non-fresh sdb1 from array!
Jan  4 00:05:05 IOSERV-HOST kernel: [ 1309.108448] md: unbind<sdb1>
Jan  4 00:05:05 IOSERV-HOST kernel: [ 1309.120015] md: export_rdev(sdb1)
 
Yikes !!!!    Curerently rebuilding 10TB Array (fingers crossed) ... first disk is done.. So happy to have ran Raid6 instead of Raid5

---

### Post by Marcelo Fernández on 2012-01-06
I had the same problem, was rebuilding the degraded RAID 1 almost on every reboot. Dangriffin's solution seems it will help here. Thanks a lot.

Dangriffin, I think you should consider file a bug report (with the attached patch)...

Regards

---

### Post by manugarg on 2012-01-13
Out of all the solutions for this problem in the wild out there, this is the only one that worked for me. Thank you very much!!!

This gives the most plausible explanation also.

> **dangriffin said:**
> I was having problems with my RAID 1 array which had previously worked fine on Natty/Lucid. There was nothing wrong with it, but on every boot either the dreaded 'purple screen of death' popped up or the busybox initramfs screen.

The /proc/mdstat that is dumped out on the 'degraded raid' screen appeared to show that one of my two drives had not been detected before the check on the raids health had been performed. It turns out that mdadm raid arrays are incrementally added to the system via udev rules that you can find in /lib/udev/rules.d/85-mdadm.rules. 

This is all well and good, as long as each of the udev rules for each of your drives in the array has fired before the check on the health of the array has occurred. If not all of the devices have come up in time then you'll get the degraded screen - a good old fashioned race condition. This occurs even if there is nothing wrong with any of your drives.

Checking through the initramfs scripts for ocelot/natty/lucid, I couldn't find anywhere where a 'sanity check' is taken to ensure that all members of the array have come up, other than the 'degraded array' screen. I can only assume in previous incarnations of ubuntu the structure of the scripts was such that the race condition didn't occur very much (I did have the odd bad boot where the array wouldn't come up).

I fixed this problem on my hardware by adding a 'udevadm settle' in the following file: 

/usr/share/initramfs-tools/scripts/mdadm-functions

In there, look for the following function:

```
degraded_arrays()
{
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}
```

and change it to:

```
degraded_arrays()
{
        udevadm settle
        mdadm --misc --scan --detail --test >/dev/null 2>&1
        return $((! $?))
}
```

then do a:

```
sudo update-initramfs -u
```

and reboot.

This line makes all current udev rules being processed complete before the health check is made on the array. By then the array should have had chance to correctly assemble.

Hope this helps.

---

### Post by KeithLM on 2012-01-22
I've been having trouble ever since I upgraded to 11.10 and finally found this thread.  Thanks a lot.  I would get occasional boots that would work, but it was less than half the time that it would work smoothly.  This looks like it should take care of my problem.

---

### Post by Kleenux on 2012-05-02
> **dangriffin said:**
> I was having problems with my RAID 1 array (...)
and change it to:

```
degraded_arrays()
{
        udevadm settle
```
Hope this helps.

It does! Thanks a lot dangriffin - I was struggling with this problem for several months!

---

### Post by dmorris68 on 2012-05-03
Just FYI, this issue still exists in 12.04.  Why???  :(

Fortunately dangriffin's fix still works, but I'd have hoped what seems to be a relatively simple timing issue couldn't be fixed in the next major release.

---

### Post by cg` on 2012-05-06
I've just done a fresh 12.04 install, using an existing 6x2tb raid5 array. Install and mdadm assemble all went fine, until reboot where I was getting the "degraded" error message on boot, even though the array was 100% fine.

Fortunately dangriffin's fix with the "udevadm settle" initramfs change is still applicable and worked great.. so thank you! :)

---

### Post by KeithLM on 2012-05-06
> **cg` said:**
> I've just done a fresh 12.04 install, using an existing 6x2tb raid5 array. Install and mdadm assemble all went fine, until reboot where I was getting the "degraded" error message on boot, even though the array was 100% fine.

Fortunately dangriffin's fix with the "udevadm settle" initramfs change is still applicable and worked great.. so thank you! :)

When I read your post in my email a moment ago I thought maybe I wrote it.  Except I have a 5x2TB raid 6 array.  But the exact same thing happened to me as soon as I updated from 11.10 to 12.04 and once I applied this fix again everything went back to normal.

---

### Post by Kleenux on 2012-05-13
> **dmorris68 said:**
> Just FYI, this issue still exists in 12.04.  Why???  :(.
That's an interesting question... especially since it affects also fresh installs, not only upgrades.
And the problem is particularly annoying, as in some cases Ubuntu waits for an action before to complete the boot.

Maybe the MD users are too few to be taken into account :-(

> **dmorris68 said:**
> Fortunately dangriffin's fix still works, but I'd have hoped what seems to be a relatively simple timing issue couldn't be fixed in the next major release.
To be honest, it took me several months to find a reliable fix [dangriffin's], and believe me I googled that a lot (and asked other forums).

So, as "simple"...  maybe the solution is simple as long as you know it :-) 
Dan deserves a medal!

---

### Post by KeithLM on 2012-05-13
Perhaps it's this [bug]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/539597") that needs to have this solution proposed to get it fixed.  I looked at the bug linked above by annagel and it appears that's a slightly different issue.

---

### Post by Kleenux on 2012-05-13
The "bug" (more of a discussion), you are referring to, underlines the confusion surrounding the  boot_degraded option [ being an "option" it may mislead some admins as, if set to yes, may bring about the shadowing of a hard disk problem ].

The actual bug identified by dangriffin shows that there is a race condition - not less - between the MD arrays assembling process and the arrays health checks ; the latter may start before all the arrays are fully assembled. In that case, the boot is interrupted and you are asked if you want to continue with a "degraded array" ... all of this happening while Ubuntu shows the "purple screen of death" (i.e. you don't even see the "degraded array" question since Ubuntu flashes that purple color - normally for 2 seconds, but in this case until you answer!).

So you could answer "yes" to that question [if you can see/guess it] and carry on... since the arrays were fully assembled in the meantime (and skip the health checks btw).
Some people, fed up with this race condition bug, may have indeed used the boot_degraded option to boot "normally" (while hiding a possible real HD problem). But the option itself is not the bug people are here talking about, in this thread.

---

### Post by KeithLM on 2012-05-13
> **Kleenux said:**
> The "bug" (more of a discussion), you are referring to, underlines the confusion surrounding the  boot_degraded option [ being an "option" it may mislead some admins as, if set to yes, may bring about the shadowing of a hard disk problem ].

The actual bug identified by dangriffin shows that there is a race condition - not less - between the MD arrays assembling process and the arrays health checks ; the latter may start before all the arrays are fully assembled. In that case, the boot is interrupted and you are asked if you want to continue with a "degraded array" ... all of this happening while Ubuntu shows the "purple screen of death" (i.e. you don't even see the "degraded array" question since Ubuntu flashes that purple color - normally for 2 seconds, but in this case until you answer!).

So you could answer "yes" to that question [if you can see/guess it] and carry on... since the arrays were fully assembled in the meantime (and skip the health checks btw).
Some people, fed up with this race condition bug, may have indeed used the boot_degraded option to boot "normally" (while hiding a possible real HD problem). But the option itself is not the bug people are here talking about, in this thread.

I understand the situation with this bug.  And Dan's fix works perfectly for me.  The question is, has an appropriate bug been filed and this solution posted as a suggestion?  I think that's the issue as to why this hasn't been fixed in 12.04.  So far as I can see, Dan's solution wasn't posted in bug postings that seem related to this issue.

---

### Post by nanog on 2012-06-02
There is a bug report that exactly describes the problem we are having. It was mistakenly marked as a duplicate by the triager.

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/917520](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/917520)

Please confirm this bug.

---

### Post by v4169sgr on 2012-06-06
> **gadnex said:**
> Lets hope this fix makes it into Ubuntu 12.04 so that mdadm works correctly on a default install.

It didn't :(

I struggled for two days before finding this thread.

Very grateful I did though - thanks dangriffin!!! :)

---

### Post by BAUSTIECH2 on 2012-06-11
DANGER - DO NOT USE UBUNTU 12.04 IF YOU HAVE ANY SOFTWARE RAID

There is a race condition that randomly marks good RAID arrays as failed.  This triggers an error that, due to another bug, ignores the "bootdegraded=true" kernel work-around parameter.  The end result is you end up in an initramfs shell called "busybox" that is a blackhole of doom and downage.

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220?comments=all](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220?comments=all)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/778520](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/778520)

And it's made much worse if you have nVidia video, which, due to another bug and/or driver issue, hides everything so you can't see anything of what's going on.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

---

### Post by sungaMagnus on 2012-06-20
@dangriffin,  you save my life.
I've been haunted by this for over half year and spent over the last 3 days and endless time resync the "degraded raid"

Ubuntu should fix this.

Many thanks.

---

### Post by ca_20gti on 2012-10-05
Out of curiosity, I am wondering if this will fix my issue. Actually it sounds identical to the issue I am having everything is fine until the purple screen. Then Boot = NOPE!  [-(

And after "scanning" the thread it looks as though this might only affect raids and I do not have a raid set-up even though my box has the options for a hardware raid if I wanted to do such a thing.

The strange thing is, the machine was booting fine until I formatted and reinstalled 12.04 (fresh install). Previously I was using 12.04 that was upgraded from 10 or 11, it was a while ago and don't remember... The machine was crashing often and tons of errors (reason for the format). Could it be this issue was resolved because the machine was upgraded and not freshly installed

I am running a mixture of SAS (OS and Video/Audio) and Normal SATA drives (for data only). I will try this when I get home. 

It's just a pitty I didn't find this last night before installing the OS 4 times! lol #-o

---

### Post by ca_20gti on 2012-10-06
Nope , didn't even have the option... Guess I am on to something else

---

