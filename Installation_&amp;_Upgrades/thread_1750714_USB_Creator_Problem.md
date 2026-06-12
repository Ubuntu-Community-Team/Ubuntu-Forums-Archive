---
title: "USB Creator Problem"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by frank cox on 2011-05-05
When I tried to use the new Multiboot system from PenDrive Linux it seems to have renamed my Toshiba 16Gb and my PNY 4gb drives to USB ZIP drives and they will not boot with Multiboot , Unetbootin {Linux or Windows} or the usb-creator in Ubuntu.
Before they showed up as USBHDD and booted fine.

I would really like to get the Multi-boot system working so i could install numerous Distros from a single stick.

Help would be appreciated.

---

### Post by wilee-nilee on 2011-05-05
> **frank cox said:**
> When I tried to use the new Multiboot system from PenDrive Linux it seems to have renamed my Toshiba 16Gb and my PNY 4gb drives to USB ZIP drives and they will not boot with Multiboot , Unetbootin {Linux or Windows} or the usb-creator in Ubuntu.
Before they showed up as USBHDD and booted fine.

I would really like to get the Multi-boot system working so i could install numerous Distros from a single stick.

Help would be appreciated.
Install gparted wipe the partition on the thumb make another name it what you want.

That multibooter works great I have found though it wont recognise the mounted thumb if not formatted with gparted, I use a fat32 partition. This is if you use the Linux version, as far as gparted.

---

### Post by frank cox on 2011-05-06
> **wilee-nilee said:**
> Install gparted wipe the partition on the thumb make another name it what you want.

That multibooter works great I have found though it wont recognise the mounted thumb if not formatted with gparted, I use a fat32 partition. This is if you use the Linux version, as far as gparted.

Thanks

I already tried doing that with gparted and reformatting with windows, neither helped.
I am pretty sure it has to do with the drives being recognized as usb zip I just don't know what to do to change it back to usbhdd.

---

### Post by wilee-nilee on 2011-05-06
> **frank cox said:**
> Thanks

I already tried doing that with gparted and reformatting with windows, neither helped.
I am pretty sure it has to do with the drives being recognized as usb zip I just don't know what to do to change it back to usbhdd.

So out of curiosity I had to look zip up; how do you recognise that the recognition is zip?

---

### Post by frank cox on 2011-05-06
> **wilee-nilee said:**
> So out of curiosity I had to look zip up; how do you recognise that the recognition is zip?

When I hit F12 to choose the boot method it has cdrom , the 2 hard drives , and the USB key  listed as USBZIP0 as choices.
When they worked the USB key was listed as USBHDD0

You must be a young person , ZiP drives were popular  before cdroms became available , they were basically large floppies in 10 and then 100 mb sizes .  They eventually got bigger but I never bought one because even though I paid 250.00 plus 3 dollars a disk for my first cdrom it held so much more it was worth it. 

Puppy Linux , and some other distros let you choose to have flash drives recognized as FDHDD, ZIPS , USBCDROMS , and even as a combo . FDHDD seems to work best on my Dell 531

They still make super floppies which are 144 megabytes instead of 1.4 . Flash drives are cheaper but can be difficult to boot from. Puppy Linux works great that way .

---

### Post by satanselbow on 2011-05-06
> **frank cox said:**
> 
You must be a young person , ZiP drives were popular  before cdroms became available , they were basically large floppies in 10 and then 100 mb sizes.

Oh man! - I still got a stock in my loft :) The mere mention on "Omega" makes me chuckle in dreamy eyed nostalgia :popcorn:

You forgot to mention that they were to same size as a housebrick and weighed about the same :D

Back on topic...

I haven't really worked out why this tool makes such a difference in "resetting" USB sticks- or what it does that formatting etc in Win/Ubuntu doesn't - but it really helps ;)

Download the HP USB Tool: [http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197) 

Works on all machines/sticks (not only HP) and zaps them good n proper where even gparted fails ;)

Then try to create you mutiboot again. I have a whole box of USB sticks so just use a diff one for each distro but I did have a play with it (the multiboot tool) a little while ago and found it to work well :D

---

### Post by frank cox on 2011-05-06
> **satanselbow said:**
> Oh man! - I still got a stock in my loft :) The mere mention on "Omega" makes me chuckle in dreamy eyed nostalgia :popcorn:

You forgot to mention that they were to same size as a housebrick and weighed about the same :D

Back on topic...

I haven't really worked out why this tool makes such a difference in "resetting" USB sticks- or what it does that formatting etc in Win/Ubuntu doesn't - but it really helps ;)

Download the HP USB Tool: [http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197) 

Works on all machines/sticks (not only HP) and zaps them good n proper where even gparted fails ;)

Then try to create you mutiboot again. I have a whole box of USB sticks so just use a diff one for each distro but I did have a play with it (the multiboot tool) a little while ago and found it to work well :D



You must see a glass as half empty, I have lost several flasjhdrives,. If i ever owned an Omega Zip drive I doubt that would have happened. Another advantage is when their useful life is over (of course useful is in the mind of the believer} they made excellant house bricks! Ever try building a house with flash drives ?
Their not even uniform in size!

Thanks, I will give it a try later!

P.M.
Zip drives would make great driveways as well!

---

### Post by C.S.Cameron on 2011-05-06
If you want to put a bunch of iso's on a flash drive and boot them try MultiBootUSB.

---

### Post by frank cox on 2011-05-07
> **C.S.Cameron said:**
> If you want to put a bunch of iso's on a flash drive and boot them try MultiBootUSB.

That is where this problem started. When I tried to use Multi-Boot !

Thanks anyway.

---

### Post by C.S.Cameron on 2011-05-08
> **frank cox said:**
> That is where this problem started. When I tried to use Multi-Boot !

Thanks anyway.

The MultiBootUSB I am talking about is not from pendrivelinux:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by frank cox on 2011-05-09
> **C.S.Cameron said:**
> The MultiBootUSB I am talking about is not from pendrivelinux:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Thanks
i will try it tomorrow!

---

### Post by frank cox on 2011-05-11
> **C.S.Cameron said:**
> The MultiBootUSB I am talking about is not from pendrivelinux:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

I tried that one and received this error:

./MultiBootUSB.sh: line 177: syntax error near unexpected token `fi'
./MultiBootUSB.sh: line 177: `fi'
User@User-Inspiron-530:~/MultiBootUSB$  sudo ./MultiBootUSB.sh
./MultiBootUSB.sh: line 177: syntax error near unexpected token `fi'
./MultiBootUSB.sh: line 177: `fi'


Not sure what to do.

---

### Post by C.S.Cameron on 2011-05-11
MultiBootUSB needs to be run from a distro that uses grub2, (running while booted from the Live CD works).

---

### Post by frank cox on 2011-05-11
> **C.S.Cameron said:**
> MultiBootUSB needs to be run from a distro that uses grub2, (running while booted from the Live CD works).

I will try running from Live CD but the distro is Ubuntu 11.04 so it uses Grub 2.
Thanks

---

