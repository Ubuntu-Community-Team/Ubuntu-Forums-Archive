---
title: "Installation problems"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by Tytt on 2014-02-16
Hi,

I decided to install Ubuntu 12.04 or 13.10 onto my laptop EeePC Seashell series. Previously the computer had Windows Starter.

Procedures so far: 

- The laptop doesn't have a CD drive, so I loaded an iso image onto a thumbdrive.
- I managed to install Ubuntu on the computer, but unfortunately I then found that the system was dependent on the thumb drive (whenever I removed it the system crashed).
- I tried to follow the instructions on [http://askubuntu.com/questions/125494/cant-boot-without-flash-drive-plugged-in](http://askubuntu.com/questions/125494/cant-boot-without-flash-drive-plugged-in), which are to try: sudo grub-install /dev/sda in the terminal. I couldn't get this to work.
- So I tried to install Ubuntu a second time. This time I started by making a new iso image using the Unetbootin programme.
- Installation this second time (and several subsequent tries) were unsuccessful. After chosing the option to erase the previous Ubuntu and reinstall the system, installation stalls on "Installing the 'grub2' package"
- After several tries, the computer now refuses to accept the thumbdrive as a bootable device.

Any ideas how I can move forward? (I'm using a MacBook Pro and Unetbootin to make the iso image.)

Many thanks for any help you can offer!

-Tytt

[Also posted here: [http://ubuntuforums.org/showthread.php?t=2205862]](http://ubuntuforums.org/showthread.php?t=2205862])

---

### Post by varunendra on 2014-02-16
The netbook's capability to boot from USB is independent of the state of the hard disk or the OS/boot-loader on it. So if it refuses to boot from the USB, the problem is in the USB drive and the first thing you need is to either make it bootable again, or get another one that lets you boot.

In order to install of fix anything on the netbook we do need a bootable device that it can boot from.

Try reformatting the current USB to FAT(16 or 32, whichever works) on your MacBook, and use the same method to make it Live bootable that you used the first time.

---

### Post by buzzingrobot on 2014-02-17
The instructions here ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)) always worked well for me creating a USB on OS X.

---

### Post by Tytt on 2014-02-17
Thanks Varunendra & buzzingrobot!

---

### Post by Tytt on 2014-02-17
Worked through the USB page you mentioned above. 

When I insert the USB with the .img file on it into the PC, the PC does not recognise it. (Is this .img in order to make a USB run on a Mac only?)

Any idea what I'm doing wrong?

The windows system has been wiped out the PC, there should be some of the ubuntu files left on it. What sort of iso should I be using?

---

### Post by buzzingrobot on 2014-02-17
Try removing the '~' in the "of" section. Right now, you're pointing it at a nonexistent /dev directory inside your home folder.

---

### Post by buzzingrobot on 2014-02-17
> **Tytt said:**
> Worked through the USB page you mentioned above. 

When I insert the USB with the .img file on it into the PC, the PC does not recognise it. (Is this .img in order to make a USB run on a Mac only?).

Just to be sure, you inserted the USB, rebooted, and either interrupted the boot to tell the machine to boot off the USB, or had already reset the BIOS to boot first off the USB?

It isn't Mac-specific.  

USB's can be quirky in my experience. If it won't boot, run through the drill again from scratch.  Then, after "dd" completes and the terminal prompt returns, execute "sync".  That flushes any data left in buffers to the drives, including the USB. I've found this necessary in Linux. It may take a minute or more to complete.

---

