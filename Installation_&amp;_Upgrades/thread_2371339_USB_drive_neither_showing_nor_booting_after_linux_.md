---
title: "USB drive neither showing nor booting after linux live installation."
date: 2017-09-13
forum: Installation &amp; Upgrades
---

### Post by bubblebee on 2017-09-13
So I wanted to install linux Libuntu 17.04 desktop 64 bit directly to my USB in order to run it from there.


I picked pretty much the exact same option as shown in these pictures I am copying from howtogeek:

[IMG]https://www.howtogeek.com/wp-content/uploads/2016/12/ximg_58473aac8f2b6.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.ru8QiLAnkN.jpg[/IMG]




[IMG]https://www.howtogeek.com/wp-content/uploads/2016/12/ximg_58473aa48d784.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.VV1CsTHQ0m.jpg [/IMG]
[IMG]https://www.howtogeek.com/wp-content/uploads/2016/12/ximg_58473a973fc57.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.ZviRbQB7za.jpg[/IMG]
[IMG]https://www.howtogeek.com/wp-content/uploads/2016/12/ximg_58473ae1b9f75.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.P7uwlwab2B.jpg[/IMG]


And finally I got:

[IMG]https://www.howtogeek.com/wp-content/uploads/2016/12/ximg_58473d89e3cd7.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.88LzpQ4etq.jpg[/IMG]

I was using Kingston 4 GB usb drive(Kingston Data traveler 2.0 USB device)


I did all the steps and now:


A: My drive has vanished as show in the screen-cap that I have taken:


[IMG]https://i.imgur.com/ySx1Mqi.png[/IMG]

B: I cannot boot from it while I can boot from my live install Windows 8.1 USB just fine(hence of course I have selected the boot order right in the BIOS setup.)


Yet my drive can be detected in the disk managment utility as show in the screen-cap that I have taken:



[IMG]https://i.imgur.com/wvcUyRI.png[/IMG]

I have already tried to ininstall and reinstall the device as shown in this video:


[https://www.youtube.com/watch?v=Jfqouva0pso&t=11s](https://www.youtube.com/watch?v=Jfqouva0pso&t=11s)

Nothing is helping....

I am at the verge of just giving it up :(

---

### Post by oldfred on 2017-09-13
Not sure what tool you are using to create flash drive.
But many now use dd or dd in background as ISO is configured as a hybrid file. The hybrid file can then be image copied to a flash drive or DVD, but then flash drive is not a standard partitioned drive but more like a DVD drive. I would not expect Windows to then see it correctly.
But system should be able to boot from that flash drive, if settings in UEFI/BIOS are correct.
What brand/model system? What video card/chip?
UEFI or BIOS install?

If your system is UEFI you can try this:
       UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040

[/URL]
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

[URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

### Post by bubblebee on 2017-09-13
@OldFred:

I am using the linux live USB creator from [https://www.linuxliveusb.com/](https://www.linuxliveusb.com/)

My system is Lenovo Ideapad 110

Here are my secs:

[IMG]https://i.imgur.com/Cf03qhD.png[/IMG]

I have UEFI, I think , but I have selected the legacy option in the boot menue because the tutorials on Youtube say so.

---

### Post by oldfred on 2017-09-13
Have not seen tutorials that say to use Legacy. If so most of those are wrong. If dual booting you need to use UEFI.

There are a few systems where Legacy may be a bit easier if only installing Ubuntu, but legacy is a 35 year old configuration and you have new hardware.

       Lenovo 110s Experience Installing and Using Linux on Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

### Post by HankB on 2017-09-13
As oldfred said try to configure the USB drive for UEFI booting. The Ubuntu image should support that.

Once the ISO is loaded on the USB drive Windows may not show it. My understanding is that Windows doesn't like USB drives with more than one partition and UEFI requires that. At best you may see the UEFI partition alone. On Linux, 'gparted' complains that the block size for the USB drive is wrong. But all you really need is that the boot loader can see the UEFI partition and get the process started.

On my Lenovo Y-50 there is a smaller button next to the power button (for system recovery) that allows me to get to a boot menu that I can use to boot whatever is found. I have my BIOS set to legacy (and Linux is installed as legacy and boots by default) and I need to use this button to (UEFI) boot Windows.

HTH,
hank

---

### Post by bubblebee on 2017-09-14
Thanks everybody!

I am getting the failed to boot error. Now I just want my USB drive back. How do I make it readable again so that I can format it.

---

### Post by oldfred on 2017-09-14
Image copy with dd is not a standard formatted drive.
You have to use dd to erase the first sector so it can be formatted.

This also has suggestions if gparted not working:

[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

