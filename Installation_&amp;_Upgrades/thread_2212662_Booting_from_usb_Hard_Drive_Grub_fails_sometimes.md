---
title: "Booting from usb Hard Drive Grub fails sometimes"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by siabost on 2014-03-22
Hi,

I had a 5-year old 2.5" exlaptop spinning SATA Hard Drive kicking about so I bought a cheap (£7) External Enclosure for it to turn it into a USB2 External Drive. The enclosure is a Dynamode USB-HD2.5S-BN.

The idea was to use it as a secondary boot device, so I loaded Ubuntu 13.10 64bit on it, in the usual manner, ensuring that grub was installed to the external drive (sdb). The installation boots fine sometimes, showing the grub menu for a few seconds and showing a menu entry for the OS (also Ubuntu) that's on the internal Hard Drive. Other times I get a "grub" prompt or a "grub rescue" prompt or sometimes nothing at all.

When I've had the "grub rescue" prompt I've run the following to get a successful boot:
```
set prefix=(hd1,1)/boot/grub
set root=(hd1,1)
insmod linux
linux (hd1,1)/vmlinuz root=/dev/sdb1 ro
initrd (hd1,1)/initrd.img
boot
```

Then I ran from Terminal:
```
sudo update-grub
```

But the external Hard Drive boot up remains as unreliable as ever.

fstab reads as follows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=0ea953b2-748a-449d-88c4-6db77d862b02 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=0442794e-7b2f-4e34-9049-48bef45cfde1 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a885107b-69a3-4ec0-912c-153521ab15fd none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=da09b9fa-a9ec-47e2-84be-9a6c8a3c9638 none            swap    sw              0       0
```

Could it be that sda and sdb rederences are getting mixed up between the drives? If so, how do I stop this happening? Can the drive references sda & sdb be changed to fixed UIDs?

NOTE: Before installing Ubuntu on the external drive I tried SolydX 64bit and I don't recall the same problem, although I didn't run that very long. SolydX is based on Debian with an XFCE Desktop.

Many thanks in anticipation :-)

---

### Post by ubfan1 on 2014-03-22
You might try adding some additional delay in the boot sequence.  There might be a time delay you can set, or a value to change from "fast" to "normal".  This might let the USB stabilize and see the devices plugged in better.  Also try powering up the USB before the computer, instead of at the same time.  That said, I have found that some external disk enclosures work better than others for booting, although all work fine as data disks.  Another workaround is to boot (run grub) off a USB flash sitck which sets the external disk as root.

---

### Post by siabost on 2014-03-22
Hi ubfan1,
Thanks.
That seems reasonable - I tried the device again just now and it needed three goes to boot up. When it does, it works perfectly.
The usb case gets its power from the usb connection of the laptop it's controlling so I can't get it to start before the laptop in order that it gets a chance to stabilise.
There may be a setting I can alter in BIOS so I'll try that. The laptop's internal drive is an SSD so that might be responding too quickly, adding to the problem?

You mention some HD Enclosures work better than others as boot devices - could you point me to some of the better ones, please?
The price (or lack of) of this one might the clue to its longer stabilisation requirement.

Adding a flash drive for grub is a possibility but as I am testing this for someone else, that might be a level of complexity too far.

I suppose I could install grub to the internal HD but then I was hoping to leave that drive untouched. Especially as the intended recipient of the device has WinXP on his main drive.

Thanks again.

---

### Post by Bashing-om on 2014-03-22
siabost; Hi !

My 2 cents worth; in accordance with ubfan1's delay advise:
Might try something like:

edit the file "/etc/default/grub"
Find the variable LINE
GRUB_CMDLINE_LINUX=""
change it to
GRUB_CMDLINE_LINUX="rootdelay=90 nomodeset"
Save the file and run
```

update-grub

```
See if that works, and then ->
Play with the options, 'nomodeset' I should hope is not required and 90 seconds may be excessive.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by ubfan1 on 2014-03-22
I never had any problems with a prebuilt 3.5" Maxtor Encl/Disk.  All other 3.5" encl. had problems booting, most problems with oldest disk, an 80G rescued desktop disk.  Best case only booted 25-30% of the time, worst case 1% of the time.  But in every case, the unit worked fine if not trying to boot off it.

---

### Post by siabost on 2014-03-22
Thanks ubfan1 & Bashing-om,

The "rootdelay" helped but didn't entirely fix the problem.
If I hit the escape key to interrupt the BIOS on boot-up (which brings up the boot order menu on my laptop), wait a few seconds & hit the escape key again, the external drive boots up fine. So those extra 2 or 3 seconds is enough to let the case electronics settle and allow the boot sequence to start correctly.

Unfortunately, there doesn't appear to be any way to set up a small delay in the BIOS before it tries to initiate the boot drive. The other options are installing grub to a seperate flashdrive or to the internal hard drive.

Thanks for the advice, though. Now I know where the problem lies :-)

---

### Post by Bashing-om on 2014-03-22
siabost; Well, Looking positive.

In my bios (Phoenix Award) I do have an option to delay hard drive spin up. Might spend a bit of time in yours and see if it does exist.

[INDENT][INDENT]my little bit
[/INDENT][/INDENT]

---

