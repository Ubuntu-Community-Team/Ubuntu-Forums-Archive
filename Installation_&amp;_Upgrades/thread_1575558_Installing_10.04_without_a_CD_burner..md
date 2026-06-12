---
title: "Installing 10.04 without a CD burner."
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by Jesdisciple on 2010-09-15
It's been a while since I hosed my system, and I finally stopped procrastinating to backup, format, and reinstall.  The latest disc I have available is 9.10, and getting new ones is a feat now that Canonical won't mail them to me.  So I installed 9.10 and immediately upgraded to 10.04; somewhere in there it asked me where to installed GRUB and I told it sda1 but not sda, which was apparently a mistake.

I got an error about "grub_puts_" being undefined and used [this guide]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") per [a relevant thread]("http://ubuntuforums.org/showthread.php?t=1397629&page=2").  I rebooted and got through GRUB, but now all that comes up is the purple background and my cursor; the mouse doesn't move, not that there's anything for it to click anyway.  I went on #ubuntu IRC and was advised to do a clean install rather than an upgrade.

Of course I can just stay with 9.10 but would prefer the latest (of course it's about to be obsolete anyway...).  I have also heard that it's possible to install to a USB drive; I'm guessing that likewise requires a CD?  I guess what I'm wondering is whether I can use a 9.10 install to download and install 10.04 directly to a different device?  Finding someone who has a CD burner is a real hassle.

Thanks.

---

### Post by oldfred on 2010-09-15
Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

### Post by CharlesA on 2010-09-15
I used Grub4DOS to do a multiboot USB.

If you don't have a CD burner, doing a bootable USB would probably be the way to go.

Check out unetbootin or similar tools.

---

### Post by Jesdisciple on 2010-09-16
Well, I guess I need to sit down and read for a few hours some day soon.

But since a USB can be installed onto without a CD, surely we can turn that on its head, basically use a full hard drive in place of the USB?  Especially if the USB is running Ubuntu itself, but even without that I have my old Live CD that can.

---

### Post by oldfred on 2010-09-16
You can also boot an ISO from a hard drive. But you cannot install to that same partition or any partition that is mounted. So if same hard drive it just about has to be a primary. Of course if you have a full install on one drive you can boot the ISO from that and install to another drive.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

