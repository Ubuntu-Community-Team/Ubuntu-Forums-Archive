---
title: "External CD drive will not boot"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by M_Brooks on 2014-04-01
I have an old Fujitsu Lifebook P Series with Window XP, which I would like to replace with Ubuntu.  I made a boot CD of Ubuntu which works on my desktop and laptop computers but the Fujitsu notebook will not boot from the external CD drive.  There is no internal CD drive.  I have changed the BIOS boot sequence to boot from "CD/USB" first, but when I tun the computer on it boots from the hard drive and Windows comes up.  I have tried an older external CD Drive and a newer DVD Drive, both of which are recognized in Windows.  I have also attempted to load Ubuntu from a flash drive with no success.  Any suggestions?

---

### Post by coldraven on 2014-04-01
Did you make the USB stick bootable? I use Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) 
On my HP laptop the "Boot from USB" option in the BIOS is only shown when a USB device is plugged in. Try again.

---

### Post by sudodus on 2014-04-01
Welcome to the Ubuntu Forums :-)

I have to ask if this link describes correctly you computer

[http://www.cnet.com/products/fujitsu-lifebook-p-series/](http://www.cnet.com/products/fujitsu-lifebook-p-series/)

In that case the specs are really low, way too low for standard Ubuntu, even low for the lightest of the Ubuntu flavours 'Lubuntu'. But if you want to install anything, you could try Lubuntu 13.10 via the alternate installer or 'Lubuntu Core' via Ubuntu 13.10 mini.iso. If that won't work, try some flavour or re-spin based on Ubuntu 12.04 LTS. Or try some other linux distro that is really ultra light-weight.

This is not the easiest thing to do, but we are here to help you, and we have patience ...

See the following link for more information about old computers
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by M_Brooks on 2014-04-03
Thank you both for your suggestions.  I tried booting from a USB flash drive but the computer will not recognize it.

My computer is the same as described in the link Sudodus gave me from CNet except without an internal CD drive.  I also tried Lubuntu with the same results.  The Ubuntu and Lubuntu initial selection screens come up but I get about 6 "EDD: Error 8000 reading sector ------" errors and a window displaying "/casper/vmlinuz:  file not found".  That file is on the Lubuntu CD.  I'm attempting to attach a photo of the screen.  This is my first try so I don't know if it will work.

---

### Post by sudodus on 2014-04-03
I think you will have big problems running an Ubuntu based system with graphics in this computer. Maybe you can install and run Lubuntu Core, but I would recommend some ultra light-weight linux distro like ***Puppy, Tiny Core, Slitaz ***or*** DSL***.

Another alternative would be to try to install ***Lubuntu Core Trusty*** (the version being developed now) with the experimental installer ***9w*** according to this link

[http://ubuntuforums.org/showthread.php?t=2130640&page=4&p=12968205#post12968205](http://ubuntuforums.org/showthread.php?t=2130640&page=4&p=12968205#post12968205)

There is a list of light and ultra-light linux distros in the following link

[Light Linux Distributions - Hardware Testing (RAM)]("http://ubuntuforums.org/showthread.php?t=1582027")

---

### Post by M_Brooks on 2014-04-04
I wonder why this computer can run Windows XP Pro with Microsoft Office, Firefox and other programs but cannot handle Ubuntu, or even Lubuntu?  Although I would really like to convert to Ubuntu it looks as though I'll just have to stick with what I now have on the machine until it bites the dust.  Thank you for your suggestions.

---

### Post by sudodus on 2014-04-05
Windows XP was designed long ago for computers with specs like those of your computer. The current linux versions are designed ten years later, and although they allow for old computers, there is a limit for backward compatibility in real life for the 'full size' linux distros.

But I am serious when I recommend some ultra light-weight linux distro like ***Puppy, Tiny Core, Slitaz ***or*** DSL***. One of those might serve you well in your old computer, and I am happy if linux can help prolonging the life of an old computer. It must not be an Ubuntu version or flavour, it can be any linux distro.

It is a bad idea to connect Windows XP to the internet after end of life, because it will receive no more security updates, and your computer will be wide open for attacks from new malware.

---

