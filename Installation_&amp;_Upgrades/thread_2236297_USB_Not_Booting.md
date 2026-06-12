---
title: "USB Not Booting"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by Brandon_MacDonald on 2014-07-25
Hey everyone, I'm new to Linux, but I have recently installed Bodhi alongside Windows 8. I can't get on Bodhi anymore and I don't know why.
Anyway, that doesn't matter because I'm trying to install Ubuntu and then uninstall Bodhi when I get on it. I used UnetBootin to put Ubuntu on a USB, and it won't boot from BIOS at all. I have EasyBCD to select which OS to boot from, and when I'm restarting my PC, no matter which device I try booting from, it just goes to the choice for OS (which is Windows 8 and Bodhi) from EasyBCD. 

Is EasyBCD the reason why my flash drive isn't booting? If it is, how would I fix it?
Also, is there a way to tell exactly which device I should use in the BIOS boot order? I have the boot order to boot from the USB's first, and it hasn't made a difference.

Thanks in advance.
Edit; The computer didn't come with Windows 8, I upgraded it to Windows 8 if that makes a difference.

---

### Post by mooreted on 2014-07-25
On my computer I press F10 at the BIOS splash screen to bring up the boot menu then select my USB drive. The function key you use depends on the BIOS your computer uses.

It could be something went wrong with Unetbootin. You could try formatting the thumbdrive to FAT-32 and trying again.

I recently ran into a problem with a Sandisk thumbdrive that was Windows 8 certified which means it now mounts as a hard drive not a removable drive. We could not image any of our systems with them because the imaging software was looking for a removable drive at reboot. In this case we had to buy new thumbdrives.

---

### Post by Brandon_MacDonald on 2014-07-25
I can select the USB drive in the boot menu, but it goes straight to the loader to choose between Windows 8 and Bodhi.
I've also tried UUI and I get the same thing. Both formatted to FAT32 before using.
And my USB is being recognized as a removable drive.

---

### Post by oldfred on 2014-07-26
Then you may need to verify that download was correct with md5sum and try installing with other boot creator programs. Some programs work better than others. And a few flash drives just do not work. Also have you tried other USB ports, some systems work better from one port or the other.

       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM

[/URL]
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[URL="http://www.pendrivelinux.com/"]http://www.pendrivelinux.com/
      [/URL]
 SOLVED!!! Used rufus to create bootable USB and it worked! I've tried UUI and unetbootin before. 
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

    [URL="http://www.pendrivelinux.com/"]
[/URL]
  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

[URL="http://www.pendrivelinux.com/"]

[/URL]

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by impliedconsent2 on 2014-07-26
> **Brandon_MacDonald said:**
> I can select the USB drive in the boot menu, but it goes straight to the loader to choose between Windows 8 and Bodhi.
I've also tried UUI and I get the same thing. Both formatted to FAT32 before using.
And my USB is being recognized as a removable drive.

Check priority of what boots first in your UEFI.  Put USB at top (or whatever you end up booting with).  I've always had great luck using [Unetbootin]("http://unetbootin.sourceforge.net/") as the .iso installer onto my USB drive and double checking BIOS/UEFI.  Maybe you're in Legacy only...dunno ... my push here is at the POST.

---

