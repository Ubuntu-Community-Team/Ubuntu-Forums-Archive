---
title: "USB install, how to prevent over write of HD MBR?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by bfromcolo on 2009-12-22
I have Ubuntu 9.10 installed on a bootable 4G USB flash drive.  Overall it works well.  I typically use it in my work laptop when I am not working, HP Compaq nc6400.  The Windows installation on my work laptop is Safeguard encrypted and therefor does not have a typical master boot record.

Twice (once during install and once during an update) Ubuntu has over written the MBR of the hard drive with out even prompting me about the changes it intended to make.  Previous version of Ubuntu with the older Grub would prompt me before making these types of changes, at least I seem to remember it did.  This leaves the Windows system unbootable, I get a Grub error, and it requires some effort to recover the MBR so I can use Windows again.  For now I have disabled updates in Ubuntu and will remove the hard drive all together before I run another update.

Is there someway to get Ubuntu to completely ignore the existence of the hard drive?  And NOT ever make changes to it, especially during updates?

Thanks

---

### Post by efflandt on 2009-12-22
After you answer all the questions about the install and get to the summary screen just before installation proceeds, you need to pay attention to the **Advanced** button, and use that to tell Ubuntu to install grub to mbr of USB device/drive, instead of default to mbr of your main drive.

That caught me off guard (that it did not ask) when I first installed Ubuntu to my desktop and laptop.  I wanted to put grub on a partition instead (which I have now done on my desktop).

So I was aware of that by the time I installed 64-bit Ubuntu 9.10 on USB WD Passport.  I needed that for my work laptop which already has 4 partitions that I did not want to tamper with (2 Dell partitions besides XP Pro and partition for media without Windows).  The USB drive works just as well on my desktop, personal laptop, and a new Dell 15 laptop I am setting up for someone (running from that drive now).

---

### Post by HappyFeet on 2009-12-22
DO NOT update your flash drive. If you do, you will soon find out why you should not.

---

### Post by oldfred on 2009-12-23
I copied this from another thread as I have multiple drives and wanted to keep track of where grub is:

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by bfromcolo on 2009-12-23
> **HappyFeet said:**
> DO NOT update your flash drive. If you do, you will soon find out why you should not.

Why?  Until this most recent issue with the MBR of the hard drive the updates have been fine.

---

### Post by cchi on 2010-06-16
Hello, I read your first post at the top of this page:
[http://ubuntuforums.org/showthread.php?t=1361987](http://ubuntuforums.org/showthread.php?t=1361987)
With great interest.  I have done exactly the same thing!!

You said:
"This leaves the Windows system unbootable, I get a Grub error, and it requires some effort to recover the MBR so I can use Windows again."

How did you get your safeguard Windows back?  please share..  my work is going to kill me when I cant boot to windows!  Thank you!

---

### Post by C.S.Cameron on 2010-06-16
> **cchi said:**
> Hello, I read your first post at the top of this page:
[http://ubuntuforums.org/showthread.php?t=1361987](http://ubuntuforums.org/showthread.php?t=1361987)
With great interest.  I have done exactly the same thing!!

You said:
"This leaves the Windows system unbootable, I get a Grub error, and it requires some effort to recover the MBR so I can use Windows again."

How did you get your safeguard Windows back?  please share..  my work is going to kill me when I cant boot to windows!  Thank you!


Use the windows install disk to run emergency repair console and then type "fixmbr"

---

### Post by C.S.Cameron on 2010-06-16
> **HappyFeet said:**
> DO NOT update your flash drive. If you do, you will soon find out why you should not.

I think bfromcolo has done a Full install to flash drive not a persistent install.

I always unplug the hard drive myself although some people say using the "Advanced" option works ok.

---

### Post by emarkay on 2010-06-18
> **C.S.Cameron said:**
> I think bfromcolo has done a Full install to flash drive not a persistent install..


Since this thread is relevant to my current issue, (Persistent Lucid USB update fail - [http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603) ) and it's been "brought back from the grave" I wonder too - but they're not accepting PM's to answer.

---

