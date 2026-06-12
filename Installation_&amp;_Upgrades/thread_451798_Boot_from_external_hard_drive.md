---
title: "Boot from external hard drive"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by heymae on 2007-05-22
Thank you people I am dead new to Ubuntu OK....
Now...I want to install and BOOT  Ubuntu 7.04 desktop 1386, from External Hard Drive Seagate S33520 USB 2.0 Free Agent Desktop 3.5”, 320GB, 7200 RPM, 8MB Cache.
> Will you please advise how I may successfully achieve this.
Currently I have Windows XP, but it is important for me to keep Ubuntu separate from the main computer, hence my need to install and boot from an external hard drive. I hope the above is sufficient information for you...Thank you Heymae.. If necessary you could email me as well at      [email]heymae@internode.on.net[/email]

---

### Post by shamreez on 2007-05-25
1) First thing you have to do is change the booting seq of your comt to 1. CD  2. USB. 3. Laptop HDD

2) you install ubuntu using the live CD.  

3)Once you get to the last screen before install click advanced change the location for the grub loader from HD0 to HD1

3) After the install when you restart the system enter the edit mode on the grub menu and give the location of the boot sector as Hd0 from HD1.  This is because when you are installing from the live CD the C:\ resides is the primary drive (hd0), and the External HDD is more secondary (hd1). But when the computer boots from USB: Computer Boots, GRUB sees the External HDD as PRIMARY now (hd0), and the Laptop HDD as the SECONDARY (hd1)

4) Once you are inside ubuntu after the restart edit the Menu.lst file present in the mnt dir and you are done...

The grub menu shows and loads ubuntu only if your USB is plugged else it is directly to windows

Hope this helps

---

### Post by mybunche on 2007-05-25
This is part of what I given some people when they are new to linux as well just as I was. I installed 6.10 on a USB drive. This is for 6.10, 7.04 will be very similar.

I**nstalling Ubuntu 6.10      **

This is to install Ubuntu on USB hard drive. The USB hard drive will always need to be connected to a USB port off the motherboard (ie not off an extension card or USB hub) in order for the computer to boot up to either Windows XP or Ubuntu. This is because the boot up menu will be written to the USB hard drive. With the following procedure, the computer will boot to Windows XP automatically when the computer is switched on.  To choose to boot to Ubuntu, when the menu appears (or even before) press up arrow to highlight the first choice and press enter.

**Installation**
Boot up to live CD.

From top menu bar select System -  Preferences – Removable Drives and Media.
Under Removable Storage, untick the top three  ie Mount removable drives when hot-plugged, Mount removable media when inserted, Browse removable media when inserted.

Plug the USB drive into a USB port off the motherboard, not off a PCI card or USB hub. Wait for the drive to be recognised. It may not be displayed but the USB drive LED should of flashed  couple of times and the LED should be on.

Double click on the install icon.

It will ask a few questions. Enter you name, choose a username and password, select your time zone.

Choose where you want it installed. Your main hard drive and your USB hard drive should be listed. Your USB hard drive should be labelled as eg 60.0GB Fujitsu (or whatever USB drive is). Choose this one.
Important: Make sure to choose the drive labelled as SCSI and/or sda not your main hard drive hd0, otherwise it will overwrite your Windows XP.

Confirmation screen. Double check that the installation will be on your USB drive, labeled  SCSI or sda. (7.04 might labell it differently)

Installation will take take approximately 25min. Upon completion it will ask you to restart computer. Remove CD before doing so.

When boot menu appears, the top choice, the Ubuntu kernel  will be automatically selected after 10 seconds. Can change the order if you wish.

Shortly, Ubuntu will ask you for your login name and password. After a couple of minutes you should be greeted with the Ubuntu desktop.

---

### Post by trishacupra on 2007-06-01
That's interesting. I've booted from an external hard drive connected to a USB hub countless times.

---

