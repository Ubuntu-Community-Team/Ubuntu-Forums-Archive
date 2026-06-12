---
title: "Installing Lubuntu 14.04 on Windows XP laptop"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by J._Routh on 2014-07-07
Hello, I have an old netbook laptop, an Acer Aspire One model. It came installed with Windows XP. Now that support for Windows XP has ended I want to use another OS. I chose Lubuntu 14.04 because the computer is too old for any of the new Windows OS. I downloaded the ISO install file and created a bootable flash drive using UNetbootin. Everything looks good. When I boot the laptop from the flash drive, the Lubuntu desktop is displayed.

1. One of the initial questions asks if I want to install 3rd party software, specifically "Fluendo MP3 plugin" includes MPEG Layer-3 audo decoding technology. Is this recommended?

2. A second screen asks if I want to install Lubuntu alongside Windows XP or replace it, which deletes all the Windows XP files. Does anyone have any experience with the latter option, ie. removing Windows XP and replacing it with Lubuntu? 

3. If I choose to install Lubuntu alongside Windows XP, can I remove Windows XP at a later time? If so, what is the procedure?

Thanks,
J. Routh

---

### Post by Rex Bouwense on 2014-07-07
1.  That is up to you.  I have installed it.
2.  I have done both without problems.  However, back up any data that you have on your computer now.  You will lose it if you install Lubuntu over XP.  Use an external source because the whole drive will be used if you replace XP with Lubuntu and you could even lose it if you installed Lubuntu next to XP (Murphy's Law)

---

### Post by slooksterpsv on 2014-07-07
1) Fluendo MP3 Plugin allows you to listen to mp3s, you can always install the lubuntu-restricted-extras to listen to music that's in WMA, MP4, etc. format as well as various video formats.

2) Removing XP and replacing it with Lubuntu reformats the entire drive, nothing is saved, no files, nothing. It's like your computer came with Lubuntu and not XP - so if you have any music, pictures, videos, documents, etc. you need saved, back them up.

3) If you install alongside, you can migrate your data over (if you allow enough of a size to accomodate your data), and you can remove XP at a later time, but you'd have to use the bootable USB again to have Lubuntu take over the rest of the drive. I believe it can be resized without damaging the current data on the disk. You may want to check into that, search on the forums, it's been asked.

Anything else we can help you with?

---

### Post by sudodus on 2014-07-08
I agree with the previous replies, and I want to add a few links that might be useful
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mastablasta on 2014-07-08
> **slooksterpsv said:**
>  I believe it can be resized without damaging the current data on the disk. You may want to check into that, search on the forums, it's been asked.


yes it can. the procedure is:
- you boot into live session (boot from USB), 
- you resize the partition (or create a new linux paritition) 
- and finally you update grub (using for example the boot repair tool or command line) to remove Windows XP from the selection in the startup menu.

---

### Post by ubfan1 on 2014-07-08
I think after making the partition larger, you will need to run resize2fs to increase the size of the filesystem (defaults to partition size).

---

### Post by Topsiho on 2014-07-09
I don't see anywhere what size your hard disk is.
Installing Lubuntu alongside Windows you'll need space to accommodate both.
My Acer Aspire One has an 8 GB SSD, which is barely enough to do something useful, using Lubuntu.
It arrived with Linux (Linpus) installed {which I replaced within 2 days, as it was shocking(ly bad), with a real Linux}.

The option 1. that you mentioned (installing 3rd party software) is because that sotware may be non-free and may not be allowed to be included in the distribution. You yourself have to decide whether you are allowed, and want, to download and use it. It contains a.o. codecs for MP3 and so.

You always can install it later, e.g. when trying to play an .mp3 file you are asked to install the necessary codecs if they are not on your computer.

Topsiho

---

### Post by J._Routh on 2014-07-19
Thanks for all your suggestions. I ended up installing Lubuntu alongside Windows XP. On my 150MB hard drive I relegated 50 MB for Windows XP and 100 MB for Linux. So far so good.

---

### Post by Rex Bouwense on 2014-07-19
Great.  Obviously you had no problems.  If you have any other problems or questions do not hesitate to post a new thread.

---

