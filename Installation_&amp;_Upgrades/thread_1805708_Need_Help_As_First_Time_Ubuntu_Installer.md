---
title: "Need Help As First Time Ubuntu Installer"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by WahooMC on 2011-07-16
Hello everyone, I have decided to install ubuntu 11.04 at a friend's recommendation.  I have a new Dell Latitude with specs I believe fulfill any minimums I have found.  I currently have windows 7 64 bit installed.

I am following this link 
[http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-2.html](http://www.tomshardware.com/reviews/ubuntu-11.04-natty-narwhal,2943-2.html)

trying to install along with windows.  I have a usb stick with the installer or whatever you call it on it, and I can boot my computer from the usb, and when I get to the screen where I can select run ubuntu, install, etc in black and gray text I can choose any of the options.

My problem comes next, regardless of what I choose the screen becomes about two thirds black and a third gray, and I cannot seem to get any menu or anything else to display at this point.  I have been reading things for a couple hours, trying some commands but it seems unresponsive.  I would greatly appreciate any help to get this working.

PS I have tried 32 and 64 bit versions of 11.04 with the same problem, currently the usb has the 32 bit on it.   Thanks.

---

### Post by WahooMC on 2011-07-16
If anyone has links to threads on this site, videos or outside resources that could help me that would be great too if nobody has the time to answer this.  Having the problem of getting a black/gray screen before installing ubuntu, im really not sure what could be the problem, there isnt any sort of error message, its just blank.

---

### Post by Bucky Ball on 2011-07-16
Download 10.04 LTS and give that a try. 

When you boot, choose the option 'Try Ubuntu' (it's called something like that) and see if that runs okay. This is a pretty good check of hardware compatibility.

---

### Post by Bucky Ball on 2011-07-16
Also, when you boot from the CD or USB you have created, check the media for errors. The best way to download the ISO is via torrent if you can do that:

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

### Post by WahooMC on 2011-07-16
Thanks a lot, I'll give the torrent a try and see if that works.

---

### Post by WahooMC on 2011-07-16
Okay, so I downloaded the first 11.04 torrent file on that site you linked, created a thumb drive and when I booted from the usb and tried to begin installation, I was prompted with the following error message:
 
Could not find kernel image: /casper/vmlinuz
 
When I tried entering other codes in the boot: line, all of them came back with the response that the kernal image could not be found.  Any idea what the cause of this might be?

---

### Post by WahooMC on 2011-07-16
Additionally, when I was prompted with the first menu with the options to run, install on a hard disk, test memory, advanced settings and help, I was unable to run or install.  The computer beeped and flashed black before returning me to this menu whenever I tried to as well as restarting the countdown the says something like "Ubuntu will begin boot sequence in 5...4...3..2..1" 
 
Thought maybe the extra info would help, thanks for your help so far.

---

### Post by WahooMC on 2011-07-16
**Ubuntu 11.04**
 
[LIST]
[*][ubuntu-11.04-alternate-amd64.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-amd64.iso.torrent")
[*][ubuntu-11.04-alternate-i386.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-i386.iso.torrent")
[*][ubuntu-11.04-desktop-amd64.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent")
[*][ubuntu-11.04-desktop-i386.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent")
[*][ubuntu-11.04-server-amd64.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-server-amd64.iso.torrent")
[*][ubuntu-11.04-server-i386.iso.torrent]("http://releases.ubuntu.com/11.04/ubuntu-11.04-server-i386.iso.torrent")
[/LIST]

Those are the offered torrent files from the link provided, which one do I want to be using for my purposes?  I downloaded the first link assuming that was the standard 64 bit I would want for my laptop.

---

### Post by Bucky Ball on 2011-07-16
Hmm, I would perhaps go for 10.04 LTS personally. Longer support and MUCH better place to start ...

---

### Post by ManualSparrow on 2011-07-16
You said you are installing Ubuntu on a friend's recommendation. To me it sounds like your Ubuntu .isos have errors when they are written to your LiveUSB, so you might try having your friend use the "Create Ubuntu Startup Disk" option (from the System menu) on their machine and then install from that. You could also try using a CD or DVD instead of a USB drive.

Assuming that the copying of the .iso is actually the problem and your friend is not available, you may want to try using the PenDrive Linux tool recommended on the Ubuntu homepage: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/). 

If that does not solve your problem I would recommend using that same tool to download and burn an older release, such as 10.10. 

Finally, you should check these forums for any known compatibility issues with your setup.

EDIT: If you have Intel hardware, you should be downloading the i386 iso for a 32-bit install, not the 64-bit AMD one.

EDIT EDIT: Sorry, this is inaccurate. The amd64 is for all 64-bit systems and the i386 is for all 32-bit systems.

---

### Post by Eldera on 2011-07-16
[quote=WahooMC]I downloaded the first link assuming that was the standard 64 bit I would want for my laptop.[/quote]

the first link is the alternate install.

I am only a hobbyist, so please, some of the experts correct me if I am wrong, but wouldn't it be easier for a first time installer to use ubuntu-11.04-**desktop**-i386-iso?

I thought the name "desktop" was for laptops and desktops as opposed to servers.

Don't get discouraged. Read the advice in this thread carefully and try again from the beginning.

Also, I think a first time user would find 10.04,2 LTS easier than 11.04. I have both on separate partitions and I had less trouble installing 10.04.2 LTS than I did 11.04.

Just the view of the less experienced. I don't understand why he is using the alternate install. Will someone more experienced please clarify.

---

### Post by Mr. Shannon on 2011-07-17
> EDIT: If you have Intel hardware, you should be downloading the i386 iso for a 32-bit install, not the 64-bit AMD one.
Actually, if you have a 64bit Intel processor and want to run Ubuntu 64bit then you need the amd64 and not the i386.  And if you have a 32bit AMD processor then you need i386.  I know it's confusing.

> I am only a hobbyist, so please, some of the experts correct me if I am wrong, but wouldn't it be easier for a first time installer to use ubuntu-11.04-desktop-i386-iso?

Ignoring the i386 vs. amd64 described above you are right, accept that in the this case he is having trouble getting graphics to load with the live version (desktop).  Thus, if he cannot get the (desktop) install to work he might consider using the (alternate) since it does not need to load up a gui (graphical user interface) before it installs.  NOTE: I am no expert.

---

### Post by Bucky Ball on 2011-07-17
> **Mr. Shannon said:**
> Actually, if you have a 64bit Intel processor and want to run Ubuntu 64bit then you need the amd64 and not the i386.  And if you have a 32bit AMD processor then you need i386.

AMD64 install = ANY 64bit hardware, make irrelevant. AMD, Intel ... doesn't matter.

Same applies to i386: ANY make of 32bit processor, not just Intel.

It is confusing but let's not make it any more so. If you have a dual-core processor, that will be 64bit. AMD64 bit install in that case, regardless of whether you are using an AMD or Intel processor. ;)

---

### Post by grahammechanical on 2011-07-17
I just want to avoid confusion. I am running Intel hardware and I have the 64bit Ubuntu installed and the ISO image is called Ubuntu 11.04 amd64. Everything works as it should because "amd" does not mean only for AMD CPUs. It refers to the fact that AMD produced the original specification.

Please check this link

[http://en.wikipedia.org/wiki/x86-64]("http://en.wikipedia.org/wiki/x86-64")

amd64 and Intel64 are basically different names for the same thing. Here is a quote:

> There are a few differences between the two instruction sets. Compilers generally produce binaries that are compatible with both AMD64 and Intel 64,making these differences mainly of interest to developers of compilers and operating systems.

We do not have a 64bit Ubuntu for AMD processors and another for Intel processors. We do not need one.

Regards.

---

### Post by ManualSparrow on 2011-07-17
Thanks guys. Edited post to reflect this information.

---

### Post by Blasphemist on 2011-07-17
So after going through all this on creating another live cd, if you still have the problem I believe it will be an issue with the driver for you video card. Do you have an nvidia gpu? If you don't know what you have, is there a sticker on the pc that says? 

I ask about nvidia because the open source driver is used by default and for some cards it isn't the recommended driver. There are ways to work around this by setting a kernel mode early in the boot process. Please see this post if you are having issues even after creating a new cd. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Start with the first post and don't get intimidated by the length of the posts or the thread. Post 3 shows what I'm talking about but the first 2 also have some information you should see.

---

### Post by Mr. Shannon on 2011-07-18
> It is confusing but let's not make it any more so. If you have a dual-core processor, that will be 64bit. AMD64 bit install in that case, regardless of whether you are using an AMD or Intel processor.

Actually, now I'm going to make it even more confusing.  To run Ubuntu 64bit you must have 2 processors (Dual Core is one way to get this) and a 64bit motherboard.  See post #4 at [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1116366") link.  For instance, I have an Intel Core 2 Duo but my motherboard's width is only 32bit, thus I cannot install a 64bit operating system.

---

