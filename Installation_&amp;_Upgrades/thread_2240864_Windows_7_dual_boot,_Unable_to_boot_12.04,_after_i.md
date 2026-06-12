---
title: "Windows 7 dual boot, Unable to boot 12.04, after installing a wrong package..."
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by tmshu1 on 2014-08-22
So I start my computer, it gets to the GRUB screen, I select the Ubuntu 12.04 option, and then the purple screen with the Ubuntu logo pops up and it says "the disk drive for /dev/mapper/cryptswap1 is not ready yet or not present". Not sure where to go from here, seems like something related to my encrypted user's directory.

So I created a bootable Ubuntu USB with Unetbootin, booted into ubuntu. Then I follow the instructions at [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info). Here's my boot-info url: [http://paste.ubuntu.com/8116958/](http://paste.ubuntu.com/8116958/)

Before, Ubuntu 12.04 was working fine, I think the cause was because I manually installed the libnl-3-200:i386 package when my Ubuntu is 64 bit (oops), and that caused somethings to mess up... I'm a complete noob. :oops: Explanations of what's happening, in addition to how I can fix it, would be wonderful--I like learning! :) 

Thank you!

---

### Post by oldfred on 2014-08-22
I do not know encryption.

But you show sda8 as swap and blkid does not show any UUID for sda8.
But your fstab entry shows a UUID to boot the encrypted swap. And of course if that is sda8 the UUID now does not exist.

Not sure how a partition can lose a UUID, did you reformat it? So then it lost UUID and encrypted settings?

And I do not know how to recreate an encrypted swap.

---

