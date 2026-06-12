---
title: "How to get the boot menu using a Startup Disk Creator's Liveusb."
date: 2015-10-09
forum: Installation &amp; Upgrades
---

### Post by hey2 on 2015-10-09
Hi.

I'm trying to diagnose a problem that i have with my computer.

Someone suggested that it might be my disk.

I thought that "check your disk for defects" would do the trick, but apparently it only checks the liveusb for errors.

The problem is that it found 1 error in one file.

Since i don't have Windows any more to use pendrivelinux, how can i get this boot menu when i create a liveusb using the startup disk creator?

When i boot, the only thing i see is a keyboard and a "little man". Sorry for the weird description.

Thanks.

---

### Post by yancek on 2015-10-09
Does the flash drive you are referring to have a Live Ubuntu on it?  If so, you can boot it and run a filesystem check on the Linux partition(s).  The link below gives a brief explanation and shows an example.  Needs to be run as root, use sudo.  This is only for a Linux filesystem which is what you have, correct?

[https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

---

### Post by hey2 on 2015-10-09
> **yancek said:**
> Does the flash drive you are referring to have a Live Ubuntu on it?  If so, you can boot it and run a filesystem check on the Linux partition(s).  The link below gives a brief explanation and shows an example.  Needs to be run as root, use sudo.  This is only for a Linux filesystem which is what you have, correct?

[https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)


Hi.

Thank you very much for trying to help me.

I didn't explained my issue very well.

I'm trying to diagnose this problem: [URL="http://ubuntuforums.org/showthread.php?t=2297918"]http://ubuntuforums.org/showthread.php?t=2297918
[/URL]
After using the "check your disk for defects", i proceeded to use the test in the Disks application. I ran short, extended and the other one and everything seems ok. So the problem shoudn't be anything related with the disk.

The thing is that while running "check your disk for defects", it detected one error in a file. So apparently the live usb have one error.

I wanted to create another live usb to see if it also had an error, but when i create a liveusb using the startup disk creator i can't access the boot menu (the one where you can test the memory, the disk, try ubuntu, etc...).

Once again thank you very much.

---

### Post by efflandt on 2015-10-09
When you create a bootable live/install Ubuntu iso on USB using Startup Disk Creator, you get to the menu by pressing any key when you boot it and see what looks like keyboard/mouse at bottom of purple screen. Otherwise it continues on to the gui where it asks if you want to "Try Ubuntu" or install.

---

### Post by sudodus on 2015-10-10
> **hey2 said:**
> ...
The thing is that while running "check your disk for defects", it detected one error in a file. So apparently the live usb have one error.
...

One error is one error too much.

Have you still got the Ubuntu iso file? (from which you made the current boot drive, a USB drive if I understand correctly?)

In that case you can check it with ***md5sum***, that it matches the listed string at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you have no good iso file available, please download one again and check it with md5sum.

-o-

In order to make it easier for us to help, please tell us

1. Which version of Ubuntu are you trying to use?

2. and please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

-o-

If the Startup Disk Creator works well for you, fine. Otherwise you can try another linux tool to create a USB boot drive, for example [mkusb](https://help.ubuntu.com/community/mkusb).

---

### Post by hey2 on 2015-10-12
Thank you all for your responses and your time.

The solution was the [**[COLOR=#000000]efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632")'s post.

It's embarrassing how easy it was.

---

### Post by hey2 on 2015-10-12
> **sudodus said:**
> One error is one error too much.

Have you still got the Ubuntu iso file? (from which you made the current boot drive, a USB drive if I understand correctly?)

In that case you can check it with ***md5sum***, that it matches the listed string at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you have no good iso file available, please download one again and check it with md5sum.

-o-

In order to make it easier for us to help, please tell us

1. Which version of Ubuntu are you trying to use?

2. and please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

-o-

If the Startup Disk Creator works well for you, fine. Otherwise you can try another linux tool to create a USB boot drive, for example [mkusb]("https://help.ubuntu.com/community/mkusb").

Thank you very much for your detailed post.

I made another bootable usb, but this time on startup disk creator and it gave me no errors on the test.

I thought it was because i used the pendrivelinux program, but when i tried the same on 15.04 it also gave me one error.

I had to use startup disk creator on 14.04 to get a bootable usb without any errors.

Thank you once again.

---

