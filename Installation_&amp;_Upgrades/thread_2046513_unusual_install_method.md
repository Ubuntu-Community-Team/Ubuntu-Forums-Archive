---
title: "unusual install method"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by BigJonMX on 2012-08-23
Can some point me in the right direction, im stuck :(
 
I have connected a HardDrive to an old pc, via a usb cable. This pc boots ubuntu cd-rom and can start installation.
But the HD is going to be put back into a laptop. (at the moment, ubuntu wont install onto usb connected hd ?!)
 
With Windows its easy: format the HD so its dos bootable, and copy windows onto it. Stick HD back into laptop, boot, install windows.
 
How can i get ubuntu onto the laptop.
(laptop has no cdrom, no usb, no network boot).
 
THanks.

---

### Post by oldfred on 2012-08-23
Welcome to the forums.

You can just do the full install to the drive. Ubuntu does not restrict you to only installing to an internal drive. Just do not install any proprietary drivers as it may then install the wrong ones particularly video.

If only hard drive connected it will install grub correctly, but if a second drive you want to be sure to install the grub2 boot loader to the external. You only get that option with manual install or Something Else.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by BigJonMX on 2012-08-31
thanks for the reply, but, i only have one drive. The installation proceedure only seems to continue if i choose usb drive from the list, and when its all finished and i put the drive into the laptop (using ide cable) it just wont boot. black screen with flashing cursor after posting.

---

### Post by Austin Texas on 2012-08-31
How much ram does the old PC have?

---

### Post by oldfred on 2012-08-31
And what video do you have.

---

