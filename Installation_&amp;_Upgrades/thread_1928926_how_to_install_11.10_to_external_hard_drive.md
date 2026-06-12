---
title: "how to install 11.10 to external hard drive"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by birdy62 on 2012-02-21
Hi I am looking to install ubuntu 11.10 to an external hard drive. I am looking to create a "portable" operating system that I can plug in and boot anywhere, as long as the computer I plug it into can boot from usb of course. I want the full operating system not the "live" version. Which is the best way to go about it? I have tried using unetbootin but for reason although the bios found unetbootin ubuntu failed to appear on the unetbootin menu. I am not tied to unetbootin I am open to other methods. I am familiar with the use of the terminal and happy to edit fstab or whatever is necessary.

Thanks

---

### Post by bogan on 2012-02-21
Hi!,** birdy62**,

You do not need to use unetbootin, or anything complex, just use a Live CD or Live USB to install in the normal - 'Something else' mode; selecting the Usb in the 'Change' Menu.

 Make certain it is the right USB!!

For best results an USB of at least 8GB, give at least 4.6GB to the Linux partition.

When it finishes, boot from it and Update - mine took 337 updates and 55 minutes to bring it up to 11.10, 3.0.0-16.

I installed Grub Customiser and used it to get a distinctive Grub Menu background, and make the USB default.
 Similarly for the Desktop background, so there is no mistaking from which installation one is booting.

**Edit:** I also put a 1GB NTFS as the first Switch partition, so a Windows machine would recognize the Usb, if  I want to use it to transfer data from Windows to another Linux machine.

Chao!,** bogan.**

---

### Post by Herman on 2012-02-21
I agree with the previous poster. Installing to a USB external hard drive is the same as installing to any other hard drive. You can choose either the normal 'Desktop' Live/Install CD or USB, or the 'Alternate Installation' CD.

You will need to make sure you install GRUB to MBR in the same hard drive you are installing Ubuntu in. The average person should be able to easily achieve that just by keeping an eye out during installation for the opportunity to specify which hard disk to install GRUB to and choosing the appropriate disk. A few people choose to unplug their other hard disk drive(s) beforehand just to make sure. Going to that extreme shouldn't be necessary, but you can do it if you feel you need to.

The standard Ubuntu install will boot and run in most computers. It detects hardware at startup and configures itself just as well as the Live CD version does. Ubuntu has had this capability in the regular installed operating system since Hardy Heron came out back in 2008 with the Xorg 7.3 Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/"). 
The exception is if you need to install drivers for special video cards to get some video-intensive app or game working properly, like Google Earth or Quantum GIS or similar. If you do install a hardware-specific video driver, you may find yourself booting to a black screen the next time you try booting in a different computer. A solution that always works for me is to boot to the GRUB menu and choose the recovery option. There's an option you can find in the menus to delete reset your xserver, and after that you can continue the boot-up as normal.
I think it just deletes your /etc/X11/xorg.conf, and another way you can do the same thing is to use a terminal in a Ubuntu Live CD, that has worked for me too. A new config file will be generated automatically during boot-up.

Since it will be a portable operating system you might want to consider choosing to encrypt your /home folder. That will protect your privacy in case the USB happens to get lost or stolen.
If you use the 'Alternate Installation' CD you can even install the entire Ubuntu operating system (except /boot) in a LUKS fully encrypted file system. Ubuntu will be pretty slow to boot up with a LUKS encrypted file system. Once it has booted it will run slightly slower too but it's still quite usable, you'll hardly notice the difference.
A downside is that it might be harder for new users to maintain (fsck), fix or recover files from in the event of some kind of disaster, but users with a little command line experience shouldn't have too much trouble. It's worth the little extra effort for the added security. Think identity theft.

Well, good luck with it and enjoy Ubuntu! :)

---

