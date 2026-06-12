---
title: "The ordeal of a clean install of 10.10 (rant)"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by AKADAP on 2010-10-12
The system:
motherboard EP-8K7A+
memory      1 GB
Processor   AMD Athlon 1.4 GHz
Video card  AMD Radion All In Wonder
Monitor     Sony GDM-FW900

This system had been running windows 2000 without problems for years until I replaced it with a faster computer. It then spent about a year running Ubuntu as my fathers computer without problems. I use it now a a test setup.

With 10.04 it was unusable because of this problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/572104](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/572104)

So I decided to do a clean install with 10.10. To that purpose, I downloaded the ISO for the i386 desktop install on my main system that is running Ubuntu 10.04. When the download was complete, I started the download of the 64 bit install CD. While that was downloading, I started Brasero, selected the i386 iso from a list of about 5 ubuntu install isos in the same directory and burned a disk. I took the disk down and booted from it in the above mentioned computer, it failed claiming to be an i686 disk. Annoyed I went back to my main system and started Brasero again, I selected the i386 iso again, clicked ok and looked at the name it had there. It had actually selected the first name on the list, not the one I had selected. I repeated this several times with the same result. I finally moved the i386 iso out of that directory was able to get it selected and burn the disk. During all of this the i686 was being downloaded into the same directory. I think this was part of the problem because once it was complete, I was able to select the i686 iso from the list without trouble and burn it.

When I finally got an i386 install disk, I booted it on the old computer. Being paranoid I ran the disk check. It went to a dark blue blank screen and sat there.
Remembering my problems with my previous install, I rebooted, and went back to the menu looking for "safe video mode". This option did not exist. Instead, I found under F6 "Other Options" a list of undocumented options. Remembering that I was told to add "nomodeset" to the boot when debugging problems previously, I selected that option and was able to start the disk test. I left and came back several hours later and found a screen blanker had engaged. I hit the space bar to clear the screen blanker and started cursing as the results of the test flashed too fast to read as the system re-booted.
I restarted the disk test and happened to be in the room when it completed successfully.

I then selected install Ubuntu. After a bunch of thrashing, this got stuck at the second problem with this system. It chose a resolution that the monitor can handle, but the video card can not. In this mode, I can only see the stuff that is on the far left edge of the screen, and that data is repeated about 6 times over the rest of the screen.

I next tried running Ubuntu directly from the CD. This again chose the wrong video resolution, but under System->Preferences->Display one can change the resolution. The problem is that I could only see the left half of the System menu. After a bunch of trial and error trying to guess where the "Display" menu item was on the screen, I finally found it and got the Monitor Preferences window up. Of course it opens in the middle of the screen and I can't see it. So I alt-click and drag the invisible window to the left where I can see it and select the next smaller 16x10 resolution and click apply. This works, I can finally see the whole screen.

I then click on install, and the entire install appears to work fine... until I reboot. Kernel Panic!!! I get the following error message:
```

[    1.805028] kernel panic -not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[    1.805085] pid:1,comm:swapper Not tainted 1.6.35-22-generic#33-ubuntu
[    1.805133] Call Trace:
[    1.805188] [<c05c6468>]  ? Printkt 0x2d/0x35
[    1.805235] [<c05c63c3>]  panic+0x5a/0xd2
[    1.805283] [<c0819d8d>]  mount_block_root+0x1d3/0x26c
[    1.805338] [<c0224cfc>]  ? sys_mknod+0x2c/0x30
[    1.805381] [<c0819e7f>]  mount_root+0x59/0x5f
[    1.805425] [<c0819fd3>]  prepare_namespace+0x14e/0x192
[    1.805478] [<c0217885>]  ? sys_access+0x25/0x30
[    1.805522] [<c0819476>]  kernel_init+0x18/0x19d
[    1.805567] [<c08192d9>]  ? kernel_init+0x0/0x19d
[    1.805614] [<c010363e>]  kernel_thread_helper+0x6/0x10

```

I tried running the recovery mode, that said something about not being able to use a particular disk ID and claimed to be about to list the available disk IDs, but instead of listing disk IDs, I got another kernel panic.

As a last resort, I decided to try installing again. I followed the same procedure, but this time after a reboot, I did not get a kernel panic, I got a blank dark blue screen. One would think that since I had to select "nomodeset" every single time I booted the install disk that it might be a good idea to add that option to the install. But no. Now I had to try and remember how to get to the grub menu on boot since it was not being displayed by default. After a few wrong guesses I remembered that I had to hold the shift key down during boot. Adding "nomodeset" got past the blank dark blue screen, and got me to a login screen with the resolution set so high that I could not see the important parts. I blindly hit enter and typed in my password. This worked and I was presented with a desktop, again in a resolution too high to be useful. I had marked on a business card the offset from the top of the screen that the "Display" menu item should be when using the liveCD, but of course there are more menu items in the actual install, so I was in for a few more rounds of trial and error. After getting the resolution down to something that actually works, and setting that to default, I ran the update manager which already had a kernel update. After the update I rebooted. I missed the grub menu so I did not get a chance to add the "nomodeset" option, the booting screens were garbage, but I was surprised to find that the login screen was now working, and I was able to login. So it looks like I have a working system.

While all of this was going on, I was attempting to backup my home directory on my main computer. I have a USB hard drive attached to a DD-WRT router that is shared as a FTP drive. I attempted to copy my home directory to this drive several times, each time, it would copy for a while, then just stop transferring data. I then turned on an old windows 2000 machine with lots of free disk space and tried to copy the home directory to that using smb with the same result. I finally did the backup my moving the USB drive from the dd-wrt machine directly to the computer I was trying to back up. That worked.

This should not have been this hard! After all these problems I'm really nervous about upgrading my main system.

---

### Post by ShakeyJake on 2010-10-12
> **AKADAP said:**
> After all these problems I'm really nervous about upgrading my main system.

Well don't. 10.04 is good 'till 2013.

Sorry to hear about your installation problems. It seems (as ever) shiny newness brings bugs. Wait, and update when it's safe.

---

### Post by ratcheer on 2010-10-12
> **ShakeyJake said:**
> Well don't. 10.04 is good 'till 2013.

Sorry to hear about your installation problems. It seems (as ever) shiny newness brings bugs. Wait, and update when it's safe.

10.10 is running better for me than 10.04 ever did.

Tim

---

### Post by pricetech on 2010-10-12
I usually stick with LTS releases but I may try Maverick at some point.  As always, ones mileage will vary.  I'm seeing posts that say Maverick works better than ever and posts that say it crashed / corrupted / lost / etc something.

---

### Post by AKADAP on 2010-10-12
> **ShakeyJake said:**
> Well don't. 10.04 is good 'till 2013.

Sorry to hear about your installation problems. It seems (as ever) shiny newness brings bugs. Wait, and update when it's safe.

There is nothing new about the hardware I was having trouble with, and the disaster of an install on that hardware with 10.10 is actually a better result than I had with 10.04!

So my experience shows me that 10.10 is better than 10.04, but 10.10 is terrible!

On the last update to my main system 9.10 to 10.04 I had a bunch of trouble with video drivers, but ultimately got it to work.

---

### Post by AKADAP on 2010-10-16
I scheduled the update to my main system for today since there was a long gap between scheduled recordings on MythTV.
I was surprised when it went rather smoothly. 3 hours to download the data, 1 hour (interrupted 4 times by requesters asking questions they should not have had to ask) updating.

So far I haven't found any thing broken, though it uninstalled gthumb when it should not have.

---

### Post by Karpah on 2010-10-19
After not being impressed by 10.10 on my desktop machine, I'm leaving my netbook on 10.04 (especially because I can't seem to run Unity on it, even though it has a dedicated Nvidia chip. Go figure.)

---

