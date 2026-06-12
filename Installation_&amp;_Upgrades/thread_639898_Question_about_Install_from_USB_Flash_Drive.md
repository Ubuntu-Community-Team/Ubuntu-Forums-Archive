---
title: "Question about Install from USB Flash Drive"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by beret9987 on 2007-12-13
Hi

I have an old laptop that doesn't have an optical drive but it has USB ports that it can boot off of so I figured I could just take a Ubuntu live CD and throw it on a flash drive and install it off of that. The only thing is that I also want to be able to use this flash drive as a portable OS, like something I can carry around and it has all my settings. I've seen directions on how to do things like this but I was just wondering if it was possible to have an install of Ubuntu on my flash drive and be able to install from it to another computer. Thanks very much!

---

### Post by logos34 on 2007-12-13
> an old laptop that doesn't have an optical drive but it has USB ports that it can boot off of

are you sure the bios supports usb boot? better double check

Here are some of my bookmarks:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://ubuntuforums.org/showthread.php?t=476302](http://ubuntuforums.org/showthread.php?t=476302)
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)
[http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/)
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Good luck

---

### Post by ResumeMan on 2007-12-21
> **logos34 said:**
> are you sure the bios supports usb boot? better double check



When you say "better double check" do you mean something other than just booting, entering the BIOS setup, and seeing if there's a "USB" option?

I just got a Dell laptop w/no CD drive. I tried this [howto]("http://ubuntuforums.org/showthread.php?t=427540&highlight=unetbootin"), and it failed -- and now I can't boot into anything, as I think that Linux overwrote Windows but was corrupted.

So now I'd like to try to install using a USB flash drive. I do [I]not[I] need to have the install allow configuration changes, etc., since all I want to do is install the OS on the hard drive via a flash drive.

The BIOS does indeed have an option for "USB device." But when I put the USB stick in with the BIOS set to boot from USB  at first priority, nothing happens. Screen just stays dark.

I have tried a couple of options, from just sticking the .iso image on the stick to several of the tutorials you linked to. 

Any ideas? I saw in one of the posts I read that some computers and USB sticks just don't play well together. Is that accurate? It could just be an unhappy marriage :P

And as I said, could it be that just because USB appears as a boot option, it really isn't?

Help would be appreciated, as I now have a nice (light! it's a small machine!) door stop.

---

### Post by logos34 on 2007-12-21
> **ResumeMan said:**
> When you say "better double check" do you mean something other than just booting, entering the BIOS setup, and seeing if there's a "USB" option?

no, I simply meant checking the Bios for that feature/option

> I just got a Dell laptop w/no CD drive. I tried this [howto]("http://ubuntuforums.org/showthread.php?t=427540&highlight=unetbootin"), and it failed -- and now I can't boot into anything, as I think that Linux overwrote Windows but was corrupted.

If it's XP you have, use the [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to restore windows bootloader to mbr.  If Vista, you're SOL.  Kidding, but I'm still not sure how you would do it without the install dvd.

To install without cdrom, I would try [this method]("https://help.ubuntu.com/community/Installation/FromWindows") next. (-->section 'Cd image approach')

---

### Post by ResumeMan on 2007-12-21
OK well the OS is XP.

I'll give the various options a shot. I wonder if there's just a problem with the flashdrive/computer combo. May need to go pick up another cheap pendrive over the holidya.

Thanks for the input.

---

### Post by ResumeMan on 2007-12-22
OK just to update:

I got super grub loader, and the computer recognized it, but I couldn't get it to boot anything. I didn't try very hard, and decided I'd try a couple other things and come back to SGD if nothing else worked.

I decided to try the [pendrive linux]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") tutorial again. I got the files on it, but got Grub error 15 when I tried to boot. I realized that I hadn't tried the lilo method to fix the master boot record. I did that, and everything seems to have worked. I've just installed Gutsy on the no-CD laptop, and as far as I can tell we're all good.

Thanks for the input.

---

