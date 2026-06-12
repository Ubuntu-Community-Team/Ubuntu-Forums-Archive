---
title: "FATAL error, Ubuntu 9.10 will not boot after Package Manager upgrades"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by ddubdub on 2009-12-13
Well, now I've done it...

I think this issue is going to be a very tough one for a couple of reasons:

1) I'm pretty new to Linux
2) My Linux install is running off a USB drive in a persistent fashion (done with instructions on pendrivelinux.com)

I have been using the USB drive installed version for several weeks.  I loved it.  No issues.  Until today.  In the Ubuntu package manager, I checked for updates and did an apply/install.  There were a lot of items updated.   I think 170 in total.  It told me I needed to reboot after the updates, so I did.

After restarting, it brings up the boot screen as usual.  I select the "Boot persistent..." option as usual.  I will get to the pulsing Ubuntu symbol as usual.  Then, the Ubuntu symbol goes away and the screen is blank.  After pressing a key, here is the error:

FATAL: Could not load /lib/modules/2.6.31-16-generic/modules.dep
No such file or directory
Unable to find a medium containing a live file system

Uh oh, that sounds bad :)

A basic shell comes up that I can navigate in.  I have the following directory, not the one it's looking for above:
/lib/modules/2.6.31-14-generic

And in that directory, there is a 'kernel' directory and a file called 'modules.order'

So I'm in a bad state.  I'm sure there'd a way to fix it if I was running on a normal install on a hard drive, but I have a feeling that because my install in on a flash drive and I don't have external access into these directories (I think they are part of a "casper" partition, whatever that is!), I don't know if there's going to be a way to fix this.

If there is no way to fix this flash drive install, is there any way to get my home directory or files out of this casper partition?  I have some files on there I would really like to get back.

---

### Post by audiomick on 2009-12-13
Hallo.
Don't know if you can fix it, sorry.
It looks like it is looking for a kernel that isn't there.

You should be able to get your stuff out of the /home folder if you boot into the live CD.

---

### Post by ddubdub on 2009-12-14
Thanks.

Well, according to an email from the friendly folks at pendrivelinux, you shouldn't try to do a system wide update as it "might not take." Apparently that's in the "disadvantages" section of their pros/cons of a persistent boot image. Love that fine print.

I found a post explaining how to mount the casper-rw in order to copy files off it. I will do that and start over with a new install.

Tough lesson to learn. If I was advanced, maybe i'd be able to figure out how to repair instead of reinstall.

Ddub

---

### Post by naadoodi on 2009-12-15
Hi,
I got the same error and found some other forum below one.

under your USB drive syslinux edit text.cfg

to below one
 append  locale=us_us bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/Ubuntu.seed boot=casper initrd=/casper/initrd.gz splash--

 initrd should point to /casper/initrd.gz  instead of initrd.lz

---

### Post by Steve Redmond on 2010-01-15
Hi!  I have a similar problem with Live USB with persistence becoming unbootable after running updates with Update Manager.  

I don't think this has always been the case, but I haven't kept track of updates to Live USB, until now when it is a problem.  In the last few weeks, right up until today, any attempts to install the full load of updates 'kills' my Live USB version.  

I haven't tried to control which updates are installed, but I suspect that at least one may be the kernal update, and another deadly item may be an update to Grub.  Since my Live USB uses syslinux as its bootloader, I doubt that any good can come from an update to Grub.

I don't have a solution yet.  I did find these threads for similar issues about kernal updates with Kubuntu 8.04 LiveUsb to be of interest, and as far as I can tell Ubuntu 9.10 still behaves similarly:[INDENT][http://kubuntuforums.net/forums/index.php?topic=3096170.0](http://kubuntuforums.net/forums/index.php?topic=3096170.0)       (search for: "However the advice from the bug report here :" )
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/292159](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/292159)       (search for "[latchkeyed]("https://launchpad.net/%7Eian-cloudwatcher")             wrote             on 2008-11-13:                          "
[/INDENT]This 'bug' in LiveUSB is hazardous to your setup and data, assuming you truly want them to be persist.  I found my USB memory sticks to be completely unreadable after these incidents.  Also, since these are using USB volatile memory, and not CD's, I expect the system to be able to handle updates gracefully.  Even if there are inappropriate updates for a LiveUSB, I would at least expect Ubuntu Update Manager to notify me and block them to prevent harm.

I'm still looking for information and a solution.

Steve

---

### Post by samatt on 2010-01-27
> **naadoodi said:**
> Hi,
I got the same error and found some other forum below one.

under your USB drive syslinux edit text.cfg

to below one
 append  locale=us_us bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/Ubuntu.seed boot=casper initrd=/casper/initrd.gz splash--

 initrd should point to /casper/initrd.gz  instead of initrd.lz

Outstanding.  I had just created a new live USB and immediately went to update manager to bring it up to speed.  Upon reboot got the same error.  I googled different search terms but couldn't quite get a functional answer.  I was just about to wipe it and reinstall when I found this thread.  I booted from another USB drive, opened text.cfg in gedit and made the changes as you suggested.  There were three initrd.lz entries and I changed all three to .gz.

Shut down, rebooted and all is well again.  Thanks for saving me hours of effort re-creating the USB and trying to update without falling down the same hole.  I'm just hopeful there aren't any other time bombs awaiting me from the update.

---

### Post by Bender2k14 on 2010-03-31
I also had this problem after trying to update a fresh USB install (via the USB Startup Disk Creator).

Changing the extension .lz to .gz (as described above) also worked for me.

Thanks! :)

---

### Post by Bender2k14 on 2010-03-31
I created a bug in lanuchpad about this issue:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/552800](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/552800)

---

