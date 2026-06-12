---
title: "Install without CD"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by kenl1925 on 2008-07-17
I have a PC that was built by someone else, it runs win 98SE.
It had some viruses and now is pretty much useless.  I wanted
to get xubuntu on it so I could atleast drag an ethernet cord
over there and have a computer for others to surf the net with
when they are over here.  Anyway, I tried to boot from the CD
drive but it would not pick it up,  I do however have a 4gb
flash drive that I could use.  This is the distro I downloaded
[http://hex1a4.net/xubuntu/mirror/releases/8.04/release/](http://hex1a4.net/xubuntu/mirror/releases/8.04/release/)
The first download on that page.
To clarify, I do not want to boot from the flash drive each time
like a portable system but just want to install it then have no
need for the flash drive being in it.  I have not modified the
file I downloaded.  I remember having to burn it in a special
way before to even get it to start on other computers, and have
a cd burner, but the computer I want to install it on won't boot
from the CD(even from the bios menu).

I am on msn now at kenl1925 @ gmail.com
and will be for awhile.  I will also check back here.
Thank you for the help in advance.

---

### Post by tommcd on 2008-07-17
You have to burn the CD as an iso image. You can't just copy it to a CD like a data file. If you are burning the iso image from a Windows machine you can use Iso Recorder or Infra Recorder. See this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso)|(image](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso)|(image))
Burn the iso at the slowest possible speed to prevent a bad burn. You should also verify the md5sum of the image you downloaded, but that is not likely the cause of your problem. See this:
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=(md5sum](https://help.ubuntu.com/community/HowToMD5SUM?highlight=(md5sum))
Also, make sure the computer is set to boot from the CDROM drive as the first boot device in the BIOS.

The link you posted for the iso you downloaded for Xubuntu is fine.

And welcome to the Ubuntu forums!!!

---

### Post by kenl1925 on 2008-07-17
I had done that previous to this.  On start up I pressed F8 or whichever
button it is on that system and found the bios expecting to see the cd drive
as an option.  I believe the only ones I had were the C:(hard drive) and
the floppy drive.  If I burned the data to the CD could I somehow copy that
burned data to my flash drive and boot from that?
And thank you for the welcomeing  =)

---

### Post by tommcd on 2008-07-17
If you want to install Ubuntu from a flash drive you can use Unetbootin. I am not familiar with this, but it does work for Windows and Linux for vreating a bootable installer on a usb stick. See these:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=(flash)|(drive)|(install](https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=(flash)|(drive)|(install))
You will of course have to be able to set the computer's BIOS to boot from removable media, like a flash drive.

---

### Post by kenl1925 on 2008-07-17
As long as I dont have to go deep into the hard drive I should be fine.
I can't open the control pannel as is...freakin viruses.

---

### Post by kenl1925 on 2008-07-17
Perhaps a better question, if I can transfer the iso to the other computer
can I boot from the file off the desktop?  I do not need windows so it
would not be a dual boot set up

---

### Post by tommcd on 2008-07-17
> **kenl1925 said:**
>   On start up I pressed F8 or whichever
button it is on that system and found the bios expecting to see the cd drive
as an option.  


Did you specifically set the PC to boot from the CDROM drive? I'm not sure what you mean by "bios expecting to see the cd drive
as an option". There should be a section in the BIOS titled "boot priority" or "boot order" or something like that. You have to set the boot order so that the CDROM drive is listed first. Is that what you did?

---

### Post by kenl1925 on 2008-07-17
I got to that part, but the cdrom drive was not an option.  It is set to
boot from the hard drive now, and the other option was a floppy.

---

### Post by tommcd on 2008-07-17
> **kenl1925 said:**
> Perhaps a better question, if I can transfer the iso to the other computer
can I boot from the file off the desktop?  I do not need windows so it
would not be a dual boot set up

You will need a working computer to burn the iso image to a CD or create the flash drive installer. You can't just burn boot off the CD image off the desktop while Windows is running. But see my last post about the boot order in the BIOS.

---

### Post by kenl1925 on 2008-07-18
I'm going to try the normal method one more time and get back to you
with the results.  Last time it wasn't an option, but thats just my luck
hehe

---

### Post by tommcd on 2008-07-18
> **kenl1925 said:**
> I'm going to try the normal method one more time and get back to you
with the results.  Last time it wasn't an option, but thats just my luck
hehe

If you have no option to boot from CDROM or usb stick I'm not sure how else you can install Ubuntu. Here is an article on installing Ubuntu from a hard drive image using bootable floppies. If you only options ar booting from floppy or hard drive, perhaps this would be an option:
[https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)
I have never tried that though.

Another thing you could do is take the hard drive out of the computer and put it in a different PC. In other words remove the hard drive from the second PC, and temporarily replace withe hard drive from the first PC that you want Ubuntu on. Install to the hard drive by booting off the install CD. Once you get Ubuntu installed, then just put the hard drive back in the first PC and it should work. I don't know of any other options.

---

### Post by kenl1925 on 2008-07-18
If the normal method fails I might have to try that even though I really
do not want to open up the system.  about 1/3 done burning the iso

---

### Post by kenl1925 on 2008-07-18
So it didn't work.  But I may be able to after a ton more work.  I just
found a cd for win 98se  for PC's without windows.  Mine already has windows
obviously, so how can I remove the current version so I can reinstall with
that cd, then possibly get xubuntu workin

---

### Post by kenl1925 on 2008-07-18
well...it doesn't read usb drives or cds.  but I used hijackthis and sent
the file to a floppy.  so now I might be able to get somewhere...and all
for a crappy old computer lol

---

### Post by tommcd on 2008-07-18
> **kenl1925 said:**
> So it didn't work.  But I may be able to after a ton more work.  I just
found a cd for win 98se  for PC's without windows.  Mine already has windows
obviously, so how can I remove the current version so I can reinstall with
that cd, then possibly get xubuntu workin


If the computer can't boot from the CDROM drive then you won't be able to install Windows98 from a bootable CD either. The options I gave you (install from CD, from usb flash drive or usb CDROM drive, the bootable floppy, or putting the hard drive in a different computer) are the only ways to do it. Windows98 was available as a series of installation floppies if I remember correctly. If you could hunt down a set of those you could install Windows98 from those.

There is the Wubi installer. This lets you install Ubuntu from within Windows. From the Wubi website it says it does support Windows98. If you could get Windows98 up and running this may be a good option for you. I have no experience with Wubi, but you can read about it here:
[http://wubi-installer.org/](http://wubi-installer.org/)
[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

This page discusses several ways to install Ubuntu from within Windows. It will work from Windows98 (assuming you can get your Windows98 up and running again). I would try "The CD approach" or "The CD image approach" toward the bottom of the page. I did not know of these methods before. I just found them. This may be the best option for you:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
The page was written for Ubuntu Gutsy, but if you just replace "gutsy" with "hardy" in the links on that page it will work for Ubuntu Hardy 8.04, the current version.
Good luck!

---

