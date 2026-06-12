---
title: "Need to make bootable USB drive from ISO"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by rishabh_destiny on 2010-05-22
Hi There
I have ubuntu 10.04 installed on my machine but I want to have Windows 7 on dual boot. The problem is, my DVD ROM is not working right and I can't boot through the Windows 7 DVD.

Is it possible, to create a bootable USB drive from the Windows ISO image in Ubuntu? It's done in windows using the "diskpart" utility of MS DOS

And just for reference, just copying the contents of ISO to the USB, DOES NOT make it bootable.

---

### Post by darkod on 2010-05-22
As far as I know, you can't do it in ubuntu. Not without tweaking around.

Because just copying the files doesn't make it bootable, you need to run a command, but that command works only in windows. Otherwise it's on the win7 dvd.

PS. However, if you are experienced with grub, you could put grub1/grub2 on the usb stick (not related to your ubuntu install) and all you need is to tell grub to call /bootmgr file on the stick. When you copy the files over, you'll notice the /bootmgr file on the root of the stick.

---

### Post by wilee-nilee on 2010-05-22
This has to be run in a windows environment and it has to be a legitamte ISO of windows 7 to work.
[http://download.cnet.com/Windows-7-USB-DVD-Download-Tool/3000-18513_4-10972600.html](http://download.cnet.com/Windows-7-USB-DVD-Download-Tool/3000-18513_4-10972600.html)

You can actually get this free form MS and should have been part of any legitimate ISO download.

---

### Post by ronparent on 2010-05-22
I beleive it is simply a right key option in win 7 to copy the iso to a cd/dvd/usb drive location and make it a bootable copy with all of the individual files.

---

### Post by wilee-nilee on 2010-05-22
> **ronparent said:**
> I beleive it is simply a right key option in win 7 to copy the iso to a cd/dvd/usb drive location and make it a bootable copy with all of the individual files.

You can burn it to a DVD but not just put it on a thumb without the windows thumb loader. There may be some hacks on the web to do this but you can't just copy it over via  a right click. MS has made it very difficult to load any windows distro on a thumb for a install.

I just found this which are instructions on how to rip the DVD to a thumb it might work with a ISO. This would be a option if the ISO doesn't qualify as authentic with the MS thumb loader.
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)
There is also a link to the MS tool in the link.

---

### Post by darkod on 2010-05-22
> **wilee-nilee said:**
> You can burn it to a DVD but not just put it on a thumb without the windows thumb loader. There may be some hacks on the web to do this but you can't just copy it over via  a right click. MS has made it very difficult to load any windows distro on a thumb for a install.

I just found this which are instructions on how to rip the DVD to a thumb it might work with a ISO. This would be a option if the ISO doesn't qualify as authentic with the MS thumb loader.
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)
There is also a link to the MS tool in the link.

Actually, I was surprised how easy they made it. In the boot folder on the dvd there is the bootsect.exe file if I remember correctly.

You just need to run command prompt as administrator and do something like:

bootsect.exe /nt60 X:

where X: is your stick letter. That creates the boot sector. After that is just copying the files.

But all of this applies for windows. There are probably ways to do it in ubuntu, only not that easy.

Google around for "booting ISO file", etc. There are guides around.

---

### Post by wilee-nilee on 2010-05-22
> **darkod said:**
> Actually, I was surprised how easy they made it. In the boot folder on the dvd there is the bootsect.exe file if I remember correctly.

You just need to run command prompt as administrator and do something like:

bootsect.exe /nt60 X:

where X: is your stick letter. That creates the boot sector. After that is just copying the files.

But all of this applies for windows. There are probably ways to do it in ubuntu, only not that easy.

Google around for "booting ISO file", etc. There are guides around.

When I downloaded the W7 purchase it was a upgrade that could be run live from XP but had to be a fresh install, this had the .exe file for installing. I also got the ISO that came with the thumbloader, I then purchased the DVD, and was sent 2 for the price of one.

I was just able to load a XP home slipped-streamed sp3 onto a thumb with the winloader in my last link. The XP ISO is from the manufacturer of my computer but this was the first time I got it to load and actually boot like a install, I didn't install as I have the OEM in the computer as of now. 

I used the XP ISO burned to a cd to load the thumb though, winload couldn't see the ISO on XP's desktop, and I have tried in the past to load with the ISO and couldn't get it to load it to boot for a install, with this device.

---

