---
title: "Alternate Installation Methods? (No CD/No Netboot/No USB)"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by fizban9 on 2008-01-03
I'm trying to get Ubuntu (Xubuntu preferably but after weeks working on this issue I'll take ANY os) on my roommates laptop.  It's an old Latitude C300.  It refuses to boot to USB and we have no method of connecting a CD drive to it.  I have attempted to do a net install also  (see this post for the details of that failure: [http://ubuntuforums.org/showthread.php?t=641395](http://ubuntuforums.org/showthread.php?t=641395) )

Is there any other method for installation?  I can remove the hard drive and connect it to my computer (which, as of 1 week ago, is running Ubuntu 7.10) via USB so I have rudimentary access to the HDD.  I was hoping there would be a way to copy the install CD directly to the HDD and make it bootable.

Any ideas?

---

### Post by carrett on 2008-01-03
Here is a pretty comprehensive guide (AFAIK) on the various methods of installing Ubuntu: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

What is the machine running? If it is currently running with a boot manager that can run Linux, there are minimal kernel images you can download that will get a text-based installer going for you.

Otherwise there are things like [http://goodbye-microsoft.com](http://goodbye-microsoft.com) that make it too simple to install Debian from Windows (don't know if there's an Ubuntu equivalent out there yet...).

Anyway good luck.

---

### Post by fizban9 on 2008-01-03
I should have mentioned that.  It currently has no running OS on it.  Thanks for the link, I'll check it out.

---

### Post by carrett on 2008-01-03
That's going to be tough...I'd try the harddrive swap.

---

### Post by Niniel on 2008-01-03
Do you have a floppy drive?
Then you could get DOS or Windows 3... (you did say "any"... :) )

What I found puzzling is your comment about getting only "rudimentary" access to the hd when you plug it into another computer. Why is that? You should have complete access if you manage to hook it up. You should then be able to install directly only the hd. Of course, the hardware will be different in the original computer, but if you go for the most generic installation it might work.

---

### Post by fizban9 on 2008-01-03
> **Niniel said:**
> Do you have a floppy drive?
Then you could get DOS or Windows 3... (you did say "any"... :) )

What I found puzzling is your comment about getting only "rudimentary" access to the hd when you plug it into another computer. Why is that? You should have complete access if you manage to hook it up. You should then be able to install directly only the hd. Of course, the hardware will be different in the original computer, but if you go for the most generic installation it might work.

When I say connect, I mean via a IDE->USB converter.  By rudimentary I mean the computer sees it as a USB drive and wont allow me to do anything, such as change the file system or edit the partitions.  This was in XP though, I haven't connected it to my machine since I installed Ubuntu.

And no, there is no floppy drive.  I have a USB floppy I've tried connecting but the BIOS doesn't have an option to boot to USB.  The closest it has is "external floppy" which I tried and didn't work.

As for the idea of a hard drive swap.  I've tried it with XP a couple different ways and it's failed every time.  Should I try it with Ubuntu, is it more forgiving of massive hardware changes?  If so, at what point would I want to swap the hard drive back?

---

### Post by Niniel on 2008-01-03
Hm, this is very weird.
You mean to say that in XP, with an admin account, you can't partition the external hd? Or format it? 
USB devices can be treated as hds and as removable media, akin to CDs, I suspect XP looks at your drive as the latter, which is why it's refusing to do your bidding. 
But with Ubuntu, I wouldn't think this will be a problem, but then again, you never know... I have seen posts by people who had problems with their external usb hd under Ubuntu. 

As to how forgiving Ubuntu is when you swap computers I don't know. Never tried it. But it seems like you are pretty much out of alternatives, so I'd say it's worth a try.
I would swap right after the installation completes. Might be best to just put a command line system on the hd and then download the GUI from the C300. 

Good luck, and do post how it goes please.

---

### Post by fizban9 on 2008-01-07
Fail on all accounts.  I tried the install on another machine than swapped the drive back into to old laptop.  Got a nasty screen a little after boot that looked like ascii vomit, multicolored an unintelligible.  I was able to get to the shell but I just don't know enough linux to set the think up from the command like.  It was plugged into the network but it couldn't see it, probably because it didn't have the right drivers for the onboard nic.  

At this point, unless someone (other than myself, because I'm tapped) comes up with an amazing idea, I think it's done.

I still can't believe there isn't a way to copy a cd directly to a hard drive and install that way.  Seems like it wouldn't be that hard to do, but then what do I know?

---

### Post by carrett on 2008-01-07
Well, if you can get grub installed onto it (somehow) you can boot the debian installer, but I don't know if there are similar images for Ubuntu. I don't see anything but ISOs on the mirrors :(

---

### Post by Craigus on 2008-01-07
Did you see this:

> Did all that and install progressed well for about ten seconds until I got a "kernel panic" and abort. Looking at the TFTP32 syslog I found that the install was not finding the files in the pxelinux.cfg and the pxelinux.cfg.serial-9600 directory (possibly only the first was important, but I did the fix below on both folders just in case, following your redundancy/lazyness approach)

First, I had to put the pxelinux.cfg and the pxelinux.cfg.serial-9600 directory in the root level of the tftp directory. Then, I had to manually edit the names of the "default" files within each of these folders to match the MAC ID of the client machine. Apparently you can also use the IP address or the hex MAC ID. The TFTP syslog assists here as it tells you exactly the names of the files the client is looking for and not finding so you can just copy them and manually rename the "default" file.

After this it worked like a charm - this was at around 1am so I went to bed and most of the installation was complete by the time I woke up. It also had the bonus of allowing me to choose Xubuntu as my default desktop which was what I was hoping to get anyway.



in this thread:

[http://ubuntuforums.org/showthread.php?t=327597&highlight=ubuntu+netboot+pxe]("http://ubuntuforums.org/showthread.php?t=327597&highlight=ubuntu+netboot+pxe")

---

### Post by logos34 on 2008-01-07
> **fizban9 said:**
> Fail on all accounts.  I tried the install on another machine than swapped the drive back into to old laptop.  Got a nasty screen a little after boot that looked like ascii vomit, multicolored an unintelligible.  I was able to get to the shell but I just don't know enough linux to set the think up from the command like.  It was plugged into the network but it couldn't see it, probably because it didn't have the right drivers for the onboard nic.  

At this point, unless someone (other than myself, because I'm tapped) comes up with an amazing idea, I think it's done.

I still can't believe there isn't a way to copy a cd directly to a hard drive and install that way.  Seems like it wouldn't be that hard to do, but then what do I know?

Here's my best shot at a solution.

At the command line prompt run

sudo dpkg-reconfigure xserver-xorg

choose 'vesa' video driver,  You can accept the defaults for much of the rest.

If that doesn't get you to the desktop gui, then try adapting one of these guides (substitute gutsy) for a hard disk install:

[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

On one you need the alternate .iso, on the other you can (I think) use the desktop .iso

Connect the drive back to the computer you originally did the install on.  Wipe it and reinstall, but create a separate /boot (~50 MB) and 'holding partition' for the iso (~750 MB) in addition to / and ~256 MB /swap (in the following order on the hard disk):

|---------------- / (sda1) --------------------------|-- /boot (sda2) --|-- 750MB (sda3) --|-- /swap (sda4) --|

Install xubuntu, specifying above mount points. Write grub to the mbr.

Copy the xubuntu .iso to the holding partition.  Add appropriate iso boot entry to menu.lst. 

Stick it back into the laptop and reboot.  Select the .iso and start up the installation process again.  Install over sda1 but this time WITHOUT specifying separate /boot.  When complete, reboot into new installation and delete /boot (sda2) and the holding partition.  Unmount /swap (swapoff) and use gparted to create a new swap incorporating all the free space at the end of the disk (~1056 MB).  

(the reason for the separate /boot is that root cannot be mounted when you reinstall over it/format it--it will mount on boot I think even if it's just to call up menu.lst)

As you follow those guides make sure to get the paths correct.

Good luck.

---

### Post by fizban9 on 2008-01-08
In case anyone wants an update on this, I still haven't gotten an OS on the laptop but I'm really close.  I took the hard drive out and put it in another working laptop and installed ubuntu.  This doesnt work, not exactly, but it paritions the drive and sets up GRUB.

From there I've been following the instructions here: [http://www.debian.com/releases/stable/i386/ch05s01.html.en#boot-initrd]("http://www.debian.com/releases/stable/i386/ch05s01.html.en#boot-initrd") to do the netboot install of Debian.  

Still running into problems, but they're problems during the install, not before it.  Wish me luck!  If this works I may try and write up my experience as a how-to doc.  It would have better grammar, spelling and punctuation than this post.

---

### Post by Partyboi2 on 2008-01-08
I might be a little late for my input but if you have grub installed you could try
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

### Post by fizban9 on 2008-01-10
Well, it's finally done.  The broken old laptop has an OS on it, not Ubuntu though.  I did use Ubuntu to help me fix the problem but in the end it was Debian that got installed.

Basically what i did was take the hard drive out of the laptop and put it in another laptop.  This is where I installed Ubuntu.  Then I followed the amazingly confusing directions over at the Debian website for booting to a Debian install on the hard drive.

It required some weird partitioning, hard to find files and passing a parameter to the kernel during boot, but it worked.  I'm going to try and write up the whole thing in a How-To guide so other people can avoid the month long drama it took me.

Thanks for everyones help!  It was invaluable.

---

### Post by Gina on 2008-01-10
I would be very interested to see your How-To when you've written it :)  I love playing around with old hardware - trying to get something working on it (and I don't mean Win95!!).  I too have tried installing Ubuntu on a hard drive and moving it to another laptop (older) - that didn't work either.  I did a fresh install with Dapper Alternate CD but the system keeps crashing.

Thanks for your thread and work on this - great stuff :):)

---

### Post by rodica.balasa on 2008-01-18
here is how i installed on an old computer, using a floppy and netboot:
[URL="http://www.len.ro/work/tools/life-to...d-i8000-1/view"]
http://www.len.ro/work/tools/life-to...d-i8000-1/view[/URL]

---

