---
title: "Live-USB not working - Can I remove Windows Partition without it?"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by vidwarren on 2012-11-25
Hi, I've just installed Ubuntu 12.10 on a Sony Vaio Y-Series VPCYB36KG Netbook (Bought in Singapore).

I got a bit confused during the installation and I've accidentally partitioned the hard drive leaving only about 18GB for Ubuntu, with most of the remaining 400+GB left on the Windows 7 Partition.

I want to remove Windows entirely and have all of the hard drive available for Ubuntu. The problem I have is that I cannot boot Ubuntu from my 2GB USB Drive. I followed the instructions but it didn't work before I installed Ubuntu (when I was trying to test it out) and it doesn't work now that Ubuntu has been installed. There's just no option on boot-up, even when I hit F2 and go to the menu, it just doesn't know it's there.

Could the problem be that my USB, even when empty says that its capacity is 1.9GB? Does it need to be at least 2GB exactly? Will I have to buy a 4GB drive for the job? I'm happy to do this but would prefer if I could fix it sooner.

All of the tutorials I've found for removing Windows or resizing partitions, require Ubuntu to be booted from a Live-USB or CD/DVD (I have no CD/DVD drive). Is there a way of doing it without?

Thanks in advance,

Vid

---

### Post by Bucky Ball on 2012-11-25
It can be booted from a hard drive install. You need to open Gparted, the partition manager, right click and unmount the Win partition. You can then delete but this may have unpredictable results regarding booting Ubuntu depending on where grub is installed. 

Never resize the newer Win partitions with Ubuntu, always with Win software and always after 2 or 6 defrags. ;)

---

### Post by vidwarren on 2012-11-25
UPDATE:

With a little further exploration, I figured out that I hadn't previously gotten into the BIOS (I think that pressing F2 too late had got me to a different menu).

Getting to the BIOS, I was able to enable the system to boot from an external hard drive. I put in my 1.9GB Live-USB formatted with Ubuntu 12.10 but now I'm getting an error message:

> SYSLINUX 4.06 EDD 2012-10-23 Copyright (C) 1994-2012 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:

Does this just mean that it hasn't properly formatted on my 1.9GB USB drive?

Thanks,

Vid

---

### Post by vidwarren on 2012-11-25
Thanks Bucky Ball, I'll have a look into that tomorrow after some sleep.

I'm not entirely sure where Grub is installed but it's not showing up on boot; I'm still getting 'Windows Boot Manager' with Windows as the default option.

Grub is a folder in /boot. Is this where it's installed or is that just the part of it that's supposed to run on boot?

Thanks,

Vid

EDIT: Also, it's pretty much a new machine. Would it be easier to just back up my files and reinstall Ubuntu without the partition? Or do I need to undo the partitioning anyway?

---

### Post by Bucky Ball on 2012-11-25
Yes, that message seems to indicate your USB dongle is not set up correctly. Did you use Unetbootin to make it? 

And yes, you may need a 4Gb stick, but not sure your error message is related to that (unless there wasn't room to get the Ubuntu installer on there which is why you have no config. file found).

---

### Post by vidwarren on 2012-11-25
I first tried to make the USB drive in Ubuntu's 'Startup Disk Creator' on another machine. That nearly worked but it cut-out when it had 1 second remaining and threw up an error.

I then did it in Windows using Pen Drive Linux: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button) - That seemed to complete though it did display a couple of errors during the process.

Eventually, when I couldn't get it to boot, I just downloaded Ubuntu onto the netbook and installed it without using a USB.

---

### Post by Bucky Ball on 2012-11-25
So you mean you have a Wubi install??? You need to install Ubuntu from some media, CD, DVD, USB ...

---

### Post by vidwarren on 2012-11-25
That makes a lot more sense now!

That would be why 'Windows Boot Manager' is still loading up on startup.
EDIT: and that would be why it only allocated a default amount of 18GB  (and offered a maximum of 30GB) for Ubuntu. And that's why it didn't have the  'slider' to partition the hard drive that I was waiting to see from the  last time I did this two-years ago...or an option as to whether to install purely Ubuntu.

I thought that I could just download an installer from the site but I get it now - Another drive needs to 'be the hard drive' while the installation happens, right?

OK, so what's my best option to set Ubuntu as the only operating system? If I get a 4GB USB and boot from that, will it remove the Wubi for me? Will it even keep the few pieces of software I've installed - GIMP, Filezilla, etc?


EDIT: I've marked the thread as solved because, although I haven't yet reinstalled, I can see what the problem was now. Thanks a lot for the help :-)

---

### Post by Bucky Ball on 2012-11-25
You're better off doing a clean install if you want just Ubuntu. If you remove the Win partition then you remove the Wubi install also. No problem with apps you've installed, though. Both easily installable in the new Ubuntu install. 

Before doing any of this, back up all personal data files on the Win partition you don't want to lose. Of course. ;)

Note: If you are going to dual-boot (Win and Ubuntu on separate partitions) you would want to shrink that Win partition and a leave the rest free space. Then use 'Something Else' when installing Ubuntu and manually partition the free space, some like:

/ = where the OS lives, 20Gb plenty;
/home = where your personal data and setting live, large as you like;
/swap = same as pagefile, 2Gb plenty.

This is flexible, of course. For instance, instead of a separate /home you could leave it out and Ubuntu creates a /home folder inside /. This will have folders for personal stuff in it, Documents, Music, Video, etc. You can delete these and symlink existing folders from an existing data directory.

Also, you can have a spare 15Gb partition or two for testing out other releases and distros. They can use existing /home and /swap partitions (no need to double up). One LTS release, say, as the stable production boot, and some playthings. Some people like to do this in an existing install using virtual machines but I'm leaping ahead ...

---

### Post by vidwarren on 2012-11-28
Thanks a lot for your help, I have it up and running and have had no problems over the last couple of days.

I ended up buying an 8GB USB (as it was on offer). I tried again with Ubuntu's Startup Disk Creator and it failed in the same way even cutting out at the same percent of completion. My guess is that this was the main problem.

So, I used [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) in Windows to make the USB bootable. This worked fine.

Having made the changes to the BIOS,  and having a USB made with no errors, it all worked a charm.

Thanks again, all the best.

Vid

---

### Post by Bucky Ball on 2012-11-28
Good news. Enjoy! ;)

---

