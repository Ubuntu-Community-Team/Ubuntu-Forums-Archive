---
title: "Newbie Ubuntu install issues on Live USB"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by DaveBilling on 2012-03-22
Hi there

I installed Ubuntu 11.10 onto a USB stick, and it works well on the whole.  However, I would like a permanent installation on my USB that I can boot whenever I want.  At the moment, everytime I boot from the USB it comes up with the install menu offering me two options - whether to "try it" or install it to my hard drive.  I don't want to install it alongside Windows 7 at this point in time.  I want to run it from the USB for the time being.  I installed it using a program called LiLi USB creator.  How do I install it 'permanently' on the USB drive without having to click on the "try" option, and thus, retain all my settings?

Also, the first time I ran it, it mounted my external hard drive fine.  Every time after that, it came up with a code 21 error.  I'll need help with this one as well.

As you can tell, I'm a newbie to Ubuntu and I haven't used Linux in donkey's years.  Any help with this would be appreciated, and the sooner the better.  Thanks very much.

---

### Post by cortman on 2012-03-22
Hi, welcome to the forums and Ubuntu!

Here's a whole [wiki page]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") on creating persistent USB installations.

---

### Post by DaveBilling on 2012-03-22
Thanks, I've already got it up and running.  I can save data on it, no problem, but not system settings.  So every time I reboot it starts from scratch, although programs and data that I've installed are still there.  I created 1.3gb persistence data using the LiLi utility, but every time I plug it in it asks whether I want to try it or install it onto the hard disk.  I followed everything to the letter.

---

### Post by cortman on 2012-03-22
> **DaveBilling said:**
> Thanks, I've already got it up and running.  I can save data on it, no problem, but not system settings.  So every time I reboot it starts from scratch, although programs and data that I've installed are still there.  I created 1.3gb persistence data using the LiLi utility, but every time I plug it in it asks whether I want to try it or install it onto the hard disk.  I followed everything to the letter.

Sorry, I misread your post! What system settings in particular are you wanting to save?

---

### Post by darkod on 2012-03-22
There is a difference between the bootable installation usb stick with persistance, and installing onto a usb stick/hdd as a target.

What you seem to want is to install it onto the usb stick so it runs from there, not being a installation media.

You can do this but you will need another usb stick to boot from and start the installation, or a cd with ubuntu. During the install simply specify the target usb stick as a destination to install and that's it. Make sure you select the bootloader to go to the same disk (stick). For this it's better to use the manual install method.

I don't know if it can install on 4GB stick, I would use 8GB as minimum to give it a little bit of space.

---

### Post by DaveBilling on 2012-03-22
Ok, I'll try that.

---

### Post by DaveBilling on 2012-03-22
I've pretty much given up on the USB.  I'm coming up with errors every time I reboot Ubuntu from it.  I'm contemplating installing it onto the hard drive alongside Windows 7, but I'm less than confident in doing so.  Being a laptop with Win 7 preinstalled, how would this affect the factory installation as well as the Windows recovery partition?

---

### Post by cortman on 2012-03-22
> **DaveBilling said:**
> I've pretty much given up on the USB.  I'm coming up with errors every time I reboot Ubuntu from it.  I'm contemplating installing it onto the hard drive alongside Windows 7, but I'm less than confident in doing so.  Being a laptop with Win 7 preinstalled, how would this affect the factory installation as well as the Windows recovery partition?

You can leave the Windows partitions safe and secure when you install. You should shrink the Windows partition using the windows tools. Open up about 40-50 GB of unallocated space for Ubuntu, if you can spare that much. Then you can select to install it in that empty space when you boot from the live CD or USB.

---

### Post by DaveBilling on 2012-03-22
I just installed Ubuntu inside Windows 7.  There wasn't an option to install it alongside Windows 7, unfortunately.  Hopefully it will work well enough.

---

### Post by mastablasta on 2012-03-23
the option appears if you have free unformated disk space available (i.e. empty disk partition).
 
by inside do you mean wubi?
 
Or virtualbox?: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
Virtual box is really good, easy and the least messy way to try out the OS.

---

### Post by DaveBilling on 2012-03-23
Yep, through wubi.  I tried Virtualbox, but everytime I ran Ubuntu it froze up and stopped responding.  I'm quite happy with the setup I have now.

---

### Post by darkod on 2012-03-23
> **DaveBilling said:**
> I just installed Ubuntu inside Windows 7.  There wasn't an option to install it alongside Windows 7, unfortunately.  Hopefully it will work well enough.

Also, if at the moment you have 4 primary partitions used, it doesn't give you the option because it can't create a fifth.

Wubi was never developed to be a long term install. It's only a question of time when you will start seeing problems and when it will break. During update, upgrade, etc.

In your place, if you want to continue using ubuntu, I would start planning your hdd layout to make that happen. For example, HP ships laptops with HP_TOOLS and Restore partition. They are both useless.
The Restore partition usually restores the factory layout which means deleting all your programs and data, even if your problem was only few corrupted windows files. I can't see any benefit of using it, except before selling the laptop if you want to return it to factory layout.
But even if you want to keep the restore option, there is a better way. The software on the laptop should allow you to create a set of restore DVDs which have the same purpose. You can boot with them and do the restore. After creating them, you can delete that partition which will allow you installing a proper dual boot.
Not to mention that you will also be able to use the 15-20GB that the restore partition is taking right now. At the moment that space is just sitting useless.

---

