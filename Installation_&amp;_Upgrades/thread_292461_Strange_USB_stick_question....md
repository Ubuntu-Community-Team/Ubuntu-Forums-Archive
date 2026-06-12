---
title: "Strange USB stick question..."
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by PaterLucis on 2006-11-03
Alright, bear with me here. I'm on Windows. I want to make my Cruzer Micro bootable, BUT, for just one reason: I have a dead laptop that I want to install Ubuntu on. The drive works fine. 

I want to boot from the USB stick and choose Install Ubuntu. 

That should work, right?

Here's the thing: I have to install the LiveCD on my pendrive from Windows. I don't care if it's persistent. 

I'm guessing that there's no easy way to do this, and I'll have to follow the rather confusing instructions in LiveUSBPendrivePersistent.

---

### Post by subzero79 on 2006-11-03
If your drive works why don't you install it from the cd?

For what i understand in the wiki, you can also make the pendrive bootable from windows. What did you find confusing?

---

### Post by PaterLucis on 2006-11-03
I absolutely cannot install from CD. And I don't get how to edit the syslinux stuff. I don't need a persistent pendrive, that's the opposite of what I need. I need JUST the LiveCD; exactly as if I were using it via optical drive. I don't need persistence. I just need it to exist on the drive.

Essentially, I'm asking for a way to burn an ISO image to my USB key.

---

### Post by subzero79 on 2006-11-03
You need to run on livecd mode imperative?

or are you going to install ubuntu definitive?

I would recommend you that if your idea is to install ubuntu then consider another way of booting the installer. You can make your pendrive to boot the necessary installer files, then the installer retrieves the necessary packages from the internet mirrors an then installs ubuntu. This is called netboot and can be achieved with a pendrive. take a look here.

[http://doc.ubuntu.com/ubuntu/install/i386/ch04s03.html](http://doc.ubuntu.com/ubuntu/install/i386/ch04s03.html)

Also take a look at your laptop BIOS for PXE boot. That is for booting from tftp.

---

### Post by PaterLucis on 2006-11-03
No...I just want to burn an ISO to my pen drive.

That's it.

No TFTP stuff. No netboots. 

No kittens or puppies.

I want my pen drive to function exactly as a LiveCD.

---

### Post by subzero79 on 2006-11-03
Then follow the instructions. If you find it to hard to do it from windows and easy from linux, the try booting in liveCd mode in another computer (with a cd drive of course) and there you can configure your pendrive.

---

### Post by PaterLucis on 2006-11-03
I don't have another computer to do it with.

I don't know what instructions you are referring to.

And I have no idea why I can't just write the ISO image to a mass storage device.

---

### Post by subzero79 on 2006-11-03
1. No extra computer? were are you writing from then?

2. I am sure you are pointing here right?

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUSBPendrivePersistent%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUSBPendrivePersistent%29)

That's the wiki you found. What part exactly you didn't get of the wiki.

3. Because iso's are images are for cd/dvd. they won't boot from other thing different from an optical drive.

---

### Post by PaterLucis on 2006-11-03
1) This computer also doesn't have an optical drive.

2) Yes. What am I supposed to configure and how? I don't get it. 

This are the parts I don't get:

Installing Dapper or Edgy on the USB pendrive

This is the same as described in the Linux section except for accessing the downloaded image. The way to do this is to mount the iso image file and copy the files that way. You can do this with NERO or [WWW] Windows VirtualCD. You might want to do it this way if you don't want to burn a CD. 

And:

Making the pendrive bootable

Go to [WWW] [http://syslinux.zytor.com/iso.php](http://syslinux.zytor.com/iso.php) and download a copy of syslinux-3.11.zip for Windows. Extract the zip file contents and move the extracted folder to your favorite location on your hard drive.

Open WordPad and edit the file syslinux.cfg as described in the Linux section.

Open a command prompt and change directory to the location of the syslinux folder. For example, if you placed the folder on your desktop then: cd C:\Documents and Settings\(your user name)\Desktop\syslinux-3.11\win32 (by the way you DO know that command prompt has command completion just like in Linux (start entering characters and then press the TAB key to complete the entry)).

Next write the bootsectors to the flash drive by entering the following command: syslinux -f X: --> where X: is replaced by the drive letter of your USB key. Be careful to pick the correct drive letter!

---

### Post by subzero79 on 2006-11-03
If you have winrar you don't have to mount the image. Winrar can handle iso files.

syslinux is here [http://www.kernel.org/pub/linux/utils/boot/syslinux/Old/syslinux-3.11.zip](http://www.kernel.org/pub/linux/utils/boot/syslinux/Old/syslinux-3.11.zip)

then extract syslinux.zip to c:\syslinux

then start=>run=> type "cmd" ; then

cd c:\syslinux\win32
syslinux f:   (f: is the drive letter of your pendrive, you have to change it here for yours)

then open syslinux.cfg (inside the pendrive of course) and put he contents pointed in the wiki.

Hope this helps.

PD:BTW are you sure your laptop can boot from an usb stick?

---

### Post by PaterLucis on 2006-11-04
Ugh. It says I have to repartition my drive.

But I cannot find any utility with which to partition my USB stick.

*slams head against wall*](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

Also, the contents of ldlinux.sys = Garbled symbols.

Augh. And it's supposed to be syslinux.

Dammit.

---

### Post by subzero79 on 2006-11-04
Come on....please read the whole wiki from top to bottom

[http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html](http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html)

the file is SYSLINUX.CFG. Also you have to rename it from ISOLINUX.CFG to SYSLINUX.CFG.

Seriously read the whole wiki. Try to understand then execute.

---

