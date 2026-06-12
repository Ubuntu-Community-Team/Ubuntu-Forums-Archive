---
title: "Ubuntu 14.10 installation fail"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by logan18 on 2014-10-31
I was trying to install Ubuntu 14.10 using Windows 7 and when the installation progress bar finished, it said that an error had occurred and didn't give me an error code or anything. Am I going through the installation process correctly? My friend hasn't upgraded/installed a new version since 12.04 and his most recent experience with it is burning the iso image to a disk. It seems there is a new method and he is unfamiliar with it. I don't really know much about Ubuntu, I'm just interested in dual booting and using it due to its quick/sleekness and virus free capabilities. Sorry if this issue has been addressed/solved already but I couldn't find a thread with the answer to my specific problem.

---

### Post by sudodus on 2014-10-31
Welcome to the Ubuntu Forums :-)

Please describe how you tried to install Ubuntu! Does 'using Windows' mean a wubi install (installing when running Windows), or does it mean that you created a DVD/USB boot drive when running Windows and then rebooting?

Wubi does not work with Windows 8 and is no longer developed, there are few people who use it nowadays and we recommend that you use another method
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

Booting/installing from DVD is still used by many people, but nowadays many people (including me) prefer booting/installing from USB pendrives. See this link (and links from it)

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I would also suggest that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by logan18 on 2014-10-31
Yes, we attempted to install using the wubi process in windows 7. We initially tried using the burning image to a disk method but we didn't get the familiar 'disk' icon on the desktop. We just got a folder with a bunch of files in it (see attached image). We tried extracting it and basically ended up with the same thing. Thanks for your reply.

---

### Post by sudodus on 2014-10-31
If you have a USB pendrive, I would suggest that you use Win32 Disk Imager according to this link

[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Otherwise, if you want to make a second attempt to burn a DVD disk: You should burn an iso image to disk. (Do *not* make a data DVD. The result should be a disk with several files and directories, not a single iso file).

And then, you must make the computer boot from DVD or USB instead of the internal hard disk drive. And you do that via changed settings in the UEFI/BIOS menu system or with a hotkey.

It makes it easier to give relevant advice, if you describe the computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and if you know if the computer run in UEFI or old style BIOS mode.

---

### Post by ajgreeny on 2014-10-31
I'm not sure what you mean by the > We initially tried using the burning image to a disk method but we  didn't get the familiar 'disk' icon on the desktop. We just got a folder  with a bunch of files in it (see attached image). We tried extracting  it and basically ended up with the same thing.You don't have to extract anything at all; you need to boot from the burned image disk by putting it in the DVD drive then rebooting the machine.  You may need to enter BIOS and ensure that the machine is set to boot from the DVD drive first, not the hard disk, then when you get the choice of what to do menu, go to the "Try without installing" option.

If everything works as you want it to you can double click on the "Install Ubuntu" icon on the live system's desktop and follow the instructions as linked to in sudodus' post.

---

### Post by QIII on 2014-10-31
If I may add to sudodus' comments for clarity:

You do not want to try to boot into Windows and install from there when using the iso after you have created the installation media.  You need not be worried about whether the disk shows in the typical way on your Windows desktop, as Windows should not even be running.

Cheers!

---

### Post by logan18 on 2014-10-31
I guess we'll try the USB method. The thing is, I'm used to seeing this appear on my desktop (see attachment), but instead I'm getting the folder with the files in it. How do I acquire that single file to write to disk? I know that I'm supposed to boot from the disk and not the drive. Essentially, I just want the icon as depicted in the attachment. That pic was taken from google images, I want a newer version of course. Thank you for your patience.

---

### Post by sudodus on 2014-10-31
The iso file 'looks' like that on the desktop and in a file browser, but actually, it is a good sign that the DVD shows folders and files. Maybe you can try again to boot from the DVD disk, but if still no go, it is a good idea to try to make a USB boot/install drive.

*Edit*: It is getting late here, and I will soon shut down the computer, but I'm sure you can get help from other people ...

---

### Post by logan18 on 2014-10-31
ok thank you for your help

---

