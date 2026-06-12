---
title: "Installing Ubuntu On Hp netbook mini"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2015-04-22
Hello everyone, I have a Netbook mini currently running Linux mint and I want to replace it with Ubuntu. Strange thing is I had not problem getting Mint installed but for the life of me I can't get Ubuntu to boot up from the USB stick.

When I turn on my netbook I hit F9 and I can see my USB drive in the list but when I click enter the screen goes black and there's only a blinking cursor in the top left hand side on my netbook mini and nothing happens. Any ideas what's happening here.

Thanks so much

---

### Post by kerry_s on 2015-04-22
sounds like a bad usb installer. what did you use to make the usb installer ? sometimes it happens try another method of making the usb installer. you can use unetbootin, disks, startup disk creator,dd . 

i have the hp mini 210-1010nr

---

### Post by RobGoss on 2015-04-23
Yes I tried the installer you mention but it was taking to long, funny thing is the usb stick with Ubuntu works fine on my other machines so I don't know what's wrong with the mini that it wont boot up. The usb tool I'm using is something Usb creator. Thanks for the help.

---

### Post by kerry_s on 2015-04-23
well i just did a clean install & like you said it has the cursor in the upper left corner, you just have to wait.

if i remember right you have 2gb of ram in yours ? i would still suggest a light ubuntu version such as xubuntu or lubuntu, they both seem the same resource wise to me, so it came down to which feels better to me.

---

### Post by RobGoss on 2015-04-23
OK and I just use the USB installer suggested and got the same results. Did it install after you waited?

---

### Post by kerry_s on 2015-04-23
> **robert159 said:**
> OK and I just use the USB installer suggested and got the same results. Did it install after you waited?

i always choose to boot live/try , from there i setup my wifi, cause it's hidden, then i start the installer.

---

### Post by RobGoss on 2015-04-23
But I even try the mint installer that's on it now and got the same results

---

### Post by kerry_s on 2015-04-23
> **robert159 said:**
> But I even try the mint installer that's on it now and got the same results

you mean it just stays at the blinking cursor ?
what ubuntu version you trying ?

---

### Post by RobGoss on 2015-04-23
Yes Ubuntu 14.04

---

### Post by kerry_s on 2015-04-23
> **robert159 said:**
> Yes Ubuntu 14.04

your trying full ubuntu ?

i'm using xubuntu 15.04 64bit

---

### Post by RobGoss on 2015-04-23
Yes I was hoping to get it installed. But I don't understand even the version on mint that's on the mini netbook now I also try on the USB stick because I wanted to see if it would also go into boot mode

I'm thinking its something to do with the boot sequence because when my USB appears on the boot list its says USB.floppy.

---

### Post by kerry_s on 2015-04-23
thats weird.

---

### Post by RobGoss on 2015-04-23
Yes that's what I say. I've formatted the usb and installed different versions of Linux and they work on my other machines but not the Netbook mini so that tells me it's something to do with the boot sequence, process of elimination.

---

### Post by kerry_s on 2015-04-23
have you looked in your bios (f10) ?
make sure everything says enabled.

---

### Post by RobGoss on 2015-04-23
Yes I did and I do believe there was one setting that said disabled so I'll check again to enable it and see how that goes. Thank you Kerry for your time if anything changes I'll post the results. I will also post the boot loading list maybe you know something I don't.

---

### Post by kerry_s on 2015-04-24
you must be doing something wrong, i just installed ubuntu 15.04 64bit without a hitch.
i used the startup disk creator(aka:usb-creator-gtk) to make the installer. it's a little slow cause i only have 1gb ram, but it's actually pretty nice, it scales everything to fit my 10" screen.

---

### Post by oceola2 on 2015-04-24
You can refer to this thread [Solved liveCD to USB, etc.](http://ubuntuforums.org/showthread.php?t=2274986) probably on the second or third page this forum by now, maybe if the link doesn't work.
I had a 16GB Kingston Data Traveller with OpenSUSE on it and had that installed on a small 64bit Netbook.
I formatted the USB as it was an older version and used the Startup Disk Creator to move a Live/install Ubuntu14.04 to the USB.
Checked my boot sequence on the notebook (Note: if you do not have administrative privilege it might not allow changing if on User access level) and after turning off the notebook completely, inserted the newly created Live/Install USB. Turned on the Notebook.
Creating just an image was not an option as it not only created the ISO but also allowed the install part.
Install went fine.

One thing I noticed is it takes a long tme for the Start Up Creator to make the persistence files and you may have a panel with a backa and forth animation reading 100% and seemingly caught in an endless loop, let it run, it will reach the end.

---

### Post by RobGoss on 2015-04-24
> **kerry_s said:**
> you must be doing something wrong, i just installed ubuntu 15.04 64bit without a hitch.
i used the startup disk creator(aka:usb-creator-gtk) to make the installer. it's a little slow cause i only have 1gb ram, but it's actually pretty nice, it scales everything to fit my 10" screen.

I don't know what I could be doing wrong it's really not that complicated I installed Ubuntu a number of times with out any trouble. What boot up options are you using with your mini?

---

### Post by RobGoss on 2015-04-24
> **oceola2 said:**
> You can refer to this thread [Solved liveCD to USB, etc.]("http://ubuntuforums.org/showthread.php?t=2274986") probably on the second or third page this forum by now, maybe if the link doesn't work.
I had a 16GB Kingston Data Traveller with OpenSUSE on it and had that installed on a small 64bit Netbook.
I formatted the USB as it was an older version and used the Startup Disk Creator to move a Live/install Ubuntu14.04 to the USB.
Checked my boot sequence on the notebook (Note: if you do not have administrative privilege it might not allow changing if on User access level) and after turning off the notebook completely, inserted the newly created Live/Install USB. Turned on the Notebook.
Creating just an image was not an option as it not only created the ISO but also allowed the install part.
Install went fine.

One thing I noticed is it takes a long tme for the Start Up Creator to make the persistence files and you may have a panel with a backa and forth animation reading 100% and seemingly caught in an endless loop, let it run, it will reach the end.

As far as administrative privilege I'm the olny one that uses this notebook so I don't see why I would be having this problem.

---

### Post by kerry_s on 2015-04-24
> **robert159 said:**
> I don't know what I could be doing wrong it's really not that complicated I installed Ubuntu a number of times with out any trouble. What boot up options are you using with your mini?


i just tap f9, select my usb (lexar usb flash drive)

i'm creating the usb for xubuntu 15.04.

---

### Post by RobGoss on 2015-04-24
Yes I'm aware about tapping f9 but for me when I choose USB nothing happens that's my point. Are you installing it on a Mini netbook? is so what boot option did your USB say.

---

### Post by kerry_s on 2015-04-24
> **robert159 said:**
> Yes I'm aware about tapping f9 but for me when I choose USB nothing happens that's my point. Are you installing it on a Mini netbook? is so what boot option did your USB say.

sorry for the late reply i just got my upgrades, so my ram is now 2gb, but i was having issues with the drive, I'm using a sd card to sata adapter, i was running it with only 1 sd ard, it supposed to have 2 sd cards & run as a raid 0, when I put the new card in I lost the whole drive nothing in gparted. so I popped the back off pulled both sd cards formatted both to fat 32 & put them back in, I'm now installing xubuntu 15

yes, i'm installing on a hp mini 210-1010nr
the boot manager says " Lexar  Usb Flash Drive" Lexar is my usb brand

(sorry I'm on my iPod till the install finishes )

---

### Post by kerry_s on 2015-04-24
could it be your usb or have you tried others with the same result ?
have you tried using a different usb port, mine has 3 usb ports, i tend to use the first port on the right, cause i have a wifi dongle on the left port, since on mine the wifi requires firmware(bcm4313).

---

### Post by RobGoss on 2015-04-24
> **kerry_s said:**
> sorry for the late reply i just got my upgrades, so my ram is now 2gb, but i was having issues with the drive, I'm using a sd card to sata adapter, i was running it with only 1 sd ard, it supposed to have 2 sd cards & run as a raid 0, when I put the new card in I lost the whole drive nothing in gparted. so I popped the back off pulled both sd cards formatted both to fat 32 & put them back in, I'm now installing xubuntu 15

yes, i'm installing on a hp mini 210-1010nr
the boot manager says " Lexar  Usb Flash Drive" Lexar is my usb brand

(sorry I'm on my iPod till the install finishes )


Kerry mines says USB floppy, I don't use a floppy so I don't understand what's going on that I can't install Ubuntu

---

### Post by kerry_s on 2015-04-24
there most be something wrong with that usb drive. the first thing i would try is to wipe the usb
in terminal:
dd if=/dev/zero of=/dev/sdb bs=512 count=1

(the command zero's the drive)
then format to fat32 in gparted

---

### Post by kerry_s on 2015-04-24
also i keep forgetting to tell you, if you use external monitor, the vga on the left, xubuntu seems to be the only 1 to handle it correctly, when you use that F4 key to select your choice.
i hook mine up to my tv sometimes to get a bigger screen or watch things i downloaded.

---

### Post by RobGoss on 2015-04-25
Thanks so much everyone for your help and time, At last it booted into Ubuntu YAAAA thanks to you guys I was able to fix the USb using Gparted everything seems to be ok so now I will play with Ubuntu and see how everything runs

---

### Post by kerry_s on 2015-04-25
> **robert159 said:**
> Thanks so much everyone for your help and time, At last it booted into Ubuntu YAAAA thanks to you guys I was able to fix the USb using Gparted everything seems to be ok so now I will play with Ubuntu and see how everything runs

hey, a win win
glad u were able to save that usb & glad you finally got ubuntu on there

---

### Post by RobGoss on 2015-04-25
Yep it was that USB from the start. I have been playing with Ubuntu 14.04 LTS because this is what I also have on my desktop and it's really performing well on this netbook thanks to you guys.... Have a great weekend my friend...

---

