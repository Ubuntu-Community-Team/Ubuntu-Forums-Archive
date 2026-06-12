---
title: "Adding additional SATA drives without causing problems with locating boot drive."
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Cronjob on 2006-09-27
This box contains all SATA drives, except the CDROM. To get Ubuntu to install properly, I had to remove all but one SATA drive. Does anyone know if there should be a problem with plugging the other two SATA drives in now that I already have things installed and running? Or will the same problem with identifying which drive is the boot drive still continue?

Forgive me for asking this question when I should just try it and see what happens, but getting to and modifying the box this on is a precarious thing at the moment.

Any comments would be greatly appreciated.

---

### Post by pseudonym on 2006-09-27
That shouldn't be a problem - the other drives should autodetect when you plug them back in. To be on the safe side, you might want to test it out by booting a live cd first. You will need to add manual entries in /etc/fstab to mount them, however.

It would also be good to know a little more about why you had to unplug the other drives, and what your relevant hardware setup is...

---

### Post by Cronjob on 2006-09-27
The reason I had to unplug all but one SATA drive is that linux (or grub, I presume) can't figure out which drive is in which order. So if there are multiple SATA drives plus the IDE CDROM drive, it will install and then upon reboot, it will just give you an "operating system not found" or similar error -- because it isn't loading from the correct drive.

Removing the other drives solved the problem. Now a few weeks later, I'm ready to put the drives back in - but am unsure if they will confuse linux/grub. Since I'm not using any IDE hard drives, I'm not sure why it would have that reported problem (which from what I have read in the past is not currently solvable by the installer/boot loader, because the IDE drive will throw each SATA drive off in it's drive number by one).

Anyway, there's nothing complex about the setup. Currently a single 74gb Raptor (SATA) with a lite-on IDE CDROM in a dual core 3800+ amd system running Kubuntu. Going to be throwing in two NTFS (ugh) formatted 320gb samsung SATA drives.

---

### Post by RichJacot on 2006-09-27
I had/have similar issues with my system when adding drives.  It turned out to by my MB BIOS screwing up the boot order.  Just an FYI

---

### Post by Cronjob on 2006-09-27
My understanding of the problem (there is a bug on file, which I can't find at the moment -- of course) is that it's something that can't be fixed by the installer or grub because it is in the BIOS as you mention. With all IDE or all SATA, I don't think it should be a problem. But a mix of SATA/IDE throws off the drive count.

So, for example, the BIOS might say your installation on the SATA drive is the second device, even though it's the first device. So then grub is going to try and pull up the MBR from the wrong drive.

However, I'm not certain if that applies only to IDE hard drives or if it applies to IDE devices of any kind. I was running into the described problem until I removed all of my SATA drives except the one I wanted to isntall to -- and the CDROM drive. And it worked. So that suggests to me that the CDROM shouldn't be part of what's throwing the BIOS or grub off.

On the other hand, since there are no IDE drives in this machine (other than the CDROM), I don't know why it would have experienced the problem at all. At least, as described by the bug reports.

Appreciate the feedback so far, though. Thank you guys.

---

### Post by pseudonym on 2006-09-27
> **Cronjob said:**
> Now a few weeks later, I'm ready to put the drives back in - but am unsure if they will confuse linux/grub. Should be no problem at all. That's similar to what I did when I upgraded to SATA drives on my machine. I have a 2-port integrated SATA controller and connected my windows drive first, installed winxp, then unplugged it. Hooked up the linux drive and did the install, but grub of course didn't pick windows up. That issue was fixed by editing /boot/grub/menu.lst to include windows, like so - ```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		The Evil Entity (my words, not grub's :) )
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

``` This just fools windows into thinking that it is booting from the primary SATA port. It usually gets written automatically if your install proceeds without hiccups. So when I reconnected the winxp drive, I was able to boot into it.

I'm assuming at least one of your NTFS drives has windows installed? If you need to do this, you will have to adjust the mapping accordingly (ie. may not be (hd0) (hd1) on your system). PLus, as noted above, you will need to assign mountpoints in /etc/fstab if you want them mounted at boot.

As to why this happens, I think it's a bug in libata, the linux SATA/RAID driver. Strange, like you say, that it happened on your system with just an IDE CDROM, though. But just reconnect your drives and you should be good to go.

---

### Post by Cronjob on 2006-09-27
I'm actually not running any other OS on this box. I just need to access the NTFS data drives which are on the other two SATA drives I want to add. After I figure out what to do with the data, I'll be reformatting them to ext3.

Here is what I have at the end of my menu.lst:

```

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

```

If I go into grub during boot and select my kernel, then 'e' to edit the boot drive, I change (hd0,0) to (hd1,0) and it still doesn't load. I've also tried hd2,0 and hd3,0 -- and it either can't boot or can't find the device.

I can edit fstab later to automount the extra drives, but my goal at the moment is to have all three SATA drives plugged in and the proper one with the actual OS on it booting up properly.

Can you nudge me in the right direction to know what I should be changing that to? And since I'm not using Windows on any drive or partition, can I just change the **root (hd0,0)** values in the above section without adding the portion you show in your example?

During POST, here is what the system reports for drives:

```

Primary IDE: CDROM
First SATA: WDC WD740GD (this is the drive I need to boot from)
Second SATA: Samsung SG250
Third SATA: Samsung 300LJ

```

I finally found an older thread with about 25 pages of posts, but I'm still unclear how people are deriving what drive/device grub needs to be told to load versus what it actually is loading?

I know I'm going in the right direction here, but still a little bit confused.

Thank you.

---

### Post by pseudonym on 2006-09-27
Ah, I see. But if you say you can already boot Ubuntu with one drive installed, and you also only have one OS installed, then grub doesn't need to know about your NTFS drives at all. 

In fact, even if you had bootable partitions on those drives it wouldn't confuse grub, because you haven't specified them in menu.lst.

Does this answer your question?

---

### Post by Cronjob on 2006-09-27
Well, I'm totally confused then... because I just tried plugging them all in again and trying to boot into linux and this is what I got:

```

Uncompressing linux... Ok booting the kernel
mounting /dev/sda1 on /root failed
mounting /root/dev on /dev/.static/dev failed
mounting /sys on /root/sys on /root/sys failed
mounting /proc on /root/proc failed
Target file system doesn't have /sbin/init

```

The drive that should be booted from is plugged into the SATA1 port on the motherboard. The other two are plugged into SATA2 and SATA3. If I unplug the other two drives, the one that should boot does so with no problem. Plug them back in -- and it won't boot . . . . :/

---

### Post by pseudonym on 2006-09-27
hmmm, that's weird. What motherboard have you got with what SATA controller?

---

### Post by Cronjob on 2006-09-27
It's an Asus A8N-SLI (though I'm not using SLI), which I believe uses an NForce4 SATA controller.

---

### Post by pseudonym on 2006-09-27
Have a look [here]("http://gentoo-wiki.com/HARDWARE_Asus_A8N-SLI"). I think this may have something to with your problem. It's a Gentoo Linux site, but they often have great howtos with general linux applicability.

---

### Post by Cronjob on 2006-09-27
Interesting. I'll go check that out. I presumed I was encountering the known bug regarding IDE throwing off the SATA drive count/hd# (even though the only IDE I have is the CDROM). It didn't occur to me that I might have something else going on.

If I come to a solution, I'll document it here. Thank you for your help.

---

### Post by Cronjob on 2006-09-27
Well, for whatever reason, I had to plug my drives into the SATA controller in the following way:

My first SATA drive went into the 3rd SATA channel.
My second SATA drive went into my 1st SATA channel.
My third SATA drive went into my 2nd SATA channel.

Boot up. Everything works fine now.

I'm not entirely sure how to fix this within linux so that I don't have to physically re-route the drives like I am doing right now, because I tried entering grub and telling it (during the boot process) to use hd0,0 hd0,1, hd1,0, hd1,1 and so on and so on -- with the only results being either "unable to read partition" or "drive/partition not found".

Anyway. Gah. :)

---

### Post by pseudonym on 2006-09-28
Glad you got it working. :)

It's a shame that Gentoo person didn't elaborate more on the issue. But I think you might also have to edit /boot/grub/device.map to complete the workaround for this grub bug. I got that from [here]("http://www.mail-archive.com/bug-grub@gnu.org/msg10264.html").

---

### Post by egd on 2006-10-14
> **Cronjob said:**
> Well, for whatever reason, I had to plug my drives into the SATA controller in the following way:

My first SATA drive went into the 3rd SATA channel.
My second SATA drive went into my 1st SATA channel.
My third SATA drive went into my 2nd SATA channel.

Boot up. Everything works fine now.

I'm not entirely sure how to fix this within linux so that I don't have to physically re-route the drives like I am doing right now, because I tried entering grub and telling it (during the boot process) to use hd0,0 hd0,1, hd1,0, hd1,1 and so on and so on -- with the only results being either "unable to read partition" or "drive/partition not found".

Anyway. Gah. :)


I'm having a similar problem, which I've been able to solve, at least partially - I can get Linux to boot, but I've lost X.

 When I installed Dapper, I had four SATAII drives installed on SATA1 through SATA4 respectively.  In my case my PC is configured to boot off SATA1 on the motherboard.  The Dapper install went well and I am able to see/access all drives in question.

The problem arose when I later installed a PCI SATAII controller to add additional drives.  If no drives are attached to the PCI SATAII controller Dapper boots without issue.  If I cable any drives to the PCI controller they displace SATA1 through SATA4 on the motherboard, ie where the SATA1 channel used to be /dev/sda, with two drives connected to the PCI SATAII controller,  the motherboard SATA1 channel becomes /dev/sdc.  Grub subsequently gives me the same errors you've experienced:

```
 Uncompressing linux... Ok booting the kernel
mounting /dev/sda1 on /root failed
mounting /root/dev on /dev/.static/dev failed
mounting /sys on /root/sys on /root/sys failed
mounting /proc on /root/proc failed
Target file system doesn't have /sbin/init
```My workaround in an attempt to solve this was to edit /boot/grub/menu.lst and to change references to sda1 to sdc1 and reboot.  Dapper successfully booted, however, I lost X.

I then returned menu.lst to its original state and edited /boot/grub/device.map to change (hd0) /dev/sda to (hd0) /dev/sdc.  This left me once again with the errors outlined above.

I suppose a simple answer would be to recable my drives, swopping /dev/sda and /dev/sdc, but this shouldn't be necessary.

I'm guessing X has a similar hard coded reference to a library location somewhere.  In any event, I'm very surprised that Linux/Ubuntu does not handle this sort of scenario automatically - adding and removing drives is a basic necessity these days.  Perhaps it does and we just don't know where/how to invoke it?

---

