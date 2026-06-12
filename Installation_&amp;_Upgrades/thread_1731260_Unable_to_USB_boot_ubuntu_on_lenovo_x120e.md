---
title: "Unable to USB boot ubuntu on lenovo x120e"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by slimysnot on 2011-04-16
Hi,

I just started testing ubuntu 10.10 today (first time user!) on my desktop via usb drive and I liked it very much so i wanted to try it on my laptop (lenovo x120e, a relatively new model).

When i tried to use the usb drive on my laptop, I am unable to boot ubuntu at all!

I went into the "boot device" menu (pressed F12, for lenovo users) and to specifically boot from the "USB HDD" drive.  This caused the screen to go blank and a cursor started blinking on the top left hand side of the screen.  A few seconds later, i would return to the "boot device" menu to try again.  (my guess is this is what happens if boot fails).

My laptop has win 7 installed on the hard disk, with no other OS installed.  The bios is at factory settings.

I googled this topic and there are many threads out there of users encountering the same problem, none specifically for the x120e model.  the other solutions are either too technical for me to understand:confused: or may not apply.  Below is a list of what i've tried or will try later..

Note: Please let me know if you need more information from me!

List of things tried/to be tried
1)  use unetbootin instead of Universal-USB-installer
        - tried both, was able to boot from desktop but not on laptop
2)  assign a variable to kernel (could not find the exact name, but the variable name had the string "intel" prepended
        - i didn't try this... my laptop is amd (i don't think it should matter... my desktop is also amd)
3)  re-image the usb
        - done it many times
4)  corrupted usb?
        - seemed to boot on desktop with no issues... tried other usb anyway but no luck
5)  Try to install 10.04
        - just downloaded it, will try tomorrow
6)  Try to remove the hard disk
        - will help with debug as last resort... but obviously not long term solution

Thanks in advance!

---

### Post by Dutch70 on 2011-04-17
Try other boot options, such as nomodeset...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="Red"]https://help.ubuntu.com/community/LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by slimysnot on 2011-04-17
Thanks for your suggestions!  I was trying them but the usb boot is somehow magically working now.

The usb boot disk will only work after i installed memtest86 drivers onto my usb and then write ubuntu 10.10 without reformatting the usb disk!

not sure what's going on...

i didn't get the keyboard = *ubuntu logo* splash screen... just a text only prompt (which is different than loading it on my virtual machine).

---

### Post by slimysnot on 2011-04-17
the drivers are not available, but that's another issue... closing thread...

---

### Post by Dutch70 on 2011-04-17
Nice! :) 

Seems that Ubuntu has a way of doing that sometimes.

---

