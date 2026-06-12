---
title: "pendrivelunix install fail"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by losthawken on 2010-06-18
Hey all,

I got a lot of help here last time I had a problem so I thought I would try it again.  :)

I'm trying to run Ubuntu 10.4 from a 320 GB external drive.  The last time I tried this I ended up accidentally deleting and replacing the mbr on my PC and had to go through all kinds of trouble to get it back.  

Then I discovered pendrivelinux.com I tested it out on an 8 GB stick I had and it works GREAT! 

However, the Universal Installer from Pendrive Linux doesn't recognize my 320 external drive....  I partitioned the drive and made a 10 GB Fat32 partition; still not recognized.  

The closest thing I found to a solution was to make a start-up disk out of the 10 gb partition (using ubuntu loaded from the other flash drive).  This works and changes are saved to the next start-up because of the casper-rw I put in, but start up is slower and I get the annoying install option at start-up every time.  

Any ideas on how to either A) get pendrivelinux universal installer to recognize my drive, or B) Install ubuntu onto the drive without the annoying and slow start-up install options (either a full install, or disabling the start-up stuff).

Thanks!

~JG

---

### Post by tommcd on 2010-06-18
So this is an external 320GB hardrive? And not a usb flash drive??
Pendrive linux is for usb flash drives. If you are installing to an external hard drive, just install normally and select the external drive as the root, swap, and (ideally) a separate home partitions. The external drive should be listed as /dev/sdb (assuming you only have 1 internal drive).
You could install grub to the external drive and then set the external drive to be the first boot device in the BIOS. If you choose this option, set the boot flag to on for the external drive when you are at the partitioning part of the install.

---

### Post by C.S.Cameron on 2010-06-18
Full install:
Turn off and unplug the computer.
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4-5 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4-5 GB, Beginning, Ext4, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning, Ext4, and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Some people succeed without disabling their internal drive but I'm scared not to because of past experience, as you might relate to.

---

### Post by oldfred on 2010-06-18
I am not as worried as C.S.Cameron about installing grub to the wrong drive as it is not that difficult to reinstall grub. But for new users his way does prevent common errors. The most important thing if installing to a second drive is the advanced button on the last partition screen. It allows you to choose where to install grub and on an external you want grub installed to the external drive.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

The problem has been so common that meierfra. posted a page on how to fix when boot is from internal not external drive.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by losthawken on 2010-06-18
Thanks All,

To clarify, the drive in question is an [IOMEGA eGO portable Hard drive]("http://go.iomega.com/en-us/products/external-hard-drive-portable/specialty-ego-portables/ego-leather/?partner=4760").  I don't know whether that makes it a 'flash' or an external HD.

I like C.S. Cameron's idea as I've had trouble with losing the mbr before.  It happened on a work computer (that I shouldn't have been screwing around on) and installing grub would have led to obvious questions.  It was resolved eventually.  Oldfreds last link would have been immensely helpful then.

Regardless, I'll try it on my laptop tonight, I can pop the hard drive out easily enough, and install safely from there.  I'll let you know how it works.

---

### Post by darkod on 2010-06-18
You "lost" a mbr before because you didn't use the Advanced button in the ubuntu installer and told grub2 where to install. Now that you know what the issue was, there is no need to be so paranoid.
Of course, you can go ahead and unplug hardware if you want to. But if you are so afraid, don't install an OS. Get someone else to do it for you. Just my personal opinion.

Will you get things wrong from time to time? Yes. Will you learn a lot and know how to handle things yourself in future? YES.

For example, the pendrive procedure didn't work on the usb hdd probably because windows uses one type of driver for usb sticks, and another type for usb hdds. The pendrive procedure is designed for usb stick so it ignored the usb hdd.

What if you mess up the hdd disconnecting/connecting it? :)

---

### Post by losthawken on 2010-06-23
> **darkod said:**
> You "lost" a mbr before because you didn't use the Advanced button in the ubuntu installer and told grub2 where to install. Now that you know what the issue was, there is no need to be so paranoid.
Of course, you can go ahead and unplug hardware if you want to. But if you are so afraid, don't install an OS. Get someone else to do it for you. Just my personal opinion.

Will you get things wrong from time to time? Yes. Will you learn a lot and know how to handle things yourself in future? YES.

For example, the pendrive procedure didn't work on the usb hdd probably because windows uses one type of driver for usb sticks, and another type for usb hdds. The pendrive procedure is designed for usb stick so it ignored the usb hdd.

What if you mess up the hdd disconnecting/connecting it? :)

OK, so I took the lecture, man-ed up and did the install.  It would have worked, except that it refused to install grub on the external drive (sdc) any idea why?

---

### Post by C.S.Cameron on 2010-06-23
Give it a try unplugging the internal drive and bypassing the Advanced option.
Let us know if disabling the internal drives has any validity.

---

