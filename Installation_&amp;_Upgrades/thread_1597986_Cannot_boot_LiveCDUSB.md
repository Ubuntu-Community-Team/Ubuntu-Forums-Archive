---
title: "Cannot boot LiveCD/USB"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by syko21 on 2010-10-16
I think my computer is actively trying to stop me from using 10.10

First thing I tried was to make a liveusb with the usbcreator.exe in windows. Each time I tried to boot the sequence would just freeze at the very first text line with the words "SYSLINUX Peter Alvin et al"
I tried this with two different USB drives and on a second computer. Both USB drives stopped at the same line but worked fine on the second computer.

Next I thought maybe my iso was corrupt, so I downloaded another and compared md5. Both iso's checked out with the MD5 I found on the ubuntu site.

I was trying to avoid wasting a disc but finally burned a 64bit desktop iso. While trying to boot I got this message
[http://imgur.com/C57c3.jpg](http://imgur.com/C57c3.jpg)

Thinking it was a USB issue I attempted to unplug all of my USB devices and force it to boot to the Desktop Environment. That yielded me this screen
[http://imgur.com/FKYRR.jpg](http://imgur.com/FKYRR.jpg)

Finally I try doing a check disc for errors which gets me this screen
[http://imgur.com/yT7us.jpg](http://imgur.com/yT7us.jpg)

I also tried installing via wubi which just got me to the USB error screens again.


Hardware
Core i7-860
Gigabyte P55-UD4P Rev 1.0 BIOS F10 (Latest)
4GB 1066 DDR3 OCZ
NVIDIA GTX 260
Razer Deathadder Mouse
WUSB600N by Linksys

If you need any other information please post here. Thanks in advance.


PS> I tried creating a liveusb of Backtrack4 and that booted fine.

---

### Post by mörgæs on 2010-10-16
Have you tried making a USB stick with the latest Unetbootin? 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by syko21 on 2010-10-16
unetbootin didn't work

---

### Post by mörgæs on 2010-10-17
We need more information here. Have you tried 32 bit versions? Alternate installer? 10.04?

---

### Post by amitvn on 2010-10-17
unetbootin works........u need to dnload latest version of that 
i too used older one and got problem,Got newer one and worked fine :)

---

### Post by syko21 on 2010-10-18
It turns out the kernel doesn't like my hardware. I installed 10.04 via usb and then did an upgrade to 10.10 which gave me those USB errors on the next reboot. So I tried the old 10.04 kernel which works perfectly.

2.6.32-24-generic = 10.04 kernel that is working well for me
2.6.35-22-generic = 10.10 kernel that gives me usb errors

---

### Post by dhavalbbhatt on 2010-10-18
> **syko21 said:**
> It turns out the kernel doesn't like my hardware. I installed 10.04 via usb and then did an upgrade to 10.10 which gave me those USB errors on the next reboot. So I tried the old 10.04 kernel which works perfectly.

2.6.32-24-generic = 10.04 kernel that is working well for me
2.6.35-22-generic = 10.10 kernel that gives me usb errors

This was a big problem for me as well. I could not get any kinds of install to work for about 3 days. Finally, I downloaded the DVD version of 10.10 64bit and that installed fine. Try doing that and see if that works.

Dhaval

---

### Post by syko21 on 2010-10-20
I don't see how using the dvd which has the same kernel version as the one I download during the upgrade process from 10.04 will be of any help. In any case, I'll just wait until there is another kernel update in a month or two before trying the current one. In the meantime I'm planning on filing a bug report to see if the issue can't be tracked down, regressions from an LTS will have to be investigated.

---

### Post by oregonbob on 2010-10-20
After a lot of horsing around I got my 10.10 Persistent USB stick working, see [http://ubuntuforums.org/showthread.php?t=1587007](http://ubuntuforums.org/showthread.php?t=1587007)

Then I played with 10.10, saw little difference and continued with my 10.04. I would wait a month as you suggested.

---

### Post by psusi on 2010-10-20
Run the memtest; that panic looks like you have bad ram.

---

