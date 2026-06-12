---
title: "How to install Ubuntu 8.10 to USB flash drive"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by warrentang on 2008-10-31
Hi 

I just wanted to use Ubuntu but there is little free disk space on my laptop with Windows XP installed. So I am trying to install Ubuntu to an USB flash drive (4GB).

After some searching I came across this "Bootable USB Maker":
[http://lifehacker.com/5070747/ubuntu-810-released-includes-bootable-usb-maker](http://lifehacker.com/5070747/ubuntu-810-released-includes-bootable-usb-maker) 

But where is it? I hope I don't need to install Ubuntu to hard disk first before I can use it...

Regards
Warren

---

### Post by cyfur01 on 2008-10-31
I think it's included with the 8.10 installation by default, so it should be on the liveCD as well. The command-line name is "usb-creator", or it's under System->Administration->Create a USB Startup Disk.

---

### Post by Partyboi2 on 2008-10-31
You might find it on the ubuntu live cd under System>Admin>Create a usb startup disk,  without having to install ubuntu.

---

### Post by freeballer on 2008-10-31
I have yet to use the command line so not sure, but the usb installer IS NOT included in xubuntu using livecd. I've looked several times and rebooted.. Seems strange that one flavor would have it and not the other, I'll see if also included in a mirror perhaps. Would kinda be nice as well as having this a tool from autostart (windows) to create the media...

So far thou, v8.10 has been a total pain to get on usb... Maybee is just me, but I'm done bit**in. G'night

---

### Post by GregMcn on 2008-10-31
Its not just you.I cant install it either using the command line of even under admin.

Pain

---

### Post by warrentang on 2008-10-31
Hi

Thank you guys. Just as you said, the USB Maker can be found when I boot with the install CD (which contains Live CD? not sure about the concepts...).

I managed to install Ubuntu to the USB flash drive, but it turned out to be quite unstable. The system hanged frequently. Booting from Live CD has similar problems. Besides, the brightness of the screen was reset at times (Fedora installed in USB drive has the same problem).

Later I decided to install Ubuntu to hard disk. After several hours of backing up files, I started the installation and it liked a breeze. I created a dual boot system with Fedora before, but Ubuntu makes it much more easier! 

Finally I am writing in Ubuntu. That's my experience installing Ubuntu 8.10. Still much to learn but I feel comfortable when there are so many people willing to help. Thanks again. 

Regards
Warren

---

### Post by C.S.Cameron on 2008-11-01
If you are frustrated with persistent type installs to USB, try a full install to flash drive.
Temporarily disable your internal HDD in BIOS and install from Live CD to your flash drive just like to hard drive.

---

### Post by warrentang on 2008-11-02
Thanks C.S.Cameron, that's interesting. But my laptop seems to have a hardware incompatibility with Ubuntu. No matter how I install it, it hangs at times and I can only move the mouse but nothing else. The hard reset is not what I can accept. 

After several times I guess it might be related to WiFi. For the hangs usually happens when I am accessing the internet, for example when I use Instant Messager, or Firefox. I don't know how I can deal with it for now.

---

### Post by gyrene2083 on 2008-11-06
I have a quick question for you C.S.Cameron, I installed 8.10 onto the thumb drive via the Live CD. Now when I boot up my computer from the usb, it comes up with the Live CD menu, the one that asks if you want to run ubuntu from cd or install onto the hard-drive, is that right? 

Reason I ask is that I was under the impression that installing the OS to the thumb drive, it would respond similar as to setting it up on a hard drive. Or did I miss something when I set it up on the thumbdrive. 

Any help you or anyone can provide would be grateful. I'm in a real jam, I'm trying to convince my friend that Linux is way better than W....., I don't even want to finish that word.  So I'm counting on the forum for help. Thanks.

---

### Post by C.S.Cameron on 2008-11-07
Using the USB installer in 8.10, (usb-creator), makes a bootable copy of the Live CD and provides a couple of files for storing stuff, (casper-rw and home-rw).

By Full install I meant insert CD, insert flash drive, start computer.
At first screen after language pick "Install Ubuntu" then complete the setup as if installing to internal drive.
(Most modern computers just see a flash drive as another HDD).

I suggest disabling your internal drive so that you don't accidentally load grub to it.

This method will give you a thumb drive that acts just like a normal install, you can update, install restricted drivers, etc.

---

### Post by josel777 on 2008-11-09
Try this:

[http://sourceforge.net/projects/unetbootin/]("http://sourceforge.net/projects/unetbootin/")

---

