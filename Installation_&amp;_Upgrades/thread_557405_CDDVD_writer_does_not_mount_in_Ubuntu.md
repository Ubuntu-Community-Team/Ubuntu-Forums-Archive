---
title: "CD/DVD writer does not mount in Ubuntu"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by sunshine135 on 2007-09-22
I have had Ubuntu Feisty 7.04 installed on my Dell XPS M1330 for about a week now. I realized the other day that my DVD/ CD RW was not mounted and could not be found. The last line of my fstab output is as follows:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

so, I tried to mount the CDROM:

[COLOR="Red"]~$ sudo mount cdrom[/COLOR]

and received the following output:
[COLOR="Red"]
mount: can't find cdrom in /etc/fstab or /etc/mtab[/COLOR]

Obviously, the CD/DVD worked, because I booted off the live CD for the install. To my knowledge it has never worked. I tried the XPSM1330 install page and no one else seems to have had the problem. I also tried this thread: [http://ubuntuforums.org/showthread.php?t=339733](http://ubuntuforums.org/showthread.php?t=339733) but that guy doesn't seem to have had much luck either. Can anyone assist?

One last thing- I dual boot with Vista and the drive works without issue.

Thanks

---

### Post by Pumalite on 2007-09-22
Install k3b and see if it detects it.

---

### Post by sunshine135 on 2007-09-22
This is what k3b said:

No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation.

What next?

---

### Post by sunshine135 on 2007-09-22
I thought posting this might also help:


mtab output:

/dev/sda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda2 /media/sda2 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda3 /media/sda3 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda5 /media/sda5 vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

### Post by scxtt on 2007-09-22
**sudo mount cdrom** won't accomplish anything - you'd need to do either **sudo mount /dev/hda /media/cdrom0** or **sudo mount /media/cdrom0** ...

what's the output of:

ls -l /dev | grep cdrom

---

### Post by sunshine135 on 2007-09-22
$ sudo mount /dev/hda /media/cdrom0
mount: special device /dev/hda does not exist


$ sudo mount /media/cdrom0
mount: special device /dev/hda does not exist

ls -l /dev | grep cdrom

This simply returns the $

---

### Post by scxtt on 2007-09-22
no idea why the install wouldn't create the /dev/cdrom block device on install ... you should have something like:
```
:> ls -l /dev | grep rom
lrwxrwxrwx 1 root root           3 Sep  8 01:51 cdrom -> hda
brw-rw---- 1 root cdrom     3,   0 Sep  8 01:51 hda
```you should be able to create this using **mknod** - but i find it very strange that wasn't done on install - never seen that myself ...

---

### Post by sunshine135 on 2007-09-22
Can you be more specific about the "mknod" command? I am willing to try it, but I am a bit of a noob .

---

### Post by Pumalite on 2007-09-22
CD-DVD has to be set first right in BIOS for Ubuntu to recognize it,
In some BIOS>IDE Configuration>Set to 'Enhanced Support for PATA+SATA'
If no such support, then: set CD-DVD drive to 2nd Master and to 'Auto' in BIOS

---

### Post by sunshine135 on 2007-09-22
Unfortunately, this is a laptop, so the HDD configuration and BIOS options are pretty well static. This is also a newer laptop type. The only configurable option for the SATA drives is AHCI or ATA for operations. Mine is set to AHCI which I understand is more desirable. If this is really what needs to be changed I may be out of luck until support for this laptop is supported.

Any "manual hacks" or "poison pills" I might be able to try?

---

### Post by Pumalite on 2007-09-22
AHCI works for a lot of people. I guess you are out of luck. If you don't depend on the OS for your living you might want to try Gutsy Tribe 5, I'm writing to you from it. It's in testing. Stable comes out in October. Recognizes more, newer hardware, more flexible,etc.

---

### Post by sunshine135 on 2007-09-22
Well thank you for your suggestions anyway. I am very impressed with how far Linux platforms have come. I'm love the ease of obtaining new programs, and actually see little need of using a CD any way at this point. I am surprised at really what little tweaking was needed to make this work (outside of the manual install of the video driver and a slight sound driver)- even on this new equipment.

I will play with Feisty for now, and wait for Gutsy to come into full release.

Thanks Again!

---

### Post by scxtt on 2007-09-22
> **sunshine135 said:**
> Can you be more specific about the "mknod" command? I am willing to try it, but I am a bit of a noob .you'd use it like the following:
[indent]**sudo mknod /dev/hda b 3 0**[/indent]
here's an example: [http://www.faqs.org/docs/linux_admin/x797.html](http://www.faqs.org/docs/linux_admin/x797.html) ... not exactly the same, since you want a block (b) device ... might not make any difference if there's some larger "issue" - can't hurt tho ... also, not sure if you'd use "3 0" or something else ... i think the "major" and "minor" codes are reserved for specific devices, but since my example was for an /dev/hda dvdrom it might "just work" ...

---

### Post by CTPAHHbIN on 2007-09-24
[https://answers.launchpad.net/ubuntu/+question/10747](https://answers.launchpad.net/ubuntu/+question/10747)

adding

libata
ata_piix
piix

to the bottom of the file /etc/modules and reboot.

worked for me. (DELL Latitude D630)

---

### Post by sunshine135 on 2007-09-27
> **CTPAHHbIN said:**
> [https://answers.launchpad.net/ubuntu/+question/10747](https://answers.launchpad.net/ubuntu/+question/10747)

adding

libata
ata_piix
piix

to the bottom of the file /etc/modules and reboot.

worked for me. (DELL Latitude D630)

Perfect.....  You solved my problem. This worked perfectly. I don't know why it works, but it does. Thank you!!!

---

