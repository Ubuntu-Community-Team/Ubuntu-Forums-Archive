---
title: "Fresh Installation problems"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by fiorinija on 2008-02-11
So heres the problem.

In preparation of installing Ubuntu I ran partition magic on my second hard drive. I made 3 partitions, One ext3 10GB partition for "/"  one ext3 30GB for /home and a swap space of 2GB.Also on the same hard drive I have a NTFS partition with the remaining space of 258 GB. The linux partitions are on the drive BEFORE the NTFS partition.

I downloaded the alternate cd image for 7.10, checked the MD5 and it was good. Burned the image at 4x.
I inserted the cd into my dvd drive and rebooted the machine. It boots up just find into the installer, goes through the normal processes and I manually selected the partitions for it to use. Everything goes fine and dandy until I get to the part where it installs the base system. Now, every time it will fail when it gets to installing the kernel. But if I tell it to continue and I go and do it again and then it asks me to select a kernel to install and i choose the second option which is something like kernel-image-generic and that will install just fine.

Next part that gives me problems is "select and install software", again everything is fine up until it gets to  about 73% and then it fails again... it tells me to check terminal 4, so i hit ctrl+alt+F4 to see the error message and this is what I see:

E: Method cdrom has died unexpectedly
menu item pkgsel failed with error code 1

And I get this every time i've tried to install.. I've tried boot options acpi=off and  acpi_irq_balance but none of those seemed to do anything. I'm really stuck here and Id love to install this O/S. Please can someone help me out.

Thanks, 
Jesse

edit: Thought I might include my sytem specs.

P4 3GHZ, 1GB RAM, Geforce 6800, LG DVD Burner, Generic CD-Burner, IDE: 80GB HD<- Master, IDE: 300GB HD<- Slave

---

### Post by Zill on 2008-02-11
fiorinija:  AIUI, Partition Magic is a Windows program and may not be formatting the partitions correctly for Ubuntu.  Not sure if this is the problem but I would only use the Ubuntu installer to partition and format the disk.

---

### Post by fiorinija on 2008-02-11
Well, i also reformatted the partitions using the installer, so that couldn't be the problem

---

### Post by fiorinija on 2008-02-11
Someone help please :-( If anyone has any suggestions at all i could use em.

---

### Post by Zill on 2008-02-11
The alternate CD install is often used for low-spec PCs.  Your spec seems quite adequate for the normal GUI install.
I suggest you download the normal Live CD and see if Ubuntu loads and runs OK (from the CD).  If so then click on the desktop install icon and see how far you get with this install.

---

### Post by fiorinija on 2008-02-11
The problem I had with the Live CD was that after the screen where you see the bar going back and fourth loading the live cd, the screen goes all wacky and stuff and i cant do anything or even make out the screen.

---

### Post by Zill on 2008-02-11
The live CD problem seems to be related to the Nvidia graphics.  If your motherboard also has a built-in graphics chipset then I suggest you temporarily enable that in the BIOS.  The live CD should then run correctly and you *may* also be able to install Ubuntu.

If Ubuntu can be installed OK it should be possible to install the correct Nvidia drivers and re-enable the Nvidia card.

Caveat:  I have never used Nvidia cards so this may be total rubbish - but it should be worth trying :-)  Maybe a Nvidia expert can help on this.

---

### Post by fiorinija on 2008-02-11
Well at least one person is giving me ideas if anything, thanks Zill. But I think i need to focus on the original problem, the alternate CD shouldnt be giving me problems in the first place. there is no way the cd is corrupt everything checks out. I guess i'll just have to keep experimenting until i figure it out.

---

### Post by Zill on 2008-02-12
You are quite right in that the alternate CD should not be giving you problems.  However, I take the view that if the Live CD will run then you are halfway there as it **proves** the hardware can handle Ubuntu.

---

### Post by DavidTangye on 2008-02-12
Actually, it sounds to me that the CD IS corrupt. The symptoms are similar to what I have had in the past. Many CD burners are utter rubbish. I now have a machine set up to serve install images over the LAN, and netboot into them, to avoid the dramas with CDs. See [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet) for details, or use a different burner.

---

### Post by fiorinija on 2008-02-14
So i ditched the cd, now im trying to use unetbootin with ubuntu 7.10, and this is what happens. I posted picture links of my screen. The system is downloading software and installing, and the system froze up at this part, i was on tty4 to be sure to catch it.

maybe my machine is telling me i should never use linux... ever... but i want to..

[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1004.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1004.jpg)
[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1003.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1003.jpg)
[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1005.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1005.jpg)
[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1007.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1007.jpg)
[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1008.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1008.jpg)

someone... help please =(

---

### Post by DavidTangye on 2008-02-14
The ubuntu kernel does not seem to be handling your hardware. I think I would try PCLinuxOs, Puppy, Knoppix or the  SystemRescueCD distro. One of them is likely to install OK, and the lst 2 might give insight into what is going on.

---

### Post by Zill on 2008-02-14
fiorinija:  Your screen dumps appear to show that you are trying to install Hardy.  This is version 8.04, rather than 7.10, and is still beta software so is very likely to give problems.

I suggest you stick to version 7.10 (Gutsy) or even try 6.06 (Dapper) - the rock-solid long-term support version.

---

### Post by fiorinija on 2008-02-14
Yea, here's the dump from installing 7.10

[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1009.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1009.jpg)
[http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1010.jpg](http://s12.photobucket.com/albums/a238/jfiorini/linux%20install/?action=view&current=100_1010.jpg)

So whats wrong with 7.10? =(

Attached is my full system hardware report if anyone wants to look and let me know if anythings wrong with it.

---

### Post by Zill on 2008-02-14
Your system spec seems **far** better than I have on my PCs :-)

I hate to sound repetitive but I still think the best bet is to get a Live CD running **first**, either with Ubuntu or one of the distros DavidTangye suggested.

IMHO if a Live CD will not run then you are wasting your time trying to install the system.

---

### Post by Bucky Ball on 2008-02-14
"Partition Magic is a Windows program and may not be formatting the partitions correctly for Ubuntu. Not sure if this is the problem but I would only use the Ubuntu installer to partition and format the disk."

I am a bit of a newbie myself, but have wrestled with my laptop and desktop dual-boots for the last couple of months or so, and I would definitely agree with this. Go the partitioner in the install process and set them all up fresh (except your Windows partition and any others with data on!)

Because the CD checked out, doesn't mean it is still fine (that's computing!), so maybe run the CD check again and have a really good look at the disk under light. A tiny smudge or slight scratch (maybe from insertion into the CD tray) can really be enough. Got an old box you can plug up to your monitor and try install the CD on that - see if you get the same error to be sure (although long winded resolution).

Try burning again, or - and this is a little from left field - this is not a hardware problem? Guess if it's giving you the error at the same spot, same time, it wouldn't be and these things normally just die, but is your burner/player old or new?

:)

---

### Post by mlapaglia on 2008-02-14
yes, even if it checks out there can still be problems with the disc.

try using a different media. certain drives work best with certain media. weird i know, but i would recommend verbatim, it works best with most drives.

also, try burning it onto a dvd if you can also, that might help.

---

### Post by ububaba on 2008-02-14
I started intalling Ubuntu 7.10 on a newly[COLOR="DarkRed"] formated[/COLOR] disk but after chosing the Keyboard
 in the next frame it says I should set the size of root partition, swap size etc but the HDD
is [COLOR="DarkRed"]not reachable[/COLOR]. With the G-Parted it is a similar problem. No harddisk seen.

---

### Post by fiorinija on 2008-02-14
The only problem is, as i stated im using unetbootin to install 7.10 so its not a cd burning issue. I guess ubuntu just wont work with my system =(

---

### Post by Pumalite on 2008-02-14
Check the Ubuntu site for hardware compatibility.

---

