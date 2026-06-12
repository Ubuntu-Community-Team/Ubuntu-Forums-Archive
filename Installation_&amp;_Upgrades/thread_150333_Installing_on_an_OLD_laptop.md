---
title: "Installing on an OLD laptop"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by jpfreely on 2006-03-25
Hi everyone

Ok, so I had nothing to do on a Saturday so I thought I'd try installing ubuntu (server) on a 10 year old laptop.

Am I crazy? ... Well, yes. :twisted: 

Anyway I faced a number of problems but have worked through most so far. It has Windows 95 on it already.
So first up, the floppy drive is completely stuffed - bye bye to that boot method.
Next, it doesn't have the ability to boot from a CD, ok fine.
And it can't do network boot, doesn't even have integrated networking.

So I installed grub4dos, copied the vmlinuz and initrd files to c: drive, configured the grub boot options and hey presto, install starts. Complains of low memory (only has 32MB). Can't find CD-ROM.

So I did the same thing except tried network install. Can't find PCMCIA network adapter.

Ok, so I repartitioned the hard drive so that along with the FAT for Windows, there's also a bit of swap space and a fat partition at the end of the drive. I copied the contents of the CD to the new FAT partition.

Next, I rebooted and when it complained it couldn't find the CD, I entered a console with Alt+F2, did a mkswap and swapon for my new swap partition, then did mount -t vfat /dev/hda5 /cdrom. I told the installer to go to the copy preseed stage and it worked! Took ages, but installed a whole lot of stuff.

It asked to reboot so I did. But now it's stuck on a screen which says 'Preparing for installation' at 0%. Left it for a long time but no activity whatsoever. If I enter a console I note that none of the installer logs under /var/log/installer have been modified since the time of stage 1.

On the matter of the network adapter and cd-drive (which would be highly useful as currently there's no way to get data to or from the system) they still don't work. I looked under /etc but there's no pcmcia directory which could have info about the net adapter. And under /dev there's nothing that looks like it could be a cd-drive. This computer has no usb ports btw.

Finally, here's some details about the computer:
Toshiba Satellite Pro 430CDT
32MB RAM
2 GB Hard drive
Network: Ositech PCMCIA jack of diamonds trumpcard
CD: Toshiba xm-1502b internal, removable

Feel free not to help if you think I'm a lost case. I just couldn't bear to have a device running win95 around, even if I hadn't used it for a few years!

---

### Post by mofojones on 2006-03-25
That's a really valiant effort, and I just want to say, "best of luck".

If this doesn't work out for you, you might consider zipslack.

---

### Post by Sef on 2006-03-27
> 32MB RAM
2 GB Hard drive
Network: Ositech PCMCIA jack of diamonds trumpcard
CD: Toshiba xm-1502b internal, removable

With your ram,  I would do a server install (type server at the prompt then hit enter.)

For a window manager, I would use Fluxbox, the lightest weight window manager.  Though you could try icewm, too.

[https://wiki.ubuntu.com/Installation/LowMemorySystems]("https://wiki.ubuntu.com/Installation/LowMemorySystems")

---

### Post by az on 2006-03-27
On a toshia 460 CDT, I added 64 megs of ram from ebay and it runs icewm happily....

Wireless works out-of-the-box with a 16-bit pcmcia card.

And mine can boot from the cdrom....

---

### Post by jpfreely on 2006-03-28
I did indeed do a server install actually sef, but thanks. I was planning to either leave it X-less or alternatively a low resource WM such as fluxbox.

So your 430cdt boots from CD azz?! Interesting, perhaps I need to check those bios options again. Upgrading the ram's definitely a possibility to make it a tad more useful.

At this stage I'm thinking of replacing the PCMCIA eth with something known to be compatible and perhaps manually istalling the packages it seems to stop at 0% attempting to install (I'm guessing this will work, only one way to find out).

Thanks everyone!

[edit] i need to learn to spell...

---

### Post by Paki on 2006-04-21
jpfreely,

I'm having a similar problem with installing to a laptop that can only boot from a USB CD-ROM (no internal CD-ROM drive) using a funky emulation; once the kernel is loaded and the install program is running, the system cannot find and mount the CD-ROM.

I'm trying to replicate things to the point that you got, but when I give the command "mount -t vfat /dev/hda4 /cdrom" it fails because "No such file or directory". Any ideas?

---

### Post by linuxa on 2006-04-21
[QUOTE=mofojones]That's a really valiant effort, and I just want to say, "best of luck".

If this doesn't work out for you, you might consider zipslack.[/QUOTE]

Or DamnSmallLinux

---

### Post by jpfreely on 2006-04-21
Paki,

Well a few things I can think of:
Have you got the partition right? Check "cat /proc/partitions" to see a list of them.
Is the partition a FAT formatted one? Use -t auto if you're not sure.
Have you copied everything from the CD to this partition (the top level)?

---

### Post by Paki on 2006-04-22
jpfreely,

Check on all counts. In fact, I can make a new folder and mount the partition to that and get access to the files. All I can't do is mount the partition to /cdrom .

---

### Post by jpfreely on 2006-04-22
Oh ok. In that case it's probably that the /cdrom directory doesn't exist. Make sure you create it first with "mkdir /cdrom".
If it already exists you could try getting rid of it then recreating it: ("rm -r /cdrom" will do the removing).

Edit:
Also check that there isn't something mounted there already. Type mount and look for something at /cdrom. You can unmount whatever's there with "umount /cdrom".

---

### Post by mattlscc on 2006-04-25
I'm new to linux and ubuntu... but I might be having a similar problem...  

I'm not sure what is going on, but I am trying to install on a desktop PC I got back in 1998 (compaq pesario).  It has 128MB RAM, a 15 GB harddrive, Pentium II, two USB drives, D-Link NIC, Dual video cards, and a dvd/rw drive, and I believe it used to have windows 95 on it.  Anyhow I formatted the harddrive because nothing was working.  I thought I'd try to install linux and ubuntu seemed like a fun choice.

I am doing a install from a boot CD... sometimes it installs everything correctly, sometimes it doesn't... (not sure why the install does different things sometimes??  my thoughts are maybe my CD drive is slowly starting to fail and doesn't read something off the install disk correctly??  or maybe there is a bad sector on the old harddrive that linux maybe tries to use??)  

Anyhow, my most common problem is I will get done with the CD part of the install... (just a regual hit enter install) and it will eject the CD and reboot.  Once it gets done loading the modules and figuring out the module dependencies... it will then go to a screen where it says "Preparing for installation..." and it stays at 0% forever.  I know it has frozen when the Caps Lock button on my keyboard no longer lights the green LED on my keyboard.     Anyhow, I'm wondering if maybe I missing something?  Or if anyone has an idea of what to try next?

Also, if I shut down after it freezes and restart... it ends up freezing at the part where it tries to calculate the module dependencies... and wont even make it to the preparing for installation screen.  

On a side note I did get it to successfully fully install one time... this was before I had a NIC that ubuntu recognized... since I'm new to linux and ubuntu I didn't know how to install the NIC without going through the whole ubuntu install again (which erases everything on the harddrive and starts fresh)... so now I'm stuck trying to get it to install correctly... any help would be greatly appreciated!!!  (also, i'm new to this forum.. if I should start a new thread instead of jumping in on this one, let me know and I will repost somewhere else.)

THANKS!

---

### Post by mattlscc on 2006-04-25
ok, I guess my first post made it... this post can be deleted... I can't seem to figure out how to delete it...but if you are an admin or something... delete this post.  Thanks. :)

---

### Post by Paki on 2006-04-29
jpfreely,

Thanks for all the help- nothing works, I'm afraid. The installer just tells me that no CD device is detected, even if I go into the shell and "ls /cdrom" gives me a listing of the files from the copied install CD. I've no idea what the problem is.

---

### Post by jpfreely on 2006-04-30
Matt,

Sounds a little like the problems I'm having. I've pretty much given up on ubuntu for that computer now - I'm thinking it's not quite the right distro for very old computers. :(

Paki,

Sorry I couldn't help you out there not sure what else to try really - just to let you know I was using Breezy not a Dapper beta/alpha - I'm not sure if anything has changed (or indeed if you were in fact using Breezy).

---

### Post by jpfreely on 2006-06-30
Hate to revive an old thread but I'll just close this by saying that I got this laptop going again by putting the hard drive into a new laptop (one which accesses the hard drive from the bottom because these old laptop hard drives are bigger and won't slot it on the side).

I then installed not Ubuntu, Kubuntu, Xubuntu or any other *buntu but Puppy Linux - it's designed for old computers and actually runs quite nicely, I prefer it to DSL as well. Disadvantage is it's not based on debian so my favourite tools (apt-get etc) don't work, I think it's actually custom built. Still it suits this computer well - I'd probably recommend it to anyone with an old computer.

---

