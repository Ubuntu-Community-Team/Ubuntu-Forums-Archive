---
title: "Boot error"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by marek10 on 2014-08-24
I've found some threads describing this problem, however I decided to create a new one, hope I didn't do wrong. 

I'm totally new to Linux and Ubuntu and I want to try them on my laptop however I can't seem to get the live usb working. Whenever I try to boot from the USB I get the "Boot error" message and nothing else. I also have a desktop PC and the Live USB works perfectly there, also a  bootable windows 7 USB I created works on the laptop no problem. Plus I tried several programs for creating the live USB with no change. I've found out that the problem is that my notebook takes the USB as floppy, not as HDD and I cannot find any options in bios to change this.

I have the following USB: Silicon Power Blaze B20 8 Gb
And the following laptop: ASUS K52JK

Isn't there a way to somehow make the USB work without buying a new one?

---

### Post by kc1di on 2014-08-24
Hi marek10 and Welcome to Ubuntu,

Have you tried telling the bios to boot from the floppy?  see if it in fact will boot from the usb drive. 

also if you haven't tried unetbootin to make the live usb give it a try you can find[ it here ]("http://unetbootin.sourceforge.net/")
it will run in windows ok. format the usb stick before running unetbootin ;)

---

### Post by marek10 on 2014-08-24
What do you mean? I set the priorities in Bios and when it tries to boot from the USB it's just "Boot error", nothing else. I tried searching the Bios for something that might help but I didn't find anything.

I've tried  several programs including unetbootin and I formatted the USB before every attempt as FAT32. I think there is no problem with the Live USB, I think the problem is in the laptop.

---

### Post by kc1di on 2014-08-24
Ok my next question would be have you tried burning the ISO to a dvd and tried to boot it that way.  
Obviously the machine is not detecting the usb drive correctly. 

Give the DVD a try.

---

### Post by marek10 on 2014-08-24
Yeah, I was thinking about that as well, but I would like to have a USB, not a DVD. If everything fails however, I think I will have no choice. 

Thank you for the help.

---

### Post by grahammechanical on 2014-08-24
On my machine if in the BIOS I disable legacy floppy boot then I get elsewhere in the BIOS USB memory stick options. Including an option to set the USB stick as a USB external drive and give it priority over the hard disk. Manufacturers do things differently but that is something that you might try.

---

### Post by sudodus on 2014-08-24
Is this link describing your computer?

[http://laptops-specs.blogspot.se/2010/04/asus-versatile-performance-k52jk.html](http://laptops-specs.blogspot.se/2010/04/asus-versatile-performance-k52jk.html)

Just to sort out one possible cause of problems: I think there should be 'only' BIOS and not UEFI. Am I right about that?

Sometimes a particular pendrive does not boot in a particular computer, while another one will be happy to boot it. So it is worthwhile to try another pendrive, for example borrow one from a friend or colleague. Sometimes you should 'pretend' that the pendrive is a hard disk drive. Boot with the pendrive plugged in, enter the BIOS and the boot order menu. If you find the pendrive among the hard disk drives, put it at the top of the list. Sometimes you can chainload from something that boots, either a CD, for example a Plop CD, another pendrive or even from the internal drive.

Several tips about booting from USB pendrives (and other USB mass storage devices) can be found at these links (and links from them). Have a look at them, try some tips. Whatever happens, luck or no luck, please post here again :-) We are many people who are happy to help, and it is valuable for other users to learn from your experiences.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by oldfred on 2014-08-24
My system is not Asus, but even though I have USB-hard drive it will not boot from that. It only boots a flash drive from the hard drive settings. And it only offers a choice of hard drives when the flash drive is correctly configured as a boot device and plugged in when rebooting. Since my system had so many USB optios I thought it should have been one of those, but it was not.

And some have to turn off floppy drive setting in BIOS to make sure it does not try to use that if you do not have a floppy drive. 

Some only boot from one port, have you tried different ports. And only boot a flash drive if only the one flash drive is plugged in.

---

