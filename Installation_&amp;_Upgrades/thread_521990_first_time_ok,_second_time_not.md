---
title: "first time ok, second time not?"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by firsttimeubuntero on 2007-08-10
I burned a disc image of Ubuntu 7.04 and decided to install it in a rig with no operating system in it. The first time I placed the CD there were no problems, the gnome and everything else loaded. I was just booting from the CD but was short on time so I turned off the box and decided to install it later. 
When I got back home the first thing I decided to do was to install Ubuntu completely this time, but here is where the problems started. I tried to boot from the CD again using my CD drive, but I kept receiving the message that there was no operating system in my computer, which is true but I had already changed the boot sequence in the BIOs to boot first from the optical drive, since I kept receiving the messages I decided to try in another drive since the system also has a DVD drive, this time it loaded and apparently everything was going fine again until I stumbled upon this message: 

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in-shell(ash)
Enter 'help' for a list of built-in commands.
/bin/sh:can't access tty: job control turned off 
initramfs)_

It's the first time I'm installing a Linux distro, and unfortunately I have no idea what to make out of this message. Does anyone know what could be causing the problem and how to solve it? thanks in advance

---

### Post by firsttimeubuntero on 2007-08-10
anyone plz?

---

### Post by Pumalite on 2007-08-10
That message can mean many things. Here is a thread for your information: [http://ubuntuforums.org/showthread.php?t=415009&page=1](http://ubuntuforums.org/showthread.php?t=415009&page=1)

---

### Post by firsttimeubuntero on 2007-08-10
This is strange I decided to try again in booting up from the live cd and this time I got this error message:

[numbershere]Buffer I/O error on device hdd, logical block 322711
SQUASH error: sb_bread failed reading block 
SQUASH error: Unable to read page, block 29041568
[1432.893622] request_module: runaway loop modprobe binfmt_0000

---

### Post by Pumalite on 2007-08-10
Post your specs. You might need the Alternate CD. Start from basics. Do md5sum on iso. Burn at 4x. Check CD for corruption before install.

---

### Post by firsttimeubuntero on 2007-08-10
> **Pumalite said:**
>  Burn at 4x. Check CD for corruption before install.

I actually did these 2 steps before I would try to boot from the live CD

---

### Post by Pumalite on 2007-08-10
What about the md5sum on the iso? Your specs please.

---

### Post by firsttimeubuntero on 2007-08-10
here's a more complete version of the error:

[1432.887601] SQUASHFS error: sb_bread failed reading block 0x8fde2
[1432.887660] SQUASHFS error: Unable to read fragment cache block [23f720bf]
[1432.887720] SQUASHFS error: Unable to read page , block 23f720bf , size 69a6

[1432.893055] request_module: runaway loop modprobe binfmt-0000
[1432.893128] request_module: runaway loop modprobe binfmt-0000
[1432.893331] request_module: runaway loop modprobe binfmt-0000
[1432.893393] request_module: runaway loop modprobe binfmt-0000
[1432.893622] request_module: runaway loop modprobe binfmt-0000

---

### Post by firsttimeubuntero on 2007-08-10
> **Pumalite said:**
> What about the md5sum on the iso? Your specs please.

sorry for the ignorance but what is the md5sum?

---

### Post by firsttimeubuntero on 2007-08-10
> **Pumalite said:**
>  Your specs please.

not quite a wizard to describe computer hardware but here goes:

45.0 GB hard drive  
CD-RW drive
DVD-ROM drive
850 MHz processor
511 MB RAM

---

### Post by merlinus on 2007-08-10
Seems like a bad download, burn, or cd drive.

Also, with 256MB RAM you are far better off using the text-based Alternate Install cd, as you will most likely not be able to install from the live cd.

-merlin

---

### Post by firsttimeubuntero on 2007-08-20
ok having a small update in this problem, it seems that there was only a card for 128 MB ram on the computer (my bad I didn't check) so I searched around to see if I had any spare ram for this system and luckily I found 2 cards of 256 MB ram each. Can I upgrade the ram inside this rig without an OS installed? I wonder if I can just open the case and switch the 128 MB ram card for two 256 MB ram cards, is it possible to do it and will ubuntu recognize them at the time of installing?

---

### Post by Pumalite on 2007-08-20
You can do it. Consult your manual to know which slots to use. Merlinuz advise still runs.

---

### Post by firsttimeubuntero on 2007-08-20
> **Pumalite said:**
> You can do it. Consult your manual to know which slots to use. Merlinuz advise still runs.

thanks for the advise, I think I'll do it that way it will be 512 MB of ram and hopefully the cards or the motherboard won't fry themselves, also do you think it will solve the problem with the slow installation from the live CD?

---

### Post by Pumalite on 2007-08-20
You could do it,but Alternate CD is better.

---

### Post by firsttimeubuntero on 2007-08-20
My system has 511 MB of RAM now and problem still persists, I'm downloading the alternate CD

---

### Post by firsttimeubuntero on 2007-08-20
I have one question, which one is more complete ubuntu 7.04 or ubuntu 6.06? which version is the most versatile and with most available software?

---

### Post by Pumalite on 2007-08-20
7.04 is latest stable. As such it has more programs and newer versions. I would go for 7.04. 6.06 OTOH has longer support.

---

### Post by firsttimeubuntero on 2007-08-20
> **Pumalite said:**
> 7.04 is latest stable. As such it has more programs and newer versions. I would go for 7.04. 6.6 OTOH has longer support.

thanks for the reply, since 7.04 has more software available I would go for that one

---

### Post by firsttimeubuntero on 2007-08-21
some help plz for some reason I can't burn the 696 MB alternate image into a CD, it stops at 19% and the message data error (cyclic redundancy check) pops out

---

### Post by firsttimeubuntero on 2007-08-21
ok assuming it was a bad download I have decided to download the alternate CD image again, while it's downloading I thought I try one more time, so I turned on the comp again with the live CD on it, this time it loaded normally and took me to the gnome interface and didn't get me any error. Since I was there I decided to install it in my system and get over this already, so I clicked the install icon, but to my surprise the system froze and none of the options on the desktop responded with the exception of movement on the mouse. I turned off the comp and turned back on and this time it showed me an error of this sort:

/usr/sbin/cupsd: error while loading shared libraries:


and another type of error which kept repeating itself


hdd error code: 0x70 sense key: 0x03 asc 0x11 ascq 0x00


just out of curiosity I decided to turn it off and back on once again, and this time I got the message:

"Operating system not found"

Does anyone know what happened here? why did the situation worsened up?

---

### Post by A$h X on 2007-08-21
Make sure that you d/l the iso from this site, and it's burned @ low speed (4x or less), use infrarecorder to make sure that it's burnt correctly. I've got a similar machine spec to you and the feisty fawn live CD worked fine for me.
Your particular problem though... maybe your HD is on the way out. I would use something like Gparted live CD to format the entire HD,  remove any partitions and then try the install from live CD again. Good luck.

---

### Post by firsttimeubuntero on 2007-08-21
> **A$h X said:**
> Make sure that you d/l the iso from this site, and it's burned @ low speed (4x or less), use infrarecorder to make sure that it's burnt correctly. I've got a similar machine spec to you and the feisty fawn live CD worked fine for me.
Your particular problem though... maybe your HD is on the way out. I would use something like Gparted live CD to format the entire HD,  remove any partitions and then try the install from live CD again. Good luck.

thanks for all the tips, I'll try them out

---

### Post by firsttimeubuntero on 2007-08-22
ok I managed to create the alternate CD image following the instructions from A$H X. However, the computer now doest not recognize anything, after starting and giving the specs of the system I keep receiving the message "Operating system not found" while it's true that I have no operating system in the computer, I thought having the CD inside the comp and changing the boot order in the bios would allow me to start with the installation, so why do I get this message? plz help

---

### Post by merlinus on 2007-08-22
If the cd has defects, the computer will not boot from it.

Check by trying it on another computer.

-merlin

---

### Post by A$h X on 2007-08-22
Don't give up, we'll sort it out. Firstly, in the BIOS is the CD/DVD drive set to primary boot device (in mine it goes boot from floppy first, then from CD, then from HD). If yours is set to boot from HD first, then the CD will never run so try that.
Secondly as merlinus said, if the CD is scratched then maybe it will not boot correctly. Try burning to another (preferably brand new or at least confirmed as working) CD-R or CD-RW and try to boot from that. Let us know how you get on.

---

### Post by firsttimeubuntero on 2007-08-22
> **merlinus said:**
> If the cd has defects, the computer will not boot from it.

Check by trying it on another computer.

-merlin

I have the same problem when trying to boot from the Ubuntu 7.04 Live CD as well, it just started doing this now and I checked the optical drives and they are both connected

---

### Post by Pumalite on 2007-08-22
If you are doing everything else well; it's time to start checking your hardware: memtest, replace burner, etc.

---

### Post by firsttimeubuntero on 2007-08-22
totally weird, this time the DVD drive actaully detected the Live CD I have checked the CD for errors using the option on the Ubuntu start up screen and it says it hasn't found any, booting from the CD as normal and entering the Gnome desktop now...

---

### Post by firsttimeubuntero on 2007-08-22
Gnome desktop loaded and I got a pop up message: 

The panel encountered a problem while loading 
"OAFIID:GNOME_NotificationAreaApplet".

Do you want to delete the applet from your configuration?



does this mean that is going to delete an applet on the gnome desktop?

---

### Post by firsttimeubuntero on 2007-08-22
I just closed the windows and didn't choose whether to delete the applet or not, I understand that you can try some options from the Live CD, so I tried the icon for mozilla firefox, and after clicking it the pointer turned into a circle which I presumed it indicates that it was loading but then it stopped and went back to normal and the browser was never launched, I also tried Applications > Accessories > Dictionary   option but it didn't load either. 
Does anyone know what's happening here?

---

### Post by firsttimeubuntero on 2007-08-22
does anyone know how can I do a memtest without an operating system installed?, Pumalite suggested one a couple of  posts ago.

---

### Post by Ubun00btu on 2007-08-23
Your BIOS can be set many times to do a self-test on the memory.  It's not exactly thorough, but it'll show a serious problem if there is one.  Otherwise you'll need to find or create a boot CD and a memory test program that will allow you to run it under DOS.  

I've had that "no operating system found" error before; unfortunately it was so long ago the details in my head are sketchy.  It was either a failure of the northbridge chip on the motherboard, or I had a bad HDD.  Possibly a bad format of the HDD.  If you have a spare HDD, you might try that; or, if you have another computer, try booting with the CD on that one and see if there is still an issue.  Don't worry, as long as you don't do an install or partition work it shouldn't mess with the other computer.

---

