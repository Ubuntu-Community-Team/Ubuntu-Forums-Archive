---
title: "USB pendrive intsall upgradable?"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by ranger_cole on 2008-11-06
I installed Ubuntu 8.10  on a 2.0 Gb pendrive using the built in installer.  Can you run the update manager and save changes to the pendrive?

---

### Post by WishMaster on 2008-11-06
Try it out :-)
 
I also installed ubuntu 8.10 to usb, and I did install the updates, no problem
 
As long as you have enough free space on your usb-stick

---

### Post by timcredible on 2008-11-06
if you're talking about the usb startup disk that's created with the new menu option, no, it's just a copy of the livecd.  if you're talking about doing a normal install to a usb drive, then yes.

---

### Post by ndruu on 2008-11-06
I also used the new built in installer to put 8.10 onto an 8GB usb drive. I want a portable desktop with the ability to update the software and all that, and I thought that the new installer would give me that. Its annoying that I have to select from the install menu when I first boot, and I noticed that it boots to root without password protection, with no option to boot to a different user with password protection.

What's the "normal" install to usb drive that will give me a portable, password protected, non root-user experience from my usb drive?

---

### Post by snowpine on 2008-11-06
> **ndruu said:**
> 
What's the "normal" install to usb drive that will give me a portable, password protected, non root-user experience from my usb drive?

Install to the USB device just as you would to your hard drive, from a Live CD (or even from the Live USB you just made).

Click "Advanced" options at the last stage of the installer and make sure you install grub to your USB stick, not the hard drive! (I am paranoid about this so I physically disconnect my hard drive when installing to a USB stick.)

---

### Post by timcredible on 2008-11-06
above poster is correct on procedure.  not sure why you'd disconnect your hard drive though.  i ran a system off an external hard drive for quite a while, ran with no problems.  a friend installed 8.10 to an 8gb drive, he said it worked, but was kind of flaky, but he has a very cheap flash drive, he's going to try it with a name brand flash drive later.

---

### Post by snowpine on 2008-11-06
> **timcredible said:**
> above poster is correct on procedure.  not sure why you'd disconnect your hard drive though. 

I have read accounts of people who were not careful and installed Grub incorrectly so that they couldn't boot from their internal hard drive unless the USB stick was inserted. I am careless sometimes, so I just pull the cable on my hard drive so there's zero percent chance anything gets messed up. Probably unnecessary if you are careful. :)

---

### Post by C.S.Cameron on 2008-11-06
I have Full installed to flash drive with my hard drive plugged in ok, but accidentally installed grub to my Windows partition a couple times. Thus I could only boot Windows with my flash drive plugged in. It was a hassle finding my Windows install disk so I could run fixmbr. 

With a usb-creator made pendrive you can make separate partitions for persistence, (formatted in ext3 or reiserfs) and label them casper-rw and home-rw.
This will let you save all your stuff when you reinstall to upgrade the kernel.

If U-C made a persistent install the file casper-rw needs to be deleted.
If Discard Changes is selected, the file syslinux/text.cfg can be edited adding the word persistent thus:
  append  noprompt cdrom-detect/try-usb=true **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

---

