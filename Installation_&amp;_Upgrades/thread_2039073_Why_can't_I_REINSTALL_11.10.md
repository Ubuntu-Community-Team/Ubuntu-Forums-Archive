---
title: "Why can't I REINSTALL 11.10?"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2012-08-08
Hello folks,

I'm no longer new to the seamy underbelly of Linux.  Starting a few months ago, I got pulled into the [_graphics card driver upgrade vortex_]("http://ubuntuforums.org/showthread.php?t=1743535").  I'm now familiar with using my rescue shell, rebuilding the video driver when the kernel gets upgraded, etc.  I know what I have to do to accomplish these tasks on my RAID1 system, [_which adds its own complexities_]("http://ubuntuforums.org/showthread.php?p=11918272#post11918272").  

But I have a new problem I simply can't figure out.

My current problems MAY have started when my video monitor died.  I sent it out for warranty service.  I plugged in a somewhat older, smaller monitor, and the system ran.  That monitor was the one I gave my son for his computer, however, and he wanted it back.  So I borrowed an even older monitor from a friend, plugged it in, and after the GRUB menu I got -- the dreaded Aubergine Void.  I plugged my son's monitor in again, and this time, it too went to Aubergine.

Did the mere act of attaching different video monitors to the end of my video card's DVI cable cause an irreversible software problem?  [_I asked that question in another thread_]("http://ubuntuforums.org/showthread.php?t=2037574"), but I did not receive an answer.

Tedious though it is, I decided to reinstall Ubuntu 11.10.  I've done that before.  I have a separate **/home** partition, so my data should be safe.  (I'll have to reinstall all my applications though, grumble.)  I went through the reinstallation process, using the Alternate Install CD because, as I said, I have a RAID.  I got no error messages during the installation process.  But again, on reboot, I found the system hanging on Aubergine.
 
Knowing that this could be a video driver problem, I rebooted with the alternate install CD, and went through the process of rebuilding my video driver using the "current" kernel headers (which, because I just reinstalled from the CD, is 3.0.0.12).  I know that I'll have to go through that process all over again once I get the online updates for the OS.  But at least I expected to get to the GUI where these tasks would be easier.

That didn't happen.  After rebuilding the video driver and rebooting, I got a GRUB menu this time.  But the only kernel it had listed was... 3.0.0.23, which is the kernel I HAD before reinstallation.  Selecting that kernel sends me to ***[COLOR="Magenta"]/dev/null/aubergine[/COLOR]*** once again.

I deduced that somehow my GRUB configuration hadn't updated correctly when I reinstalled.  So I rebooted from the alternate install CD, chose the "repair a broken system" option, executed a shell with my RAID "/" partition as root, and ran **update-grub**.  The messages indicated that grub.cfg was cleaned out and that a link to the 3.0.0.12 kernel was created.

Then I rebooted again, from the RAID, and -- the GRUB menu was still showing 3.0.0.23!  What?

Finally, I tried directing the alternate install CD to FORMAT the RAID logical partition that I will use for the root file system, and then reinstall the OS once again.  My GRUB menu upon completion of the reinstallation still showed -- kernel 3.0.0.23, which still refuses to boot.

I am baffled.

Before you suggest that I try 12.04, be advised that I tried  12.04 a few months back, [_with bad results_]("http://ubuntuforums.org/showthread.php?t=1974971").  The system hung DURING the installation process, with my hard drive thrashing madly for over an hour.

Any help is appreciated!

---

### Post by darkod on 2012-08-08
Do you have a separate /boot partition maybe? You would need to format it too when reinstalling so it can delete all old files.

Otherwise, it's really weird. Yes, you do need to format / in any case otherwise there will be left overs from the previous system, but you tried that too.

In case updates are downloaded during install, can that maybe update the kernel to -23?

---

### Post by ladasky on 2012-08-08
> **darkod said:**
> Do you have a separate /boot partition maybe? You would need to format it too when reinstalling so it can delete all old files.

I have three partitions in my RAID.  The first is used as swap, the second as /, and the third as /home.  I see these same three partitions every time I try to reinstall.  If there was a separate /boot partition, I SHOULD see it when I'm using the partition manager, right?

> **darkod said:**
>  In case updates are downloaded during install, can that maybe update the kernel to -23?

I was wondering about that.  But the last time I did a reinstallation, I am pretty sure that I wasn't offered a kernel upgrade until after I had installed the kernel on the CD and booted to the GUI.

I am starting to think that I will try to back up my /home partition and reformat my entire RAID.  Should this be necessary???

---

### Post by darkod on 2012-08-08
No, reformatting /home shouldn't be necessary. On the other hand, what you are experiencing shouldn't be happening either. :)

---

### Post by ladasky on 2012-08-10
OK, this is getting stranger.  My RAID partition table definitely got corrupted somehow.  This time through, when I booted from the rescue disk, I was confronted with a different range of options after automatically assembling a RAID (I'm using RAID1).

I'm expecting the following:

[LIST]
[*]/dev/md/0, built from the physical devices /dev/sda1 and /dev/sdb1.  Used as swap.
[*]/dev/md/1, from /dev/sda2 and /dev/sdb2.  Mounts as /.
[*]/dev/md/2, from /dev/sda3 and /dev/sdb3.  Used as home.
[/LIST]

Instead, I'm seeing weird changes to /dev/md/1.  I now have a /dev/md1 (note the missing slash).  Then, I have a /dev/md/125, /dev/md/126, and /dev/md/127!  What are these?

When I rebooted the machine, these new partitions came up automatically.

I need to undo this mess.  I would like to delete the 125, 126, and 127 partitions, and recover /dev/md/1.  I went into the partition editor, and did a test deletion of these RAID entries.  I would have the ability to delete 126 and 127, but it would NOT let me delete 125.  Looking into the details, it claims this partition is defined as swap.  But so is /dev/md/0.

It's almost as if the system has built a nested RAID inside a RAID!  This is NOT what I wanted, and I have no idea how that occurred, or why it's even useful, or possible.

I can still execute a shell in the strangely-named /dev/md1, and I can mount /dev/md/2 and examine the perfectly-intact contents of my /home directory.  I haven't hurt my data partition (yet).  I would greatly appreciate any recommendations that you folks might have to back my way out of this weird mess!

I am contemplating booting from my standard install CD, running GParted, and from there delete and rebuild /dev/sda1, /dev/sda2, /dev/sdb1 and /dev/sdb2.  It's drastic, but -- it may get rid of the problem? :confused:

---

### Post by ladasky on 2012-08-14
My nightmare deepens.

I now think that I may have had a RAID failure, which just coincidentally happened while I was swapping video monitors, as I described in the first post of this thread.  And it began with a simple mechanical problem.

Here's what I think happened, something that I didn't mention the first time: when I couldn't get one of those old video monitors to show me a login screen, I briefly tried VGA.  My video card outputs are DVI only, so I tried to use the motherboard's basic on-board video.  I pulled my video card out of the machine, a quick way to ensure that the system would use the on-board video.  When I did so, I pulled a SATA cable loose from one of my two RAID drives.  There is a small crack on the drive's SATA socket!  The metal tab no longer snaps when you push the plug into the socket.  I didn't notice this crack, and it allowed the cable to get pulled loose as I was fiddling with other components in the computer case.

I booted the machine and, as I mentioned, the screen went to Aubergine Purgatory after the GRUB menu.  A few boot cycles later I noticed, as the BIOS screen was flashing by, that only one SATA drive was being detected.  I found the disconnected cable, plugged it back in, duct-taped the bugger down, rebooted, and registered two drives again.

When does Linux begin WRITING to / and/or /home?  During the boot cycle?  Did I damage my RAID during those boot attempts?  Is it merely out of sync and repairable, or have I lost it completely?

I don't care if I have lost / .  I DO want to recover some recent data from my /home partition.  My most recent backup was about a week old.

I took out my 11.10 standard (not alternate) CD, and selected the "try Ubuntu without installing" option.  In this configuration, the system will not recognize the physical partitions on the two drives as RAID.  That may be acceptable.  I am thinking that, if I can't reassemble the RAID, I can just back up the two physical partitions separately, /dev/sda3 and /dev/sdb3, to be extra-safe.

But when I get to the GUI, the system will not mount any of my internal hard-drive partitions at all.  Nor will *gparted*.  GParted gave me an error dialog box suggesting that I look at the output of *dmesg*.  I did, and I found this at the end (FYI, /dev/sdc3 is my USB backup drive):

```
[  105.507936] EXT3-fs: barriers not enabled
[  106.258532] kjournald starting.  Commit interval 5 seconds
[  106.264231] EXT3-fs (sdc3): using internal journal
[  106.264243] ext3_orphan_cleanup: deleting unreferenced inode 1436
[  106.264264] EXT3-fs (sdc3): 1 orphan inode deleted
[  106.264265] EXT3-fs (sdc3): recovery complete
[  106.310603] EXT3-fs (sdc3): mounted filesystem with ordered data mode
[  151.686808] EXT4-fs (sda2): ext4_check_descriptors: Checksum for group 0 failed (7653!=0)
[  151.686818] EXT4-fs (sda2): group descriptors corrupted!
[  463.630721] EXT4-fs (sda3): ext4_check_descriptors: Checksum for group 0 failed (54457!=0)
[  463.630731] EXT4-fs (sda3): group descriptors corrupted!
```

OK, what do I do with the information that the group descriptors (whatever they are) are corrupted?

I am afraid to use the "check and repair" options in GParted without understanding them further.  GParted also has an "attempt data rescue" option which, according to the error message I get when I select it, requires a tool called *gpart*.  I cannot seem to find any file called *gpart* through *apt-get*, not even when I execute *apt-get update* to add the universe repository.

I searched the forums for discussions about corrupt group descriptors.  [_This thread_]("http://ubuntuforums.org/showthread.php?t=1881479") suggests that I might need a utility called *testdisk*.  As with *gpart*, I cannot seem to download it.  [_This thread_]("http://ubuntuforums.org/showthread.php?t=1736742") suggests that *mdadm* might be helpful.  I am wading through be volumes of on-line text about *mdadm*, hoping to find a FM so that I can RTFM.

As an aside, I am using my video card again, though I'm booting from the 11.10 install CD with the *nomodeset* option.  I am confident that the video hardware is all functional now.  I'll deal with the inevitable video driver mess later.

Any advice or shortcuts?  Thanks!

---

### Post by Bucky Ball on 2012-08-14
If you tried 12.04 a few months ago it was a baby and very unstable for some. I only just installed it myself (usually wait six months after release) and it is pretty solid so far. Not saying it will be for you, though. If it runs from the CD, that would be a good sign. 

You could try booting to the recovery kernel with an ethernet cable in, choose the option to drop to a shell, and 'sudo apt-get install' and 'sudo apt-get upgrade' (that **won't** upgrade the release). I'm thinking your 11.10 CD might be a few months old also? There's probably been a kernel upgrade in that time. I only ever use LTS releases so wouldn't know for certain. ;)

---

### Post by ladasky on 2012-08-14
> **Bucky Ball said:**
> If you tried 12.04 a few months ago it was a baby and very unstable for some. I only just installed it myself (usually wait six months after release) and it is pretty solid so far. Not saying it will be for you, though. If it runs from the CD, that would be a good sign.

I think that bumping up to 12.04 is tangential to my current problem, which is recovering data from my /home partition.  But as long as we're talking about it...  

I DID try 12.04 back in May, and it went badly.  I [_could not get it to install_]("http://ubuntuforums.org/showpost.php?p=11918328&postcount=6") on my system, it hung for HOURS while trying to install GRUB.  The ISO checksum was correct.  I know that 12.04 is a long-term support release.  Does that mean that the ISO for an Ubuntu install CD gets updated after the initial release?  Unless I can get a CD (NOT Internet updates) with some bug fixes that were not present the first time I tried 12.04, I expect that I can't even begin to install it. 

(Edit: after doing a little more reading, I believe that I'm waiting for the 12.04.1 revision, which is not available for another two weeks.  When it is released, I hope that all the various versions are released together -- I need the AMD, 64-bit, alternate-install version.)

Still looking for help with that RAID... thanks!

---

### Post by darkod on 2012-08-14
I wouldn't touch a software raid array with Gparted, not until you try all possible options first.

Even if one cable was disconnected temporarily, it should sync when you plug it back and continue working. That's the point of raid.

If you had more than one disk disconnected at the same time, that could create a problem, but not one (unless we are talking about raid0 which is not real raid in fact).

If you boot into live mode with the live cd, add the mdadm package, is the array active or not? If not, try assembling it, something like:
```
sudo apt-get install mdadm (mdadm is not included on the live cd)
sudo mdadm --assemble --scan
```

That will scan all partitions for raid and assemble the array if it can. Post any errors that it might show.

rubylaser is a good mdadm expert, hopefully he can jump in for this thread after you post more data and also tell you what to try next.

---

### Post by ladasky on 2012-08-14
Thanks again, Darko.

I am most surprised.  I got NO errors!

```
ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md/1 has been started with 1 drive (out of 2).
mdadm: /dev/md/2 has been started with 1 drive (out of 2).
ubuntu@ubuntu:~$ sudo mkdir /media/hdroot
ubuntu@ubuntu:~$ sudo mount /dev/md/1 /media/hdroot
ubuntu@ubuntu:~$ sudo mkdir /media/hdhome
ubuntu@ubuntu:~$ sudo mount /dev/md/2 /media/hdhome
ubuntu@ubuntu:~$ ls /media/hdroot
bin   etc         lib         media  proc  sbin     sys  var
boot  home        lib64       mnt    root  selinux  tmp  vmlinuz
dev   initrd.img  lost+found  opt    run   srv      usr
ubuntu@ubuntu:~$ ls -l /media/hdhome
total 25
drwxr-xr-x 58 1000 1000  4096 2012-07-31 23:35 john
drwx------  2 root root 16384 2012-04-18 18:57 lost+found
```

Now, /dev/md/1 and /dev/md/2 remain INVISIBLE to GParted and to Nautilus.  I've tried to refresh them both and I do not see any new devices.  However, /dev/md/1 and /2 are visible from the shell, and can be mounted.  At least I can make a current backup.  Then I can reformat everything.

I am puzzled by why my Ubuntu installation failed to do with *mdadm* what I can accomplish manually.  But it is more important that I get a working computer again.  I should be able to brute-force my way forward from here.  I'll come back and mark the thread as "solved," as long as I don't get stuck again.

I do hope that 12.04.1 serves my needs better!  I have been with Ubuntu since 6.06.  The 11.x series has given me 90% of my systems-administration headaches.  Admittedly, I've complicated things by bumping up to a RAID1 and a high-performance GPU, but I've had several other problems that are unrelated to either my RAID or my GPU.

---

### Post by ladasky on 2012-08-15
This thing is STUBBORN.

I used *rsync* to back up /dev/md/2, my /home partition.  At least I'm not going to lose any data.

I then used GParted to delete all of my old partitions and create new ones.  When I did this, I thought that I _might_ have discovered what was preventing me from reinstalling: somehow the "boot" flag had gotten set on /dev/sdb1, one of the two physical partitions that comprised my swap partition.  I couldn't delete this partition until I unset that flag.  Did an operating system somehow end up installed inside one of my swap partitions?  I don't know.  I don't care.  I'm cleaning up.

Next, I installed 11.10, once again, from the alternate install CD.  Sigh of relief, I can auto-assemble the RAID again.  I have /dev/md/0, /1, and /2 again, and nothing else.  Back to what I expected.  The OS installation proceeded with no error messages.

I rebooted.  Got past my BIOS pages, and then... no GRUB menu.  Just **[COLOR="Magenta"]Aubergine[/COLOR]**.  My hard disk access light flickered for about a minute, and then went solidly bright.  Ctrl-Alt-F1 through -F6 did nothing.  I waited five minutes, and then shut down.

Just in case something had happened to my alternate install CD-ROM, I checked its integrity using the tool on the disk itself.  The CD-ROM integrity test passed.  This is the exact same CD-ROM that I used to install 11.10, on this system, in the first place.

The machine WILL still run 11.10 off the live CD.  To my mind, this narrows down the problem to the hard drives.  But I have reformatted the drives, and rebuilt the RAID.

Next, I booted from the alternate install CD, chose "repair a broken system", and executed a shell in /dev/md/1.  Even though I wasn't getting any complaints from the system when I followed these steps, I decided to have a look at *dmesg | tail*.

```
[  194.847467] Buffer I/O error on device sdb, logical block 1250261409
[  194.847469] Buffer I/O error on device sdb, logical block 1250261410
[  194.847470] Buffer I/O error on device sdb, logical block 1250261411
[  194.847471] Buffer I/O error on device sdb, logical block 1250261412
[  194.847472] Buffer I/O error on device sdb, logical block 1250261413
[  194.847473] Buffer I/O error on device sdb, logical block 1250261414
[  194.847489] ata3: EH complete
[  202.941231] EXT3-fs (md1): error: couldn't mount because of unsupported optional features (240)
[  203.072147] EXT2-fs (md1): error: couldn't mount because of unsupported optional features (240)
[  203.587786] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)
```

Do I actually have bad blocks on /dev/sdb?  Why didn't the system raise an error when I built the RAID then?

If there really are bad blocks, I did select the option not to boot onto a degraded RAID during the install.  Maybe that's why I'm hanging when I try to boot.  I would have expected a visible error message or something, though!  In fact, I think that I saw a degraded RAID warning several months back when I was dealing with another problem.  I'm not getting any information at all now, just an empty screen.

I tried ANOTHER reinstallation.  This time I tried F6 on the top menu of the alternate install CD and selected the "nomodeset" option, then selected "install Ubuntu."  This addresses video card problems, as I recall.  I do seem to need to select nomodeset to get the live CD to run.  Anyway, I still got Aubergine.

Then, from the alternate install CD once again, I edited /etc/default/grub and ran *update-grub*, to try to force nomodeset (as described on [_this page_]("http://askubuntu.com/questions/97475/monitor-shuts-off-after-installing-ubuntu-11-10-64-bit")).  I am STILL looking at Aubergine.  And I STILL did not see a GRUB menu on boot.

If I do have a video problem, I'm wondering why I didn't encounter this problem the last time I installed?  I think it might be because I already had 11.10 installed on my system when I got this new video card (an NVidia 460-family card).  I could still get a GRUB menu, perhaps because I had installed multiple kernel revisions (does GRUB simply not show, when you have only Linux on your system, and just one kernel?).  I may have edited the boot options from within GRUB.

Still confused and frustrated!  I've been at this for the better part of a week now!

---

### Post by ladasky on 2012-08-15
](*,) ](*,) ](*,)

I have backed up my /home from the RAID to an external drive, leaving me free to erase anything I want.  I disassembled my RAID, wiped the hard drives, created fresh partitions.  I have now tried reinstalling without RAID, using the standard CD.  I tried EACH of my hard drives, one at a time.  Both times it failed, in different ways.

When I tried installing to /dev/sda, I got no errors during the installation process.  But on boot, I got a "grub error:no such disk."  This dropped me into something called grub-rescue.  I could not see how to accomplish anything from there.  Still RTFM on grub-rescue.

Anyway, I decided to try installing to /dev/sdb, even though, as I mentioned, *dmesg* is telling me that I MAY have some bad blocks on that drive (*mdadm* never warned me previously).  This generated a Fatal Error during grub-install.  At first, the installer tried to put grub on /dev/sda (odd, given that I wiped every partition off /dev/sda before trying the /dev/sdb install).  I selected the option to try reinstalling GRUB to /dev/sdb instead, and I got the same Fatal Error.

I can still run from the 11.10_x64 live CD.  I am running from it right now -- although, as I mentioned, I have to force a nomodeset.

But I can no longer INSTALL 11.10 to my system!  In ANY way, shape, or form!  With or without RAID, it doesn't matter.

Arrrrgh!

---

### Post by Bucky Ball on 2012-08-15
Can't help with much of this but if you wiped sda (no partitions) that would leave free space, exactly what a Ubuntu install is looking for; not partitions. 

Don't make partitions to install to. Leave free space. Choose 'Something Else' when you come to the partitioning section of the install and manually create them using the free space. Default mountpoints /, /home, /swap, among others, are already there for selection.

---

### Post by ladasky on 2012-08-16
> **Bucky Ball said:**
> Don't make partitions to install to. Leave free space. Choose 'Something Else' when you come to the partitioning section of the install and manually create them using the free space. Default mountpoints /, /home, /swap, among others, are already there for selection.

I proceeded as you suggested, wiping the hard drive /dev/sda, and making partitions with the utility inside the installation procedure.  Ubuntu 11.10 installed from the standard CD without complaints.  On boot:

```
error: no such disk.
grub rescue>
```

I again erased all the partititons from /dev/sda.  Thinking that there might be something subtly objectionable about my partitioning scheme, this time I allowed Ubuntu to install its entire self -- boot, swap, and home -- to a single partition occupying the entire device(*).  This is not my preferred configuration, but I just want to see it boot!

The results were identical.  Installation gave no errors, but I got kicked to GRUB Rescue on boot.

Once more, with feeling:  ](*,) ](*,) ](*,)

I've found _[this page]("https://help.ubuntu.com/community/Grub2/Troubleshooting")_, and I'm reading it.  I am still wondering WHY I am getting this behavior.

(*Edit: I looked at the partition scheme that Linux chose for itself, and it's not a single partition.  /dev/sda1 was formatted as ext4, and mounted as / .  Then /dev/sda2 was formatted as a primary partition which contained the LOGICAL partition /dev/sda5, and this logical partition was mounted as swap.  I have never used this nested approach before.  Is it recommended?  Why so?)

---

### Post by ladasky on 2012-08-16
Some progress at last!  I'm not ready to mark this thread as "Solved" just yet, though.

The _[Grub2 troubleshooting page]("https://help.ubuntu.com/community/Grub2/Troubleshooting")_ recommends an automated _[Boot Repair utility]("https://help.ubuntu.com/community/Boot-Repair")_, which I tried.  It did nothing to correct my problem.  I still booted into grub-rescue after using it.  However, Boot Repair does produce a log file, which you can automatically share to the Internet.  My log file is _[here]("http://paste.ubuntu.com/1151066/")_.

I am no expert in reading that log file by any means.  But I saw three concerns, one of which I thought was most important.

```
 9   => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
10      the same hard drive for core.img. core.img is at this location and looks 
11      for (mduuid/95397e09bc3e362eee4fb109bc9f9ad7)/boot/grub on this drive.
```

I did not expect to see a copy of GRUB, or a Master Boot Record on /dev/sdb since, as I recounted in an earlier post, I deleted all of its partitions.  What's more, that copy of GRUB on /dev/sdb MIGHT be a hold-over from my RAID.  Given that line 11 says "mduuid" and not "uuid", it looks to me like it refers to a RAID partition.  So I tried an experiment.  I shut the machine down, unplugged /dev/sdb, and rebooted.

I got a GRUB menu.  I got a GUI login page.  I'm on!

My conclusion is that there is something on /dev/sdb that GRUB is TRYING to make use of, even when I think I've set up the system to boot from /dev/sda and ignore /dev/sdb.  This conflict is forcing me to the GRUB rescue mode.

What might this conflict be?  How do I correct it?  Clearly, just erasing partitions on /dev/sdb was inadequate.  (EDIT: Is _[this]("http://askubuntu.com/questions/131168/how-do-i-uninstall-grub")_ what I need to do? "Warning: Extremely Dangerous!"is jumping out at me.)

Perhaps I created some of my own problems after all, by trying to disassemble my RAID.  Perhaps the Linux designers thought that no one would ever try such a thing, and so they didn't design a graceful way to do it.  Given the inconsistent messages that I was getting, including one report of bad blocks, I thought that I might have to limp along with one hard drive for a while.  Maybe I still do, it's not yet clear.

I still want to restore RAID eventually, of course.  I suppose that, in order to accomplish that, I'll have to remove GRUB from both /dev/sda and /dev/sdb.

Thanks for any advice!

---

### Post by darkod on 2012-08-16
Having a broken grub on sdb is not a big problem as long as you are booting from the correct disk which in your case seems to be sda.

Simply double check in BIOS and change if necessary, to boot from sda and it looks to me it should work fine.

---

### Post by ladasky on 2012-08-24
> **darkod said:**
> Having a broken grub on sdb is not a big problem as long as you are booting from the correct disk which in your case seems to be sda.

Simply double check in BIOS and change if necessary, to boot from sda and it looks to me it should work fine.

And THAT was my final problem!  Somewhere along the way, while fiddling in my computer case, I discovered that SWAPPED the two SATA cables.  Months ago, I would guess.

Linux took this in stride, and silently remapped /dev/sda to what BIOS saw as my SECOND hard drive, and /dev/sdb to my FIRST.  I was technically booting from the wrong drive, but, since it was RAID, the two GRUB configurations were identical and it didn't matter.

Now after I disassembled the RAID, Linux was faithfully preserving this reversed mapping.  Every time that I tried to install to /dev/sda, I was actually installing to BIOS drive #2.  Meanwhile, on BIOS drive #1, I still had a GRUB that was looking for a RAID.

I have now labeled my hard drives and color-coded the SATA cables, so that this doesn't happen again.  With that problem understood and corrected, I was able to reinstall my RAID.  I'm back in business!  Thanks for sticking with me, I'm going to mark this thread as solved.

---

### Post by Bucky Ball on 2012-08-24
Wow, what a lot of spaghetti! Nicely unravelled. ;)

---

