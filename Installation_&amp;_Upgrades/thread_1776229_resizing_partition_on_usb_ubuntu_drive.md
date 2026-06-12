---
title: "resizing partition on usb ubuntu drive"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by jsthrower on 2011-06-05
A few months ago I installed ubuntu 10.10 on a 250 g usb hardrive to boot to.  I have it set up the way I like it.  I let the install disk auto install the program.  There are two partitions.  Works great.

I have an older desktop that was running win xp and the main drive was starting to fail so I used easus disk copy to clone the drive and decided to use the second slot for a ubuntu drive.  I installed a 120 g drive to install ubuntu onto and set grub for dual boot.  Then I decided instead of downloading and resetting up the ubuntu drive maybe i could disc copy from the 250 to the 120. 

In order to do so I need to resize the partition on the 250g usb drive so the copy will fit on the 120g. Easus partition nor windows device manager recognizes the format the the ubuntu disc used when it installed on the usb drive...I tried gparted live ( booting form the cd )but it doesn't recognize the usb drive at all.

My question is what program can I used to resize the partition of the usb drive in order to get it to a size that disk copy will allow me to copy onto the 120 g drive.  The second question is what file format does ubuntu put on the disk during install that isn't detected by these programs.

---

### Post by kjuergen on 2011-06-05
Try Disk Utility (in the system menu).
In Xubuntu 11.04 you have to install it but I think it's standard in ubuntu. Great tool I just installed.

Juergen

---

### Post by oldfred on 2011-06-06
It is normal that windows does not see Linux partitions.

But we have seen some windows tools incorrectly write the partition table and then gparted will not work. Often end of extended is beyond the end of the drive or other overlapping issues.

Post this as it gives all the details on what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

