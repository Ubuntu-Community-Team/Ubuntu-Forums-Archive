---
title: "Trying to upgrade from 16.04 to 17.10 on a Dual-Boot system - stuck in initramfs"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by bschwartz757 on 2017-10-20
Hello!

I just tried to upgrade from 16.04 to 17.10 - had it on a USB stick and was in trial mode, then decided to go ahead and install it. I have a dual-boot setup with Ubuntu 16.04 which I've been using as my primary system for about6 months, and Windows 10 which I rarely touch anymore (although I am a recovering Windows user.) I like to have the option and have some files there I don't have on my Linux machine. 

After starting the upgrade process, I saw a message that said the drive partition was causing an issue. I tried pressing the 'go back' button, but the system appeared frozen. The 'continue' button also didn't work. I finally gave up and hard-restarted the machine, and went to one of those 'waiting for boot sequence' screens. I waited a while and then hard restarted. 

Now, I'm able to boot into the grub menu and select Advanced Options - but I get a list of ubuntu versions (backup images?) and not an option to select 'Root' which is what all the threads I've found tell you to do. Instead, when I select one from the list the system spits out a bunch of info and then I'm dropped into an (initramfs) prompt, it looks like I'm on a really stripped-down version of bash (looks like it's BusyBox - Ash). I can't execute any commands as sudo as it says sudo is not found in /bin/sh.

I've been trying to follow directions from [https://askubuntu.com/questions/901402/kernel-panic-cant-exit](https://askubuntu.com/questions/901402/kernel-panic-cant-exit) and [http://www.rffuste.com/2016/10/01/ubuntu-16-04-a-start-job-is-running-for-hold-until-boot-finishes-up-error/](http://www.rffuste.com/2016/10/01/ubuntu-16-04-a-start-job-is-running-for-hold-until-boot-finishes-up-error/), but don't have enough reputation to actually post comments to any running threads.

I can still boot into my Windows 10 machine just fine, and all my programs work and files are there - so it seems like there may be hope for the Ubuntu side. I'm pretty sure my filesystem got unmounted somehow but I just don't know enough to fix it. Any help would be most appreciated!

---

### Post by ian-weisser on 2017-10-20
First, you NEED backups. Partitioning your disk and installing OSs are activities with a *significant probability of complete data loss.* This forum is littered with users who mistakenly destroyed-beyond-recovery years of their works and art and science and family photos...because they didn't backup and made a trivial mistake while partitioning or installing.

Second, the grub "list of ubuntu versions" are not backup images. Not at all. They are merely various older kernels, so a kernel update doesn't leave your Ubuntu system unbootable.

Third, search this forum for Boot Repair. Create a LiveUSB with Boot Repair. While booted into the Live environment, backup your data from BOTH Windows and Ubuntu - this might be your last chance. Then run Boot Repair. If you can get Ubuntu to boot, we'll work on the next step.

A failed release-upgrade, under some conditions, may be almost impossible to recover from. It's impossible to say from the information so far. But be prepared to reinstall afresh. Good thing your data is now backed up.

---

### Post by bschwartz757 on 2017-10-29
Ok so I was able to get back in and back up the last of my files that weren't backed up (booting into "try ubuntu" on my new 17.10 image.) I was also able to boot into the Windows machine as well, and verified everything I need is backed up externally. 

Following some more research, I ran gparted from the trial ubuntu system. It didn't really seem to fix anything, but I can see that all my partitions are still there - they're just not mounted. I have tried puzzling my way through how and where the partitions should be mounted, but haven't really found anything that explains this in a clear and straightforward way. 

One thing now is that I can no longer boot into the Windows system - it gives a "Windows Boot manager failed to start" error, so maybe using the gparted auto-check/fix utilities messed that up. Not the end of the world, but if I could get the filesystem mounted again properly I think that might help.

After trying to mount/remount a few partitions following online threads, I decided to give up and run Boot Repair. This did say it ran successfully, and I was finally able to quit from the liveUSB trial version of Ubuntu 17.10 without being dumped into the "a startup job is waiting for..." screen. However, I'm still unable to boot into Windows, and when I try to boot into my Ubuntu 16.04 system I get this:

```

/dev/nvmeOn1p6: clean, ... files, ... blocks
mount: mounting /dev on /root/dev failed: No such file or directory
run-init: opening console: No such file or directory
Target filesystem doesn't have requested /sbin/init

```
And then dumps me into the initramfs prompt.

Here is a link to the pastebin created by Boot-Repair:
[http://paste.ubuntu.com/25848170/](http://paste.ubuntu.com/25848170/)

Any help would be most appreciated! At this point, I realize I may need to wipe out and start over which is ok, but if possible I'd love to recover my partitions because 1) I don't want to re-create everything if I don't have to and 2) I don't want to re-install all of my software... Probably time to start making setup scripts once this is all over with.

Thanks!

---

### Post by bschwartz757 on 2017-10-29
[ATTACH=CONFIG]277337[/ATTACH]

Almost forgot - here are my partitions as shown by gparted.

---

### Post by bschwartz757 on 2017-10-29
I'm also curious if this thread could be of use, and if so, how: [http://gparted-forum.surf4.info/viewtopic.php?id=17373](http://gparted-forum.surf4.info/viewtopic.php?id=17373)

---

