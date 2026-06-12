---
title: "Installing Ubuntu on SD card"
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by Matthew_Smith on 2014-02-14
Hi,


So, I want to install (try) Ubuntu on a SD card. Are these steps right?


1. Make SD card bootable
2. Put ISO onto it with LinuxLive USB Creator
3. Boot from SD card
4. Install on the SD card partition made with step 1


And will I be able to make the SD card normal (use it as a normal 16 GB SDHC card) by formatting it? (don't want to loose space with that one!*)?


*had Chromium on my USB once, formatted, and lost all my 8 Gig space :(


Please tell me if I am right and how to make my SD normal.


Thanks,
Matthew Smith

P.S: Running Win 7 Home Premium x32 (ugh!) installing on 16 Gb SDHC card.

69 views and no response, please help me! anyone...

---

### Post by bc.haynes on 2014-02-14
I believe you install to an sd card the same as to a usb stick (I could not find the Howto for this.). Be patient and someone with more experience than I will help you....or you can help yourself and Google the question.

---

### Post by QIII on 2014-02-14
> **Matthew_Smith said:**
> 69 views and no response, please help me! anyone...

That means that 69 people (or web crawlers indexing your thread) have looked at your post and have no answer for you.

I do not, as I have no experience with installing on SD cards.

Please allow 24 hours before bumping.  Remember that this is a world-wide forum populated by people from all time zones who volunteer their time as they have it.  Impatience can be off-putting to many members who might otherwise help.

Cheers.

---

### Post by 23dornot23d on 2014-02-14
Toms Hardware has a how to ..........

But from what I have been reading the best way is to get a USB adapter for the SD card and boot
it that way ......... but I too have never booted from a SD card .........

Here is the search I did should you want to check out what I found ..........

[https://www.google.co.uk/search?q=installing+ubuntu+from+a+sd+card&hl=en&btnG=Google+Search&sourceid=Mozilla-search&start=0#hl=en&q=installing+ubuntu+from+a+sd+card+2014+solved](https://www.google.co.uk/search?q=installing+ubuntu+from+a+sd+card&hl=en&btnG=Google+Search&sourceid=Mozilla-search&start=0#hl=en&q=installing+ubuntu+from+a+sd+card+2014+solved)

---

### Post by ian-weisser on 2014-02-14
I installed to an SD card.
But that was years ago, before making live .iso media was so easy.

Instead, I copied an installed (minimal) system onto the card, and modified /etc/fstab and grub to reflect the new boot media.

---

### Post by C.S.Cameron on 2014-02-14
If your computer will boot SD cards, (some won't), you can do a Persistent install to it, I suggest UNetbootin or Startup Disk Creator.

Or you can do a Full install:

Disable your internal HDD,
Plug in your SD card,
Install to it using Live CD or Live USB.

---

### Post by mc4man on 2014-02-14
> **C.S.Cameron said:**
> 
Or you can do a Full install:

Disable your internal HDD,
Plug in your SD card,
Install to it using Live CD or Live USB.

To re-enforce the above,
To do a real install to removable media you cannot install to the media that you're booting from. So you have to boot from one device, install to another.
Also you'd be well advised to switch the boot loader location *to the device you're installing to* rather then the default chosen in the live installer's partitioner

---

### Post by C.S.Cameron on 2014-02-15
> **mc4man said:**
> 
Also you'd be well advised to switch the boot loader location *to the device you're installing to* rather then the default chosen in the live installer's partitioner

These should be the same if you have disabled the internal HDDs.

---

### Post by Matthew_Smith on 2014-02-15
> **23dornot23d said:**
> Toms Hardware has a how to ..........

But from what I have been reading the best way is to get a USB adapter for the SD card and boot
it that way ......... but I too have never booted from a SD card .........

Here is the search I did should you want to check out what I found ..........

[https://www.google.co.uk/search?q=installing+ubuntu+from+a+sd+card&hl=en&btnG=Google+Search&sourceid=Mozilla-search&start=0#hl=en&q=installing+ubuntu+from+a+sd+card+2014+solved](https://www.google.co.uk/search?q=installing+ubuntu+from+a+sd+card&hl=en&btnG=Google+Search&sourceid=Mozilla-search&start=0#hl=en&q=installing+ubuntu+from+a+sd+card+2014+solved)

I have an adapter and I read that article. I just wanna know if I'm doin' it right.

But I don't get it... can't I just put the iso on the SD card using Pendrive Linux and boot from that, inatalling ubuntu onto the SD card? I guess I'll just follow Tom's Hardware Tutorial installing on my SD card.

---

### Post by sudodus on 2014-02-15
Do you want the SD card to have a live system (like an Ubuntu install USB pendrive) or do you want a system, where you can store data?

0. First make the computer boot from the SD card. I think you know how to do that now

1. Flash the system (live, persistent live or 'installed system') in the same way as described for USB pendrives and almost the same way as described for internal drives.

See also this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

So try (and ask again if you get stuck) :-)

---

### Post by C.S.Cameron on 2014-02-15
> **Matthew_Smith said:**
> But I don't get it... can't I just put the iso on the SD card using Pendrive Linux and boot from that, inatalling ubuntu onto the SD card? I guess I'll just follow Tom's Hardware Tutorial installing on my SD card.

No, you can not install to the drive you boot from.

If you make a persistent install, (Unetbootin etc), the SD card ends up formatted FAT32 and you can continue to use it to store and transfer data.

If you do a Full install and make the first partition Fat32 and use the second partition as / , (using Something else while partitioning), you can use the first partition to store and transfer data.

---

### Post by Matthew_Smith on 2014-02-17
Ok, 

So i put the iso onto the SD card using pendrive linux and then booted onto it but it came up with a console and said something like "unable to mount ... ". I then wanted to boot onto windows to see what I'm meant to type in (I saw the official usb how-to doc and it had some commands, I think) but I had COMPLETELY NO INTERNET CONNECTION, causing me to reinstall ("restore" thingy. Erases the c drive and resets all settings to factory. Basically, factory reset/ hard reset) windows. I DO NOT WANT TO HAVE TO DO THAT AGAIN. So can you guys tell me what I done wrong? I didn't make the SD bootable, but I don't think that matters, as Pen Linux did something to the SD card already, and the setup STARTED to launch.

Thanks for all your help,
Matthew_Smith

---

### Post by sudodus on 2014-02-17
I don't know what happened. Maybe you wrote a bootloader to the internal  drive, containing Windows. Be very careful, and avoid messing with the  drive containing Windows. Then you can change the boot order back to the  internal drive, and Windows should boot as before. If that happens (again?), it is possible to repair the Windows bootloader without a full re-install.

Anyway, it is very important to identify the drives, so that you are sure that you install to the SD card and not to the internal drive. The methods to identify are different depending on the operating system (Windows or linux).

-o-

If you intend to create a USB boot drive or an SD boot card, the procedure should be similar (except the extra task to make sure that the computer will boot from the SD card). So you should be able to use one or more of the methods and tools available to create a USB boot drive, that you find in the following link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you are starting from Windows, I would recommend Unetbootin, which has a rather good record of success. See this detailed description

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

If you are starting from linux, we can discuss the details further. I think ***mkusb*** has a good record of success, and it shows rather well, how to select the target drive (to avoid mistakes).

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Unetbootin is a good choice also in linux.

---

### Post by C.S.Cameron on 2014-02-17
+1 for UNetbootin ,it may be a bit ugly but it works.

But if you want a Full install to SD Card why not try Sudodus' OBI, (one button installer):

[http://ubuntuforums.org/showthread.php?t=2172971](http://ubuntuforums.org/showthread.php?t=2172971)

---

