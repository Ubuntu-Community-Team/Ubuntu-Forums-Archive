---
title: "Uninstalling windows"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by golfingfool on 2011-09-30
I have a new computer upon which I installed windows 7 and product key was bad.  The vendor would not exchange and I will not pay again so I now have ubuntu 11.04 disk.  I want to uninstall windows 7 and put in ubuntu.  What would be the easiest and best way to get this done?

---

### Post by bfmetcalf on 2011-09-30
When installing Ubuntu you put the CD in and it will bring up the installer.  You will have different options to choose from.  I would recommend trying it on the live CD to make sure it will work correctly with your system.  If all is good you will want to start the install and choose the option to install Ubuntu (not install along side other OS).  It will format the entire drive and will erase Windows in the process.

---

### Post by golfingfool on 2011-09-30
also part of the problem is windows 7 main window is up and wanting a password which has expired since it has been more than 30 days.  When I install ubuntu cd there is no installer.  What else should I try?  Thanks.

---

### Post by Paddy Landau on 2011-09-30
Sorry about your vendor!

Have you booted from the Live CD? You don't run Ubuntu from Windows -- it is an entirely different operating system (OS), just as Mac is.

Create a Live CD (on either a CD or a USB stick) -- you say you already have one. Shut down your computer. Plug in the CD (or USB stick). Start your computer and boot from the CD (or USB stick).

Try out Ubuntu to check whether or not all the basics work -- Internet, video (there is a short sample on the Live CD), webcam if you have one, microphone, speakers. (It will be slow because it's running from the CD or USB stick.)

If everything works, go ahead and install.

---

### Post by LinuxFan999 on 2011-09-30
> **golfingfool said:**
> also part of the problem is windows 7 main window is up and wanting a password which has expired since it has been more than 30 days.  When I install ubuntu cd there is no installer.  What else should I try?  Thanks.
You might have a bad CD or ISO image. Re-download Ubuntu and burn another CD at a slower speed.

---

### Post by Hakunka-Matata on 2011-09-30
Once you're up and running in ubuntu you can probably find a program somewhere to suss the Product key on your Win7 install disc(s).  Then you run a dual boot..

---

### Post by viperdvman on 2011-09-30
As long as you have some kind of internet connection (*wired ethernet is best when installing as not all internal WiFi adapters are supported out of the box*), you can do a complete install with no problems. Just download the Ubuntu 11.04 image from the Ubuntu website (do it quick, 'cause 11.10 is about to be released in October), and burn the iso image to a CD, or download UNetbootin for Windows and use it to put the iso image on a USB drive.

Once you have that done, you can 1) For CD, just put it in and reboot. Almost every PC BIOS boots from CD first. -or- 2) For USB drive, go into your BIOS and make sure your computer boots from the USB before booting from the hard drive.... and try out Ubuntu without installing.

If you like how it works, there's usually an icon on the desktop, launcher, or both, for installing Ubuntu to your hard drive. When you install it, **pay very close attention** to the partitioning section. A lot of laptops/subnotebooks/netbooks have a hidden partition used as the computer's Windows Restore partition. Unless you want absolutely nothing to do with Windows anymore and don't care to ever have that Windows Restore, **do not touch** that partition.

There is an easy option of installing Ubuntu in place of Windows, but I don't know what that does to the Restore Partitions of some Windows computers. Or when you choose the more advanced partitioning method, just click on the partition that contains the said Windows OS with the bad key and click the option to have that partition reformatted, and then install Ubuntu to that partition (remember to set that partition's mount point as **/** ). There's also the option for where you want to install the GRUB bootloader (what boots your Ubuntu OS). You can either install it to the MBR, on the partition your Ubuntu is being installed on, or a completely different boot partition altogether. Since you're wanting to replace Windows altogether, it's best to have Ubuntu put the bootloader in the MBR (thus overwriting the Windows bootloader). The rest is just setting up your regular install stuff (i.e. keyboard, networking, video resolutions, username and password, etc.). And voila, you now have Ubuntu.

That is my little "Installing Ubuntu 101"

---

### Post by halibaitor on 2011-09-30
> **golfingfool said:**
> I have a new computer upon which I installed windows 7 and product key was bad.  The vendor would not exchange and I will not pay again so I now have ubuntu 11.04 disk.  I want to uninstall windows 7 and put in ubuntu.  What would be the easiest and best way to get this done?

I've seen this story before, and in all cases I've seen, the vendor was selling bootleg copies of Windows.  :(

Assuming you have a receipt, take the guy to small claims court and get your money back.  Then tell MS about this guy.  (He needs all the help he can get. :lolflag:)

---

### Post by golfingfool on 2011-10-03
when installing ubuntu i get this:


kernel_thread_helper+0*6/0*10  on the same line I get 0.333030] [<c100367e>] just right before the kernel portion on the same line.

---

