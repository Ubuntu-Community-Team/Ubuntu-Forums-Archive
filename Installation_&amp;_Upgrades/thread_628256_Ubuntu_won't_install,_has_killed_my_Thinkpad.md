---
title: "Ubuntu won't install, has killed my Thinkpad"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by rodthefarmer on 2007-12-01
I am really frustrated with Linux.  I got a new hard drive for my Thinkpad, and decided now would be the time to install Linux.  Ubuntu 6.10 ALMOST installed, but would not recognise my Ethernet chipset.  I got some cryptic advice from some people, and things went from bad to worse.  Eventually 6.10 would not boot unless the CD was in the drive.  Files on a floppy drive cannot be read.  Then I was told to get the System Rescue CD.  That ruined the hard drive so that 6.10 will no longer install at all.  I got 7.xx, and that won't do anything.  It even refuses to recognise the CD Eject button.  I have to power it off to get the CD out.  I have written to several people on Linux fora trying to get help, and almost every single one does not even reply.  I tried switching to Mepis, as there seemd to be some of those users who were able to get the Thinkpad Ethernet working.  Nothing works now.  The Thinkpad is now useless.  Whatever Linux did to it, it will not even reload Windows.  I get a black screen and a blinking cursor now.  Some of the syntax suggested to me to "fix" my problems are so obscure that a Windows user like me  has no idea what they mean, where to input them, or what is supposed to happen.  Count me among those extremely disappointed and frustrated with my Linux experience.  I will recommend strongly that any Windows user NEVER consider changing to Linux.  Buy a PC with it pre-installed, maybe.

---

### Post by Pumalite on 2007-12-01
What do you want installed in this laptop?

---

### Post by rodthefarmer on 2007-12-01
I would like to try some version of Linux.  At least, one that will work, and connect to the Internet.

---

### Post by Craigus on 2007-12-01
Software cannot permanently damage your hard disk, although things can certainly get royally screwed up.

What I'd suggest you do is to download Ultimate Boot CD - it has HD manufacturer's utilities as well as many other useful things. Run the appropriate utility for your make of HD and do a "low level" format (assuming that there isn't mission critical data on the drive that you need to recover). This will write zero's to all of the user data sectors of the drive and return it to factory condition.

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

After that, you can reinstall windows or even have another shot with linux if you wish.

---

### Post by Pumalite on 2007-12-01
I can help you to install anything you want. First post your specs: processor, memory, graphics, etc

---

### Post by Craigus on 2007-12-01
> I would like to try some version of Linux. At least, one that will work, and connect to the Internet.

Have any of the livecd's that you have tried been able to do that ?

---

### Post by rodthefarmer on 2007-12-01
None of the CD's I have tried have worked.  The Ubuntu 6.10 was able to boot from the hard drive, initially, but did not recognise the Ethernet. The others were less functional than that, and 7.xx did not even seem to install.  Now here is an example of my frustration.  I just went to the Ultimate Boot web site.  I cannot find a "download here" button.  A long list of what I will GET, but no place to actually GET it.

My ThinkPad is an A20m, with a Celeron 500 MHz, 512 MB of RAM, ATI Rage Mobility M

---

### Post by Pumalite on 2007-12-01
DBan your drive:[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then get Gparted Live CD and format your drive ext3.

---

### Post by rodthefarmer on 2007-12-01
I am operating on a different PC than I was when I originally got the ISO files.  Now I have to try to find a tool that will create a CD from the ISO file, as I don't have that program on this machine.

---

### Post by rodthefarmer on 2007-12-01
OK, used a second machine with a rewritable drive, DBAN is now loading.  Running autonuke.

---

### Post by Pumalite on 2007-12-01
If you are in Windows; download and install ImgBurn:[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Go to Mode>ISO>Burn

---

### Post by rodthefarmer on 2007-12-01
OK, DBAN is completed, apparently successfully.  On reboot is says "OS not found".  Thanks for the help so far, now what do I do ?

---

### Post by Pumalite on 2007-12-01
Boot Gparted Live CD and make a large partition of your whole hard drive, formatted ext3.

---

### Post by rodthefarmer on 2007-12-01
OK, I got the Gparted CD, (btw the first web site I went to has lots of typos).  I ran it, and it found the disk 37 GB, but I don;t know what the "ext3" means.  I just ran the default first item on the menu.  The GUI panel says the drive is unallocated.

---

### Post by Pumalite on 2007-12-01
You have to click on the unallocated space, then go to Partitions>New and in the new menu you'll see ext2, ext3, etc. Make it ext3 and 'Apply'

---

### Post by rodthefarmer on 2007-12-01
OK, done, now what ?

---

### Post by Pumalite on 2007-12-01
You have a brand new hard drive, absolutely clean of all debris and you can install Ubuntu.

---

### Post by rodthefarmer on 2007-12-01
Thanks.  Downloading 7.10 as we speak.  I may post again here, to get directions on where to go for Ethernet support, if it does not work in the new version.

---

### Post by Pumalite on 2007-12-01
Good luck.

---

### Post by Whiffle on 2007-12-01
Might be useful:

[http://dag.wieers.com/howto/thinkpad/a20m/](http://dag.wieers.com/howto/thinkpad/a20m/)

[http://www.thinkwiki.org/wiki/Category:A20m](http://www.thinkwiki.org/wiki/Category:A20m)

Assuming you have the dreaded Intel/Pro100 network, you may have to do

```

rmmod eepro100
modprobe e100

```

to get the network working.  It seems to be sort of oddly supported ethernet card

---

### Post by rodthefarmer on 2007-12-01
I tried Dag Wieers - he does not respond to email.  Thanks for the other ideas. But remember I am a Windoze type.  All this syntax is cryptic and possibly meaningless to me.  Do I type this in a terminal session ?  What directory should I be in to do it ?  What do I do AFTER I type it ?  Reboot ?

---

### Post by Pumalite on 2007-12-01
You installed your system. I'd recommend starting a new thread. There is a Networking sub-forum. You might have better luck.

---

### Post by rodthefarmer on 2007-12-01
Well it looks like I am back to my old situation.  Ubuntu 7.10 STARTS the install, loads 100 % of the kernel, then the startup screen vanishes, and I am left with a blinking cursor.  All CD activity stops.  This is exactly what happened the last time.  I will now try using my old 6.10 CD, and see if the symptom is the same....boots only with the CD loaded.

---

### Post by Pumalite on 2007-12-01
Clean yur hard drive first with Gparted(erase prior installation reformatting), then try installing with the Alternate CD.

---

### Post by rodthefarmer on 2007-12-01
More error messages with 6.10, something about it being a Laptop.....

piix4_smbus (or something, it disappeared as I was typing)  this module may corrupt your serial eeprom.

light grey screen, startup music, another error message about GNOME Settings Daemon

It seems to have completed now.  CD Eject button is again not working until AFTER the shutdown has completed.  On restart, nothing happens unless the CD is loaded.  I get only a blinking cursor.  Then it goes through the same, long process of "installing" Ubuntu.  AT least the CD eject button works, and once I insert the disk, it is still stuck at "nothing".  I have to reboot to get Ubuntu to load/install again.

When I tell it to "boot from local disk", it does nothing.  It would appear that Ubuntu never actually INSTALLED on the hard disk, it just loaded from the CD.  It would be nice if there was a CHOICE, to just load, or do a full install.

---

### Post by Pumalite on 2007-12-01
Check your BIOS for settings. Then get inside your computer and check cables (change if necessary) and connections. Clean the lens of your burner. Check CD's in a different computer.

---

### Post by rodthefarmer on 2007-12-01
Sorry, I don't know what you mean by "check my BIOS".  How ?  Cables loose ? Suddenly a cable came loose in a notebook ?  I am going to have to buy a large pack of blank CD's to write all the different tools I am supposed to try.  I am starting to think maybe Ubuntu is not meant for ThinkPads.

---

### Post by Pumalite on 2007-12-01
Search this forum for your laptop and you'll find many successful installs.

---

### Post by xeth_delta on 2007-12-01
> **rodthefarmer said:**
> More error messages with 6.10, something about it being a Laptop.....

piix4_smbus (or something, it disappeared as I was typing)  this module may corrupt your serial eeprom.

light grey screen, startup music, another error message about GNOME Settings Daemon

It seems to have completed now.  CD Eject button is again not working until AFTER the shutdown has completed.  On restart, nothing happens unless the CD is loaded.  I get only a blinking cursor.  Then it goes through the same, long process of "installing" Ubuntu.  AT least the CD eject button works, and once I insert the disk, it is still stuck at "nothing".  I have to reboot to get Ubuntu to load/install again.

When I tell it to "boot from local disk", it does nothing.  It would appear that Ubuntu never actually INSTALLED on the hard disk, it just loaded from the CD.  It would be nice if there was a CHOICE, to just load, or do a full install.

Quick Question. I might have missed it in the previous posts, but after botting the live cd, did you click on install Ubuntu? There should be an icon on your desktop that allows you to install.

The fact that your operating system will load only with the cd in, would lead me to the assumption that Ubuntu was in fact not installed.

---

### Post by xeth_delta on 2007-12-01
You could also have a look at these Ubuntu pages:
An Ubuntu 6.10 installation Guide [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html")

More information for users new to Ubuntu (It is aboult Ubuntu 7.10, but the general idea should be conserved for previous versions, too) [https://help.ubuntu.com/7.10/newtoubuntu/C/index.html]("https://help.ubuntu.com/7.10/newtoubuntu/C/index.html")

---

### Post by rodthefarmer on 2007-12-04
Well, here is the latest tale of woe.  During the INSTALL of Ubuntu 6.10, a new problem appeared.  And by the way, should there not be a message saying to the new user that Ubuntu is only LOADED ?  To INSTALL, click on the INSTALL icon.  It was not intuitive to me that this meant "Install Ubuntu".  I thought it was to install other stuff.  Anyway, during the INSTALL, it stopped at 24 %, and just sat there.  I tried to LOAD it again, and it will not work at all.  I ran DBAN twice, and it still won't load Ubuntu from a CD.  I will now try the System Rescue CD, to see if THAT will do something to the disk so that Ubuntu will now at least LOAD once more, so I can retry the INSTALL function. Two steps forward, 4 steps back.

---

### Post by rodthefarmer on 2007-12-04
The latest news is that after multiple attempts to get Ubuntu 6.10 to load from CD, it finally made it.  Clicking on the INSTALL icon has caused it to reach all the way to Step 5 of 6, "Starting up the Partitioner".  That has now been running for 2 hours, and is stuck at 7%.  I will let it run for a day or two, to see if it improves.  The little clock thingy is still rotating, so it at least thinks it is doing something.

---

